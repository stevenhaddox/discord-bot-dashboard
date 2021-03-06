# Get Started

Welcome to the starter guide of the Discord Bot Dashboard.

This dashboard was written for bot developers who want to have a better overview of their own bot
and to have the possibility to control and analyse its behaviour.

### Creating a config file

Before using the dashboard, we recommend to use ``dotenv`` (if you are not already) and to create a ``.env`` file with the necessary values:

```dotenv
SESSION_SECRET=your_own_secret_code_for_sessions
CLIENT_SECRET=your_client_secret_code
REDIRECT_URI=your_redirect_uri
```

- To get your **client secret**, go to: 

**discordapp.com >> Developer Portal >> Your Bot >> General Information**

- For setting up the **OAuth2 connection** and for the functionality of the login, please go to:

**(Steps before) >> Your Bot >> OAuth2**

- Now you need to **specify a redirect URI** in the following format (it must exactly match):

```text
http(s)://[your-domain-or-ip.com]/auth/discord/callback
```

...and now you are done with setting up the application! :)

### Implementing the dashboard

Now it is time to implement the dashboard into your bot project. It is very simple!

- After setting up the ``Discord.Client``, you need to give the dashboard access to the ``OAuth2Applictaion`` class like this:

````js
// Discord client setup
const client = new Discord.Client();
const oAuth = Discord.OAuth2Application;
// dotenv
require('dotenv').config();
// Dashboard package
const dashboard = require("discord-bot-dashboard");

// ...
client.on('ready', () => {

  dashboard.run(client, { port: your_open_port, clientSecret: process.env.CLIENT_SECRET, redirectURI: process.env.REDIRECT_URI}, oAuth);
  //...

});
//...
````

Now the dashboard can be used! Just restart your bot and try it out!