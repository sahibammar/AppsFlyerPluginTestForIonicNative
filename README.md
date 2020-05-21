# AppsFlyer Plugin Test For Native Ionic App 
The purpose pf this project is to test AppsFlyer plugin for Ionic native. Here we are using Capacitor instead of Cordova. The project is tested for Android on a physical Android device.

### Building node_modules:
```
npm install
```

### Installing AppsFlyer plugin for native Ionic using Capacitor:
```
npm install cordova-plugin-appsflyer-sdk
npm install @ionic-native/appsflyer
ionic cap sync
```
### Running the project:
```
ionic serve
```
### Building the Android native app:
```
npm run build
npx cap add android
npx cap copy
npx cap open android
```
## What has been changed in scripts:
The required changes are already applied to this project so you dont need to do these changes your self. However if your are interested to know what has been changed, here is a summary:
 
### Changes to app.module.ts
1. Importing Appsflyer. To be added to app.module.ts
```
import { Appsflyer } from "@ionic-native/appsflyer/ngx";
```
2. Adding Appsflyer to providers. To be added to app.module.ts
```
 providers: [
   Appsflyer,
   ]
```

### Changes to home.page.ts
1. Importing Appsflyer. Check home.page.ts
```
import { Appsflyer } from "@ionic-native/appsflyer/ngx";
```
2. Defining appsflyer in constructor. Check home.page.ts
```
 constructor(
   private appsflyer: Appsflyer
```
3. Providing devkey acquired from Appsflyer. To be added to home.page.ts
```
const options = {
     devKey: "...", -- replace this with devkey you get from Appsflyer dashboard
     isDebug: true,
     onInstallConversionDataListener: true
   };
```
4 Initiating SDK. To be added to home.page.ts
```
   this.appsflyer
     .initSdk(options)
     .then(res => {
       console.log("INIT SDK");
       this.gcd = res.data;
       console.log(res);
     })
     .catch(err => {
       console.log(err);
     });
```
5. Register with App open. To be added to home.page.ts
```
   this.appsflyer
     .registerOnAppOpenAttribution()
     .then(res => {
       console.log("OAOA");
       this.oaoa = res.data;
       console.log(res);
     })
     .catch(err => {
       console.log(err);
     });
```
6. Track event. To be added to home.page.ts
```
 async trackEvent() {
   var eventName = "af_add_to_cart";
   var eventValues = {
     af_content_id: "id123",
     af_currency: "USD",
     af_revenue: "2"
   };
   this.appsflyer.trackEvent(eventName, eventValues);
   await this.presentToast("Event was sent successfully");
 }
```


## Notes:
1. You need to have Android studio installed and configured in your machine
2. After few second from launching the app in your native device you can see the Appsflyer dashboard updated
![alt text](https://github.com/sahibammar/AppsFlyerTest/raw/master/src/common/images/appsflyer_dashboard_snapshot.jpg "Logo Title Text 1")

