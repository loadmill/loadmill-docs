# Bitbucket

Bitbucket integration is a great way to speed up your development process. By integrating Bitbucket with Loadmill, you can automatically test your code as you make changes. This makes it easy to find and fix bugs quickly and ensures that your code is always up to date.

{% hint style="warning" %}
Make sure to have an Atlassian account to connect to Bitbucket.
{% endhint %}

### Bitbucket Integration Setup

1. Go to **Settings** > **Integrations**.
2. Click on the <img src="../.gitbook/assets/connect-bitbucket.png" alt="connect to bitbucket" data-size="line"> button.
3. Grand Loadmill access to your Bitbucket account.
4. Select your repository.

{% hint style="info" %}
You might be redirected to the Atlassian login page when connecting Loadmill to Bitbucket. Login using your Atlassian credentials and set up a Bitbucket username to complete the registration.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FAoPecxoS75EvZifcSToh%2Fbitbucket-integration--setup.mp4?alt=media&token=608af104-9172-451a-b62b-6ffebdd714c8" %}

### Syncing your Test Suite/Plan

Now that your Bitbucket integration is all set up head over and sync your Test Suites/Plans to your repositories.

#### To sync your Test Suite to your Bitbucket repository:

1. Select the Test Suite you wish to connect your repository to.
2. Select the "Bitbucket Sync" tab.
3. Select or create a new branch from the Sync Actions section.
4. Enter a commit message (example: my first commit).
5. Click on <img src="../.gitbook/assets/bitbucket-commit.png" alt="commit" data-size="line">.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FoYsGaOa76Xv8wZUg2g6t%2Fbitbucket-commit.mp4?alt=media&token=eeaef713-356c-4e13-9fba-ad3b33a3d7fa" %}

#### To sync your Test Plan to your Bitbucket repository:

You can configure your Test Plan to run with the latest syncs of your test suites repositories. That means that if one of your Test Suites is running with a previous configuration from a previous commit your Test Plan will run with the latest commit regardless.

**To configure this option:**

1. Head over to any Test Suite you wish to connect your repository to.
2. Select the "Run Settings" tab of the Test Plan.
3. Select the branch containing the Test Suite repositories.

Your Test Plan will now run on the latest commits of its Test Suites.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2F3dW2BqSf8Bkn0zKdFK4G%2Fbitbucket-commit_test_plan.mp4?alt=media&token=1be5fdcd-96ef-402a-a71a-a96dcaaf7981" %}

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

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FzFSVV5CuiFmt7viw66tF%2Fbitbucket-commit-from-bitbucket.mp4?alt=media&token=470a6ec1-7439-40f9-be9d-c7e6471aec06" %}

### Creating/Updating Branch

To create a new branch (or update an existing one) from the Loadmill app:

1. Head over to your Test Suite.
2. Select the "Bitbucket Sync" Tab.
3. Under Sync **Actions** > **Commits**.
4. Type in the new branch name (or select an existing one).
5. Commit the changes done on your test suite.
6. Click on "Create Pull Request"

Once you click on the "Create Pull Request" button, your Test Suite changes will immediately be pushed to the Bitbucket branch repository. There you'll be able to manage it and merge it when ready.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FymGuQAh5AcZ4Nf6zJQ7A%2Fbitbucket-commit_new_branch.mp4?alt=media&token=2ef0e1dd-c8c4-448e-b890-7013d4c6b1cb" %}
