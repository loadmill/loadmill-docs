# Data-Driven Tests and Scenarios

A Scenario Run lets you run the same saved test with different data, or choose a set of tests using a request in plain language. You describe the variations, review the planned cases, and run them. The original `.dcua` tests stay unchanged.

Use `test-data.md` for reusable products, accounts, regions, and other non-secret inputs. Use [project context](project-context.md) for shared product knowledge and [`.secrets`](using-secrets.md) for credentials.

## Add test data to your project

Open the project's menu in the sidebar and select **Open test data**. Droid opens `test-data.md`, creating a starter file if needed.

Write named entries with enough detail to identify each item in the app. For example:

```md
# Test Data

## Products

### Oat milk
Name: Oat Milk 1L
Availability: In stock

### Bread
Name: Wholegrain Bread 500g
Availability: In stock

## Delivery areas
- Central
- North
```

Replace these examples with products and areas available in your test environment. There is no required schema: headings, lists, and tables are all useful when their meaning is clear.

The editor saves changes automatically to `test-data.md` in the project's root folder. It is a regular file on disk, shared by the project's tests, including those in nested folders. You can edit it outside Droid and keep non-secret test fixtures in version control.

## Import an existing file

While editing test data, select **Import test data**, choose a CSV, TXT, JSON, XML, or Markdown file, and select **Import**. For a spreadsheet, export the relevant sheet as CSV first.

Droid uses AI to turn the source into readable Markdown and merge it with the current content. You can give instructions about how to organize it:

> Group products by name and put delivery areas in a separate section. Keep each product only once and preserve its availability.

If each row already represents a complete case, preserve that relationship instead:

> Treat each row as one case. Keep its product and delivery area together. Do not create additional combinations.

The result appears in the editor and is saved to `test-data.md`. Review names, values, and relationships after importing. The source file is not changed, and later edits to it are not automatically synchronized. Import it again when you want to update the project data. Import only non-secret data; this content is supplied to the AI model.

## Write one reusable journey

Keep the test readable and refer to the data by its purpose. A `catalog.dcua` test for the example above could say:

```text
Open the home screen.
Open delivery settings and select the delivery area provided for this run.
Search for the product provided for this run.
Open its details and verify the full product name matches the selected product.
Verify that the availability label is "In stock".
```

Each scenario case supplies a product and delivery area for these instructions. You do not need `{product}` or `{{area}}` placeholders.

A normal **Run** executes the test as written and does not automatically load `test-data.md`. Use **Run Scenario** when the test needs data supplied for each variation.

## Preview and run a scenario

Connect your target, then open the saved test's context menu and select **Run Scenario**. You can also open the project menu and select **Run Scenario** to let Droid choose from the project's tests.

Enter a request such as:

> Run catalog.dcua for each product in test-data.md, using Central as the delivery area.

Select **Preview Cases**. With the sample data, you should see two cases: Oat milk in Central and Bread in Central. Check that the preview includes the cases you intended. Use **Back** to adjust the request, then select **Run 2 Cases** to execute them.

## Try every combination

To combine two sets of data, say so directly:

> Run catalog.dcua for every combination of product and delivery area in test-data.md. Use both products in both areas.

Two products and two areas give four cases:

| Product | Delivery area |
| --- | --- |
| Oat milk | Central |
| Oat milk | North |
| Bread | Central |
| Bread | North |

This is sometimes called a Cartesian product, but the prompt can simply say "every combination." More dimensions increase the number of cases quickly, so check the preview before running.

You can also ask for a smaller selection:

> Run catalog.dcua only for Oat milk in Central and Bread in North. Keep those pairs together; do not mix them.

For a one-off check, paste non-secret data directly into the scenario request instead of saving it in the file:

> Run catalog.dcua once with product "Oat Milk 1L" and delivery area "Central".

Scenarios do not require a data file. If existing tests already contain everything they need, a request such as _run profile.dcua and settings.dcua once each_ can select those tests from a project.

## Review the results

Droid runs the planned cases one after another. Each case has a name and result in the scenario report, so you can find which variation failed. These cases are runs of existing tests, not new `.dcua` files. Start each journey from a known state; a Scenario Run does not automatically reset the application or recreate backend data between cases.

Use Droid for variations that prove something about the visible user experience. When the goal is to check hundreds of backend input combinations, [Loadmill API testing](../api-testing/overview.md) is usually a more efficient fit.

## Run scenarios from the CLI

Supply both the request and the test-data path:

```sh
droid-cua run tests/droid/catalog.dcua \
  --avd adb:emulator-5554 \
  --context tests/droid/context.md \
  --test-data tests/droid/test-data.md \
  --scenario "Run this test for every combination of product and delivery area."
```

The CLI prints the planned cases and starts execution without the desktop confirmation step. `--test-data` is optional when all the needed data is in the scenario request, but it can only be used with `--scenario`. The CLI does not automatically discover the project's `test-data.md`.
