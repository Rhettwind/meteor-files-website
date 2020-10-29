[![support](https://img.shields.io/badge/support-GitHub-white)](https://github.com/sponsors/dr-dimitru)
[![support](https://img.shields.io/badge/support-PayPal-white)](https://paypal.me/veliovgroup)
<a href="https://ostr.io/info/built-by-developers-for-developers">
  <img src="https://ostr.io/apple-touch-icon-60x60.png" height="20">
</a>

# File sharing web app

This is repository with codebase of the web application available at [files.veliov.com](https://files.veliov.com/). It's fully-featured file-sharing service build on top of [`ostrio:files` library](https://github.com/veliovgroup/Meteor-Files) and [meteor.js](https://docs.meteor.com).

## Links:

- Website: __[files.veliov.com](https://files.veliov.com/)__
- Meteor's [tutorials repository](https://github.com/veliovgroup/meteor-snippets#meteor-snippets)
- [`ostrio:files`](https://github.com/veliovgroup/Meteor-Files) library
- Hekoru [deploy instructions](https://github.com/veliovgroup/meteor-files-website/blob/master/heroku-deploy.md)

## Functionality:

- Upload / Download Files
- Drag'n'drop support (*files only, folders is not supported yet*)
- AWS:S3 as storage
- PWA with Push Notifications
- Heroku support (*including one-click-deploy*)

## Quick start:

### Activate AWS:S3

1. Read [this article](https://github.com/VeliovGroup/Meteor-Files/wiki/AWS-S3-Integration)
2. After creating S3 bucket, create CloudFront Distribution and attach it to S3 bucket
3. Set S3 credentials into `METEOR_SETTINGS` env.var or pass as the file, read [here for more info](http://docs.meteor.com/#/full/meteor_settings), alternatively (*if something not working*) set `S3` env.var
4. You can pass S3 credentials as JSON-string when using "*Heroku's one click install-button*"

S3 credentials format (*region is required*):

```js
{
  "s3": {
    "key": "xxx",
    "secret": "xxx",
    "bucket": "xxx",
    "region": "xxx"
  }
}
```

### Activate Web Push Notifications

1. Install [`web-push` NPM](https://www.npmjs.com/package/web-push) package
2. Generate key-pair using `webpush.generateVAPIDKeys()`;
3. Set VAPID credentials into `METEOR_SETTINGS` env.var or pass as the file, read [here for more info](http://docs.meteor.com/#/full/meteor_settings)

VAPID credentials format:

```js
{
  "public": {
    "vapid": {
      "publicKey": ""
    }
  },
  "vapid": {
    "email": "mailto:webmaster@example.com", // SET TO REAL EMAIL
    "privateKey": ""
  }
}
```

### Application settings

All supported and annotated settings

```js
{
  "storagePath": "/data/meteor-files/uploads", // LOCAL STORAGE ON THE SERVER
  "public": {
    "maxFileSizeMb": 1024, // MAXIMUM UPLOAD FILE-SIZE
    "maxFilesQty": 8, // MAXIMUM AMOUNT OF SIMULTANEOUSLY UPLOADED FILES
    "fileTTLSec": 259200, // 3 days; FILE'S TTL IN SECONDS
    "vapid": { // VAPID WEB PUSH NOTIFICATIONS CONFIGURATION
      "publicKey": "" // WEB PUSH NOTIFICATION PUBLIC KEY
    }
  },
  "s3": { // AWS:S#3 CLOUD STORAGE CREDENTIALS
    "key": "",
    "secret": "",
    "bucket": "",
    "region": ""
  },
  "vapid": { // VAPID WEB PUSH NOTIFICATIONS CONFIGURATION
    "email": "mailto:webmaster@example.com", // WEB PUSH NOTIFICATION EMAIL
    "privateKey": "" // WEB PUSH NOTIFICATION PRIVATE KEY
  }
}
```

### Deployment

Learn more about DevOps, deployment, and running this app live in [DevOps and Deployment tutorial](https://github.com/veliovgroup/meteor-snippets/tree/main/devops).

## Support this project:

- Star on [GitHub](https://github.com/VeliovGroup/Meteor-Files)
- Star on [Atmosphere](https://atmospherejs.com/ostrio/files)
- Share via [Facebook](https://www.facebook.com/sharer.php?u=https%3A%2F%2Fgithub.com%2FVeliovGroup%2FMeteor-Files) and [Twitter](https://twitter.com/share?url=https%3A%2F%2Fgithub.com%2FVeliovGroup%2FMeteor-Files)
- [Sponsor via GitHub](https://github.com/sponsors/dr-dimitru)
- [Support via PayPal](https://paypal.me/veliovgroup) — support my open source contributions once or on regular basis
- Use [ostr.io](https://ostr.io) — [Monitoring](https://snmp-monitoring.com), [Analytics](https://ostr.io/info/web-analytics), [WebSec](https://domain-protection.info), [Web-CRON](https://web-cron.info) and [Pre-rendering](https://prerendering.com) for a website