---
description: >-
  Diversify your test parameter values by using a CSV file to populate their
  values.
---

# Data from CSV files

Upload large datasets as CSV files and use them as parameters for you tests. Super fast. Super simple. Find the "Import CSV" in the test  "Advanced Settings" card.

![](../../.gitbook/assets/mar-04-2018-12-18-15-1.gif)

Once the CSV file has been uploaded, you will be able to go over the different parameters and their values in a preview modal, when you're done, just click "Upload". \(Attention: in cases where the CSV file contains empty cells, Loadmill will not prevent its uploading\).

When a test is using a CSV file, there will be an indication in the UI - "Using CSV".

![](../../.gitbook/assets/screen-shot-2019-02-10-at-3.17.48-pm.png)

 In order to remove a CSV file from the test, simply click on the "Using CSV" button, and click on the red **DELETE** button.

![](../../.gitbook/assets/screen-shot-2020-12-01-at-14.45.07.png)

### Execution Order

When running a test using a CSV file, **a random set of values** will be picked each iteration from one of the CSV lines. When using a parameter defined in CSV file, any giving parameter defined  in the "Default Parameters" section will be overridden by the value given from the CSV file. 

The order of parameter value assignment is: 

1. Value as in the "Parameter Defaults" section
2. Value as they appear in the CSV file
3. Value as defined in the "Extractions - Set Parameters" section of specific request \(This will override all of the above\)



