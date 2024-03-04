# iOS certificate installation

To deploy a certificate into an iOS device, follow these steps:

1. **Download the certificate**: In loadmill desktop app, go to the proxy section, download the certificate by clicking on![](<../../../.gitbook/assets/image (52).png>)button. Transfer the certificate file (usually in `.cer` or `.crt` format) to your device (ie. via AirDrop or Google drive).
2. **Install the certificate**: Once the certificate file is downloaded, a prompt will appear asking to review and install a profile.\
   ![](<../../../.gitbook/assets/image (119).png>)
3. Go to device settings and select "Profile Downloaded"\
   ![](<../../../.gitbook/assets/image (21) (2).png>)
4. Click on install,\
   You will be prompted for your device password, proceed to completion.\
   ![](<../../../.gitbook/assets/image (117).png>)\

5. **Trust the certificate**: After the certificate is installed, you need to manually trust it. To do this, go to `Settings` > `General` > `About` > `Certificate Trust Settings`. Under the "Enable full trust for root certificates" section, find the Loadmill certificate you just installed and toggle the switch to enable trust for the certificate.\
   ![](<../../../.gitbook/assets/image (20) (2).png>)

By following these steps, you can successfully deploy a certificate into your iOS device and configure it to work with the Loadmill MITM proxy for deviceless testing. This will enable you to capture and analyze encrypted API traffic from your iOS device, allowing for more comprehensive and accurate test scenarios.
