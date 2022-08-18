# Labels

Labels is a great feature that allows to easily organize tests and then include them in your CI/CD process.

You can add multiple labels to each test flow by clicking on **Labels** or select a few test flows and click the labels icon.

![](../../.gitbook/assets/video1957132272-online-video-cut.gif)

When running a test suite or test plan via [the CLI](https://docs.loadmill.com/integrations/npm-modal), you can select to run flows that are assigned to a specific label by using the --labels command line option:

```
// Note, you can provide multiple labels separated by commas.
loadmill <test-suite-id> --test-suite -t <token> --labels "label1,label2"
```

Thus, by using labels, you will make sure that only relevant test flows run per a code-change, deploy etc.
