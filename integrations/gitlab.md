# GitLab

You can easily set up Loadmill to automatically run your tests as part of your continuous integration (CI) workflow.

### Gitlab Integration Setup

1. Go to **Settings** > **Integrations**.
2. Click on the <img src="../.gitbook/assets/connect-to-gitlab.png" alt="connect to gitlab" data-size="line"> button.
3. Authorize Loadmill to use your account.
4. Select the project to enable data sync to and click on <img src="../.gitbook/assets/connect-to-project.png" alt="connect to project" data-size="line">.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FZmOShciaVeCXCJMwCgGs%2Fgitlab-integration-setup.mp4?alt=media&token=315d1500-8a53-44fb-b941-627edbd840cd" %}

### Syncing your Test Suite

Now that your GitLab integration is all set up head over and sync your Test Suite to your repository.

#### To sync your Test Suite to your GitLab repository:

1. Select the Test Suite you wish to connect your repository to.
2. Select the "GitLab Sync" tab.
3. Select or create a new branch from the Sync Actions section.
4. Enter a commit message (example: my first commit).
5. Click on <img src="../.gitbook/assets/bitbucket-commit.png" alt="commit" data-size="line">.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2Fg73Y2LbPirzzylUfbvok%2Fgitlab-integration-commit.mp4?alt=media&token=8747b986-c060-4059-8b7a-97409379b1f5" %}

### Merging Branches

Loadmill makes it easy to merge your commits directly through its interface. Simply select the commits you want to merge, and Loadmill will handle the rest.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FMbS05BMOxHN3XHNOqfdf%2Fgitlab-integration-merge.mp4?alt=media&token=26f195d5-da9d-48c7-b3a5-2856cacc8939" %}

### Running Test Plans with GitLab

You can configure your Test Plan to run with the latest syncs of your test suites repositories. That means your Test Plan will run with the latest Test Suite synced commits.

**To configure this option:**

1. Head over to any Test Plan you wish to connect your repository to.
2. Select the "Run Settings" tab of the Test Plan.
3. Select the branch containing the synced Test Suite.

Your Test Plan will now run on the latest committed version of the Test Suites.

{% hint style="warning" %}
Changing your Test Suites locally will not affect the Test Plan run until you commit your changes to GitLab.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FPvmMnSySejHHi9rKDoI5%2Fgitlab-integration-testplan.mp4?alt=media&token=708e8f19-f20a-46df-919f-ef8c93347cc6" %}

### Syncing from your GitLab Repository

1. Edit your Test Suite file from your GitLab repository.
2. Commit the changes made.
3. Go back to your Test Suite > GitLab Sync on the Loadmill app.
4. Notice the latest commit under the "Branch History" section.
5. Click on "Checkout".
6. See the changes on your Test Suite.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FWEWo1gCuyWABod6x20aU%2Fgitlab-integration-commit-frombranch.mp4?alt=media&token=15106924-eedb-4c47-9664-53958ca98711" %}
