# @deliverybot/firebase

Configures a firebase deployment target by implementing all services on top of
firebase.

### Deployment Prerequisites

* Google Cloud account w/ firebase Blaze pay-as-you-go plan
  * IAM API enabled for firebase project
  * Sevice account with following `Service Account Token Creator` role
* Firebase cli

### Deployment configuration

During deployments files are copied from `env/<environment>` into `lib/config`
which should hold the necessary configuration for the application. The two
expected configuration files are:

`client.json`

```javascript
{
  "firebase": {
    "apiKey": "AIza....",
    "projectId": "my-firebase-project",
    "messagingSenderId": "1234546",
    "databaseURL": "https://YOUR_APP.firebaseio.com"
  }
  "stackdriver": ... // Stackdriver api key and project.
}
```

`server.json`

```javascript
{
  "ENVIRONMENT": "production",
  "NODE_ENV": "production",
  "LOG_FORMAT": "json",
  "BASE_URL": "https://app.deliverybot.dev",
  "PRIVATE_KEY": "GitHub private key",
  "CLIENT_ID": "GitHub client id",
  "CLIENT_SECRET": "GitHub client secret",
  "WEBHOOK_SECRET": "GitHub webhook client secret",
  "WEBHOOK_PATH": "Webhook path suffix",
  "APP_ID": "GitHub app id",
  "SLACK_APP_ID": "Slack app id",
  "SLACK_CLIENT_ID": "Slack client id",
  "SLACK_CLIENT_SECRET": "Slack client secret",
  "SLACK_SECRET": "Slack signing secret",
  "SLACK_LOGIN_URL": "Slack app url",
}
```

## Deployment steps

```shell
firebase login        # Login using google cloud credentials
firebase use --add    # Add project alias
yarn run deploy:{env} # Execute deployment
```
