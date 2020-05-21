# AppsFlyerTest
Testing AppsFlyer plugin for Ionic native which uses Capacitor. 

Building node_modules:
```
npm install
```

Installing AppsFlyer plugin for native Ionic using Capacitor:
```
npm install cordova-plugin-appsflyer-sdk
npm install @ionic-native/appsflyer
ionic cap sync
```
## What do you need to change in your script:
Changes to app.module.ts
1. Importing Appsflyer. you need to add the following to app.module.ts
```
import { Appsflyer } from "@ionic-native/appsflyer/ngx";
```

Running:
```
ionic serve
```

