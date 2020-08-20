---
description: >-
  Rerun the test suite’s flow for a number of iterations while using each of the
  CSV rows as parameter values.
---

# API Tests - Data from CSV files

When you wish to run a flow several times using different parameters values for each run - just use a CSV file to list the parameters values and on run time the flow will run as the number of rows in the CSV, each run will get it’s own row values from the CSV file.

Find the "Import CSV" in the flow upper toolbar:

![Loadmill API tests - load CSV file](../../.gitbook/assets/csv.gif)

Once the CSV file has been uploaded, you will be able to go over the different parameters and their values in a preview window, when you're done, just click "Upload". \(Attention: in cases where the CSV file contains empty cells, Loadmill will not prevent its uploading\).

When a flow is using a CSV file, there will be an indication "Using CSV".

![Import CSV button](https://lh4.googleusercontent.com/ifbiZuH0JsNIb5aN6HRoBD1jY5IcyLAMc1Ji5vAK86hVCmkwnHnx-iHWd3vCX-kP2ZJOgxBAtTK94zZKjRz6YPCQ6o3jtDbsAO0YwldrnSpuxcJ03kKrDdfvxZpKyDEMC-jNlgeJ)

In order to remove a CSV file from the test, simply click on the "Using CSV" button, and click on the "Delete" button, located on the right button of the CSV window.

![](https://lh6.googleusercontent.com/r6nNQ0ReXJEtZ6M7yzVm1p0wCOXflhs68gni7r0phAfLe7KpXEQKJ8QMgzmbBSAxcUM4inb5LrnwCZa6FR4jxhf2vErU_suQt3i39HdRSn_RJ0M24QnWV3XMpuTJuA6oVPc-w4DH)

**Iteration for each CSV value**

When running a test suite using a CSV file, the flow using the CSV will run for a number of iterations as the number of values in the CSV, each iteration with the next values defined in the CSV file.

![](https://lh4.googleusercontent.com/8SJI1rHES86UJzwsJ9m3l2ck71TPi-HaxFCEQ4n5ohOCndnxdm8YHmvHa5tFHxyBtkttCguAV0mAdr9rDGwOxCrsuCpJ8LsVYuezE46YfhIqsLG4o0FzS9dOr2sftDS7AqaixDzu)

### Execution Order

When using a parameter defined in a CSV file, any parameter defined in the "Test Suite Parameters" section will be overridden by the value given from the CSV file.

The order of parameter value assignment is:

1. Value as in **Test Suite Parameters tab**. For example:  


   ![](https://lh6.googleusercontent.com/ELJn3Fp20I7qhVnAdI9AJmbUfbNyH3_Lqv8-6ecpi3-_ewPLwQ3mAGhgcjqjfAVOAwnjiMOrYewWgkD8iul7khd_Gvp0vsbFY1NqRbacMF0ldhpQu_SuggkOUNh0bDfZRqPozxvv)

2. Value as they appear in the **CSV** file. For example:  


   ![](https://lh4.googleusercontent.com/WpgRhs4TzSe3Tf0LQrm8YC4x6QlfjZwPHp891iW__ASk8EEy0lVZ7u9wW_RiK6eMd0oP4Aqy0olsd4PR_orzmnSMPTmhcBBjrvBt66dfRCgqi20ryZ-sy7znCjDj3U6CrqHnB3CH)

3. Value as defined in the **Extractions - Set Parameters** section of specific request \(These will override all of the above\). For example:  


   ![](https://lh6.googleusercontent.com/clyvxvJHm15KuFYx2BXDHXfiKEtdzAswSofZa24xTreUsLAp6mURs4tUoD4Li2nBBpHGZHk8mMCDL6byMIgOFPxPoJdFZiaUS90AcfghQM4uLsci4-OgTSY4feVte-UF2ob9aEUf)

