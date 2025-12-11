# **Suite Execution Mode**

Loadmill lets you control how flows inside a test suite interact with each other and how failures are handled.

The *Execution Mode* determines whether flows share state, how retries behave, and whether the suite stops on the first failed flow.

---

## **Where to configure Execution Mode**

You can configure Execution Mode from the suite’s **Run Settings**:

1. Open your test suite.
2. Navigate to **Run Settings** in the top navigation bar.
3. Scroll to the **Execution Mode** section.
4. Select either **Dependent** or **Independent**.

![](<../assets/suite-run-settings.png>)
---

## **Modes**

### **Dependent Mode**

Flows run sequentially and share execution state.

**Characteristics:**

* **Shared cookies & parameters** — any extracted values from one flow are available in the next.
* **Stops on first failure** — if one flow fails, the entire suite ends immediately.
* **Retry reruns the entire suite** — to rebuild all shared context correctly.

**Best for:**
 
* Multi-step flows where later tests rely on earlier outputs.
* Ensuring consistent global state.

---

### **Independent Mode**

Each flow runs in complete isolation (except `Before All`).

**Characteristics:**

* **No shared state** — every flow receives a clean environment.
* **Suite continues even if a flow fails** — all flows execute regardless of failures.
* **Retry reruns only failed flows** — much faster iteration when debugging.

**Best for:**

* Collections of unrelated flows.
* Wide coverage testing where independence improves stability.
* Re-tring specific failures without rerunning everything.

---

## **How Execution Mode Works**

* **Before All** always runs before the suite starts.
* In **Dependent mode**, all flows share one continuous execution context (cookies and parameters).
* In **Independent mode**, each flow gets its own isolated environment (cookies, parameters, and context are not reused).
* Retries follow the selected mode to ensure deterministic behavior.

---