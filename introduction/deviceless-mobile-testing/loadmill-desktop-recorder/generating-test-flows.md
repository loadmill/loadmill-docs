# Generating test flows

Loadmill allows streamlining tests generation by capturing user behavior on a mobile device.

To generate a test follow the following steps:

1. Ensure your device is up and configured correctly with [mitm certificate](../installing-certificate-on-mobile-devices/) and [proxy settings](../configuring-proxy-on-mobile-devices/).
2. Start your application and position it's state to the beginning of a scenario
3. Start loadmill proxy by clicking<img src="../../../.gitbook/assets/image (16).png" alt="" data-size="line">, \
   Tip: make sure you start from an empty list, you can clear the residues by clicking <img src="../../../.gitbook/assets/image (11).png" alt="" data-size="line">.
4. Drive the application on your device by the scenario you want to capture, make sure requests are captured in the proxy
5. If needed, adjust the filter<img src="../../../.gitbook/assets/image (27).png" alt="" data-size="line">to focus or relevant domain(s) to reduce potential noise from irrelevant requests.
6. Once finished driving the scenario, click on <img src="../../../.gitbook/assets/image (17).png" alt="" data-size="line">button.\
   loadmill will filter out requests that are highly suspected as irrelevant and strikes them out. You can review the filtered requests and if needed restore them by selecting and clicking<img src="../../../.gitbook/assets/image (23).png" alt="" data-size="line">.
7. Adjust the destination suite in the suite field: <img src="../../../.gitbook/assets/image (32).png" alt="" data-size="line">
8. To generate the test, click on <img src="../../../.gitbook/assets/image (15).png" alt="" data-size="line">
9. To review the test navigate to Loadmill section <img src="../../../.gitbook/assets/image (28).png" alt="" data-size="line">go to Test suite\
   &#x20;<img src="../../../.gitbook/assets/image (1) (4).png" alt="" data-size="original">\
   And select your test suite, \
   The recently created flow in the list will be marked with the recent timestamp.
