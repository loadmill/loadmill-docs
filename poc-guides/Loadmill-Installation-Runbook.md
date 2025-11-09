# Loadmill Installation & Deployment Runbook

## 1. Deployment Options
Loadmill supports multiple deployment approaches depending on your organization’s environment:
- **Desktop Runner (POC Setup):** Ideal for proof-of-concept or local execution. Installed on a user machine to run tests inside a VPN.
- **Docker/Server Runner:** Recommended for production. Deploy the Loadmill runner as a Docker container on an internal server. It can auto-update and connect to Loadmill Cloud for orchestration.
- **Cloud Runner:** Fully managed by Loadmill. Suitable when internal applications are publicly accessible or whitelisted.

## 2. Recorder Setup
To record browser interactions for Loadmill’s User Behavior Testing, install the Loadmill Chrome Extension:
1. Visit https://app.loadmill.com/ and create or log in to your account.
2. Navigate to 'Recordings' → 'Set up the Recorder'.
3. Install the Chrome Extension from the Chrome Web Store.
4. Click the Loadmill icon in Chrome, sign in, and start recording your flow.
5. Save the recording directly to your Loadmill workspace.

> Note: Recording via the extension does not require admin rights. Execution requires either the Desktop App or Server Runner.

## 3. Installation Requirements
- The Desktop App requires one-time admin rights for installation.
- Automatic updates occur every two weeks for the embedded runner; the app wrapper updates infrequently (twice per year).
- Ensure outbound internet access to app.loadmill.com and related API endpoints.
- No inbound firewall rules are needed when using a Desktop App Runner within a VPN.

## 4. Proxy & SSL Configuration
If your environment uses a corporate proxy or SSL inspection:
- Configure proxy settings in the Loadmill Desktop App under 'Settings'.
- If required, install the Loadmill CA certificate for HTTPS traffic capture.
- When recording with the Chrome Extension, no SSL certificate configuration is needed.

## 5. CI/CD Integration
Loadmill integrates with CI/CD platforms like Jenkins, GitHub Actions, and Azure DevOps. You can trigger Loadmill tests via API, npm, or Docker ([read more here](/integrations/npm-modal)).

**Example using npm:**
```bash
npm install -g loadmill
loadmill <TEST_PLAN_ID> --token <YOUR_API_TOKEN>
```
**Example using Docker:**
```bash
docker run -it --rm -e TOKEN=INSERT_TOKEN_HERE -e TP_ID=TEST_PLAN_ID_HERE loadmill/runner
```

## 6. Network & Whitelisting
For Desktop and Docker runners inside a VPN, no external whitelisting is required. Cloud runners require IP whitelisting or a NAT gateway for access to internal systems.

## 7. Permissions and Updates
- Desktop App auto-updates both wrapper and embedded runner.
- No recurring admin rights are needed post-installation.
- If updates fail, verify write permissions to the installation directory.

## 8. Common Installation Issues
- **Issue:** Certificate/Proxy errors → Configure SSL or disable interception for app.loadmill.com.
- **Issue:** Tests fail to run → Ensure the runner has outbound internet access.
- **Issue:** Chrome Extension records but doesn’t replay → Install the Desktop or Docker runner.

## 9. Summary: POC vs Long-Term Setup

| Feature                | POC Setup (Desktop App) | Long-Term Setup (Docker Runner) |
|------------------------|-------------------------|----------------------------------|
| Network Access         | Runs inside VPN, outbound only | Server inside network, managed via CI |
| Whitelisting           | Not required            | Optional for cloud access        |
| CI/CD Integration      | Manual or limited       | Automated via Loadmill CLI or API|
| Admin Rights           | Needed once             | Needed once (server setup)       |
| Auto Updates           | Yes                     | Yes (Docker auto-pull)           |
