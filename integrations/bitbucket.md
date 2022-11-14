# Bitbucket

Bitbucket integration is a great way to speed up your development process. By integrating Bitbucket with Loadmill, you can automatically test your code as you make changes. This makes it easy to find and fix bugs quickly and ensures that your code is always up to date.

{% hint style="warning" %}
Make sure to have an Atlassian account to connect to Bitbucket.
{% endhint %}

### Bitbucket Integration Setup

1. Go to **Settings** > **Integrations**.
2. Click on the <img src="../.gitbook/assets/connect-bitbucket.png" alt="connect to bitbucket" data-size="line"> button.
3. Grant Loadmill access to your Bitbucket account.
4. Select your repository.

{% hint style="info" %}
You might be redirected to the Atlassian login page when connecting Loadmill to Bitbucket. Login using your Atlassian credentials and set up a Bitbucket username to complete the registration.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FMxs4VbGA570CeZrxXJjo%2Fbitbucket-integration_setup.mp4?alt=media&token=a48633f0-d02b-407a-bf5b-e0c976f927f8" %}

### Syncing your Test Suite

Now that your Bitbucket integration is all set up head over and sync your Test Suite to your repository.

#### To sync your Test Suite to your Bitbucket repository:

1. Select the Test Suite you wish to connect your repository to.
2. Select the "Bitbucket Sync" tab.
3. Select or create a new branch from the Sync Actions section.
4. Enter a commit message (example: my first commit).
5. Click on <img src="../.gitbook/assets/bitbucket-commit.png" alt="commit" data-size="line">.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FK9u9JP9huaXUypuo1EB7%2Fbitbucket-integration_commit.mp4?alt=media&token=709b5619-b5c8-4a42-8b75-3de0cac630f9" %}

### Running Test Plans with Bitbucket

You can configure your Test Plan to run with the latest syncs of your test suites repositories. That means your Test Plan will run with the latest Test Suite synced commits.

**To configure this option:**

1. Head over to any Test Plan you wish to connect your repository to.
2. Select the "Run Settings" tab of the Test Plan.
3. Select the branch containing the synced Test Suite.

Your Test Plan will now run on the latest committed version of the Test Suites.

{% hint style="warning" %}
Changing your Test Suites locally will not affect the Test Plan run until you commit your changes to Bitbucket.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FRXLm6IUBG19fm9ecyUuc%2Fbitbucket-integration_test-plan.mp4?alt=media&token=fbeabdd3-9244-4c30-8ddb-4c6db50df89d" %}

### Syncing from your Bitbucket Repository

Loadmill can similarly track syncs made directly through Bitbucket. Simply commit a new change from your repository and you'll be able to see the commit change under the Bitbucket Sync tab of your Test Suite.

To do that:

1. Edit your Test Suite file from your Bitbucket repository.
2. Commit the changes made.
3. Enter your commit message and create a pull request from this change.
4. Click on "Merge" from your pull request.
5. Go back to your Test Suite > Bitbucket Sync on the Loadmill app.
6. Notice the latest commit under the "Branch History" section.
7. Click on "Checkout".
8. See the changes on your Test Suite.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FAjTuQPBwPL9MEQDTSr7s%2Fbitbucket-integration_commit-back.mp4?alt=media&token=7ac1656c-cbe1-4f53-ae0b-257354d040a2" %}

### Creating/Updating Branch

To create a new branch (or update an existing one) from the Loadmill app:

1. Head over to your Test Suite.
2. Select the "Bitbucket Sync" Tab.
3. Under Sync **Actions** > **Commits**.
4. Type in the new branch name (or select an existing one).
5. Commit the changes done on your test suite.
6. Click on "Create Pull Request"

Clicking "Create Pull Request" enables you to view the changes in the Test Suite and create a pull request for your synced Bitbucket branch. There, you'll be able to manage and merge when ready.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FpiyA0h5OL6WetHjQKI9q%2Fbitbucket-integration_new-branch.mp4?alt=media&token=5c400fc9-0e1e-46da-8377-a9418a156b63" %}
