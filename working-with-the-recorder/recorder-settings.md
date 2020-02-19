# Recorder settings

Use the advanced recorder settings to create meaningful replay-able tests that are easy to configure. You can control these settings [on this page](https://www.loadmill.com/app/user/settings/recordings).

### Split sessions by URLs

In general we want the test cases created based on recorded data, to be short and focused as possible. By default, Loadmill will split a recorded user session into two separate Loadmill test flow, if the user hasn't been active for 5 minutes. 

In many cases, you will want to control when a session is split into separate test cases. Using this setting, you can add API URLs that will define the beginning of a new test case each time they are called.

Note: You can also use raw JavaScript to fire an event from your code to splits a recorded session:

`navigator.serviceWorker.controller.postMessage({ type: "reset-session" });`

### URL Filters

Use this setting to filter API calls that are not relevant for you tests i.e. marketing, monitoring, analytics and other external integrations.

### Special Keys

Use this setting to manage important Special Keys located in your POST requests body. This way, we can make sure they won’t be missed during the recording processing phase.

### Entities Synonyms

Entities Synonyms help us to detect same entities with different names like a 'Jet' and an 'Airplane'.

Here you can add and manage entities synonyms. This way, we can make sure they won’t be missed during the recording processing phase. Synonyms must be entered in a list and separated by comas. I.e. Plane, Aircraft, Jet

