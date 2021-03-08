# Data sync connection to GitHub

## Data sync connection to GitHub

Loadmill provides the ability to store the Test Suite data in your GitHub repository so you always have a backup when needed. In addition, the data sync connection to GitHub enables you to always track changes made to Test Suites.

### Setup

1. Navigate to **Settings - Integrations - CONNECT TO GITHUB.** Note: only team admins can perform this action.
2. You will promptly be redirected to GitHub and then back to Loadmill, scroll down to the **Setup data sync connection to GitHub** section.
3. Choose a repository to enable data sync to. 

![The GitHub data sync integration setup page](../../.gitbook/assets/screen-shot-2021-03-04-at-12.07.23.png)

    4. Click on **CONNECT TO REPO.** Now it's time to fill it in with your Test Suite data. 🥳 

### **Usage**

To sync your Test Suite data with your GitHub repository, follow the steps below:

1. Navigate to a relevant Test Suite and click on the **SYNC TO GIT** button. 

![The Sync to Git button](../../.gitbook/assets/screenshot-2021-03-03t132730.064.png)

  2. Enter an initial ****commit message and click **COMMIT** to sync the Test Suite data. 

![Entering a commit message in Loadmill](../../.gitbook/assets/screen-shot-2021-03-04-at-12.08.36.png)

**What happens next?** Loadmill creates the **loadmill-sync** branch and the **loadmill-suites** folder in the repository. ****In addition, a new file with the Test Suite data is created in the **loadmill-suites** folder. Its name matches the Test Suite ID. 

Easily navigate to the commit by clicking on **GO TO COMMIT** at the bottom left corner of the screen.

![](../../.gitbook/assets/screen-shot-2021-03-03-at-13.34.26.png)

The commit message in GitHub includes your Loadmill username and the commit message you entered in Loadmill. 

![Test Suite data file in GitHub](../../.gitbook/assets/screenshot-2021-03-04t121904.550.png)

**Another great thing about this feature** is that, over time, you can always track changes made to Test Suites. Just remember to enter commit messages to sync the Test Suite changes to GitHub.

![Showing changes made to the Test Suite ](../../.gitbook/assets/screenshot-2021-03-03t140700.969.png)

To reset the integration, click on **DISCONNECT** within Settings - Integrations - Setup data sync connection to Github.



