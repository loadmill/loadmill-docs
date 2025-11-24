# Quick Start Guide

## Quick Start — Demo AUT (Record & Run Your First Test)

This guide will help you record and run your **first end-to-end test in Loadmill** using the Maker–Checker demo app.\
Time needed: **10–15 minutes**

***

### What You’ll Need

* A Loadmill trial account (logged in)
* Google Chrome (latest version)
* [Loadmill Test Composer Chrome Extension](https://chromewebstore.google.com/detail/gdkmnfehipofdefhpegbgkkocinlaofd) installed and visible in DevTools
* 10–15 minutes of focus

***

### Step 1 — Install the Composer

1. Install the **Loadmill Test Composer** from the Chrome Web Store.
2. If your Chrome is managed, ask IT to approve the extension.

<figure><img src="../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>



***

### Step 2 — Verify the Recorder

1. Start by navigating to [https://bank-demo.loadmill.com/](https://bank-demo.loadmill.com/)
2. Open Chrome DevTools (**⌘⌥J** on macOS / **Ctrl+Shift+J** on Windows/Linux).
3. Select the **Loadmill Composer** tab.
4. Make sure the **Record** button is available.
5. Set **Filter Settings** to the demo AUT domain.

👉 Only after this step should you continue to the demo AUT.

<figure><img src="../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>

***

### About the Demo AUT — Maker–Checker Bank

The demo application is a simple **bank transfer system** showing the classic _Maker–Checker approval workflow_ (the “four-eyes principle”). It gives you a realistic but lightweight environment to test Loadmill.

* **Maker** logs in, creates a new funds transfer (amount, recipient, description). The transfer is saved with status _Pending_.
* **Checker** logs in separately, reviews pending transfers, and either approves or rejects them.
* **Maker** can then log back in to see the updated status.

**Demo URL & Credentials**

* URL: [https://bank-demo.loadmill.com/](https://bank-demo.loadmill.com/)
* Maker: `maker / maker1234!`
* Checker: `checker / checker1234!`

***

### Step 3 — Record the Maker & Checker Flow Together

1. In the Composer, **create a new Test Suite** by typing the name (e.g., _Maker–Checker Demo Flow_) into the suite selector and pressing **Enter**.
2. Click **Record**.
3. Log in as **Maker** and create a new transfer.
4. Confirm the transfer shows _Pending_.
5. **Click Pause** on the recorder (this ensures both roles are captured cleanly).
6. Log out (or open a private window).
7. Log in as **Checker**.
8. Approve the transfer created earlier.
9. Confirm the status updates to _Approved_ (or _Rejected_).
10. Stop the recording only after both Maker and Checker steps are complete.

👉 This demonstrates a **real end-to-end business process** across two roles.

<figure><img src="../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>

***

### Step 4 — Analyze Requests

1. Click **Analyze Requests** in the Composer.
2. (Optional) Check the **“Show filtered steps”** box to see which calls were removed. You can override AI filtering decisions here.

👉 This produces a **leaner, faster, and more stable test**.

<figure><img src="../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>

***

### Step 5 — Create the Test

1. Once analysis is complete, click **Create Test**.
2. You’ll be redirected to the Loadmill platform.
3. Review the test steps generated from your recording.

<figure><img src="../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>

***

### Step 6 — Finalize and Enhance

1. **Review & Rename** your test for clarity.
2. **Check Parameters & Correlations:** Notice how inputs like _amount_ and _recipient_ were auto-parameterized, and dynamic values like _transaction ID_ are automatically reused in later steps.
   * Rename parameters to readable keys if needed.
   * 👉 This reduces maintenance and makes tests reusable.
3.  **Try an AI Refactor:** Click the **AI Refactor** button and type:

    ```
    change recipient name to test-name
    ```

    * 👉 This shows how Loadmill AI can refactor many steps at once, cutting down manual edits.

***

### Step 7 — Debug and Run the Test

1. Toggle **Debug Mode** (gear icon).
2. Add a **breakpoint** on one of the steps.
3. Run the test and watch it stop at the breakpoint.

👉 Debugging lets you inspect intermediate results and quickly validate logic.



***

### Step 8 — Run the Suite

1. Click **Run Suite** to execute the full flow.
2. Verify that the Maker–Checker flow passes end-to-end.

<figure><img src="../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>

***

### Step 9 — Run as Load Test

1. Click the **small arrow** next to **Run Suite** and select **Run as Load Test**.
2. Set the test duration to **2 minutes**.
3. Run with **5 users** (trial accounts are limited to small load tests).

👉 This shows how the **same flow** doubles as both a functional and performance test.

<figure><img src="../.gitbook/assets/image (200).png" alt="" width="263"><figcaption></figcaption></figure>

***

### Step 10 — (Optional) Explore AI Configuration

Want to make Loadmill’s AI match your team’s language?

1. Go to **Settings → Algorithm → AI Prompts**.
2. Customize how Loadmill:
   * Describes steps (tone, style, emojis, business terms)
   * Explains failures (e.g., known API errors)
   * Suggests next steps in a flow

👉 Tailoring AI output makes results clearer, saves triage time, and fits better into your workflow.

**Explore here:** [AI Prompts Settings](https://app.loadmill.com/app/user/settings/algorithm?tab=ai-prompts)

***

### Troubleshooting

* **Can’t find the recorder?** It may be hidden in Chrome’s toolbar. Pin it.
* **No requests?** Check that recording is on and filters are correct.
* **Managed Chrome?** Ask IT to install the extension.
* **Security warning on AUT?** Expected, safe to proceed (browser flags it as a banking app).
