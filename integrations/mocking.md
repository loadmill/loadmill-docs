# Mocking

## Mocking services from API specs

Easily turn your API specs and Loadmill tests into a fully working mock server based on [Mountebank](https://www.mbtest.org/).\
You can generate mocks from Swagger or OpenAPI files, run them locally, and connect your Loadmill flows to them.

***

### What you can do

With this feature you can:

* Generate a Mountebank **imposter JSON** from:
  * A Swagger / OpenAPI file imported into Loadmill as a suite
  * Any Loadmill **test suite** (YAML)
  * Any single **flow** (YAML)
* Run the mock server locally on **port 9090** by default.
* Point Loadmill tests, Postman, or any HTTP client at the mock instead of the real service.
* Catch issues in your specs early (for example, mismatched field names) using Loadmill assertions against the mock.

***

### Prerequisites

Before you start, you need:

* A Swagger / OpenAPI file or existing Loadmill tests.
* A Loadmill account with permission to:
  * Import a Swagger file as a suite.
  * Export suites as YAML.
* Node.js installed on your machine.
* [Mountebank](https://www.mbtest.org/) (installed through `npm` or `npx`).
* Optional: Loadmill private agent or Desktop App if you want to run flows against `localhost`.

***

### Generate a mock from a Swagger / OpenAPI file

This is the most common workflow.

#### 1. Import the spec as a Loadmill suite

1. Open Loadmill.
2. Import your Swagger / OpenAPI file as a **test suite**.
3. Loadmill creates:
   * A flow for each endpoint.
   * JSON schema assertions based on the spec.
4. Open the suite and review:
   * The flows that were created.
   * The **Parameters** tab where the default origin URL is defined.

#### 2. Export the suite as YAML

1. In the **Test Suites** list, find the suite generated from your spec.
2. Open the suite menu (three dots).
3. Click **Export suite**.
4. Save the exported YAML file (this will be your input to the mock generator).

#### 3. Generate a Mountebank imposter

1. Open `https://mock.loadmill.com/` in your browser.
2. Upload the exported suite YAML.
3. Click **Generate imposter**.
4. Wait for the job to complete.
5. Click **Download imposter JSON** and save the file as something like `imposter.json`.

The downloaded file is a complete Mountebank configuration that you can run as a mock server.

***

### Run the mock locally with Mountebank

By default, the generated imposter config uses **port 9090** for the mock service.

#### 1. Install Mountebank

You can install Mountebank globally:

```bash
npm install -g mountebank
```

Or run it with `npx`:

```bash
npx mountebank --version
```

(This also checks that it is available.)

#### 2. Start Mountebank with the generated imposter

From the folder where `imposter.json` is saved:

```bash
mb start --configfile imposter.json
```

Mountebank will:

* Start its admin API (usually on port 2525).
* Start your mock service on **port 9090**, as defined in the imposter file.

You can verify that the mock is up by calling it directly:

```bash
curl -k https://localhost:9090/health
```

_(Replace `/health` with any endpoint you have.)_

***

### Use the mock in Loadmill

Once the mock is running, you can run your Loadmill tests against it.

#### 1. Point the suite to the mock server

1. Open the suite you created from your Swagger file.
2. Go to the **Parameters** tab.
3. Find the origin / base URL parameter.
4.  Replace the original host with:

    ```
    https://localhost:9090
    ```
5. Wait for the cloud icon to show that the suite has been saved.

All flows in the suite that use this origin now target your local mock server.

#### 2. Run flows using a local agent (for localhost)

If your mock is running on your machine (localhost):

1. Start the **Loadmill Desktop App** or a **private agent** on your machine.
2. Confirm in Loadmill that your agent is connected.
3. In the suite, pick your private agent in the **Run settings** (if needed).
4. Run a flow or the entire suite.

Loadmill will:

* Send requests to `https://localhost:9090`.
* Get responses from the Mountebank mock.
* Validate responses using the assertions created from your spec.

If there is a mismatch between the spec and the responses (or between the spec and the example schema), you will see assertion failures that point to the problem.

***

### Use the mock from other tools

You can also use the generated mock outside Loadmill:

* Postman collections
* Custom test frameworks
* Frontend or backend services running locally

Just set the base URL to:

```
https://localhost:9090
```

and call the same paths that your real service exposes.
