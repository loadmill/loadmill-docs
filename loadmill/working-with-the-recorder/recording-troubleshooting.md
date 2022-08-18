# Recording troubleshooting

### I'm trying to record my tests by using the Chrome recorder extension but getting error that I need to login to Loadmill however I'm logged in... Any idea on how to fix it?

There are a few ones 🙂:

* It might be related to the 3rd party blocking policy, see how to disable it [here](https://support.cloudhq.net/how-to-enable-3rd-party-cookies-in-google-chrome-browser/).&#x20;
* If the above option didn't help, you might have the "don't track" option enabled in Chrome and you will need to whitelist app.loadmill.com, see where to do this whitelisting [here](https://support.google.com/chrome/answer/2790761?hl=en\&co=GENIE.Platform%3DDesktop).&#x20;
* Sometimes other installed extensions like Adblock may cause this, thus we recommend switching them off while recording.
