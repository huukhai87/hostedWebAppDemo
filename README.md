Creating a hosted web app using Cordova - Tutorial
====================================

After building a web site it was required have smart phone app especially for android phone.  
It turned out that building a web app is so easy.  
Here are simple steps to build a web app using [Cordova][cordova] and `cordova-plugin-hostedwebapp` plugin.

## Build Environment
* Windows 10
* Cordova version
```cmd
D:\cordovaApp>cordova --version
6.5.0
```

### Project Creation Steps
* Create a Cordova project
```cmd
D:\cordovaApp>cordova create hostedWebAppDemo io.altoransystem.hostedWebApp HostedWebAppDemo
```
* Get in a project folder
```cmd
D:\cordovaApp>cd hostedWebAppDemo
```
* Add android platform
```cmd
cordova platform add android@4.1 --save
```
* Add `cordova-plugin-hostedwebapp` plugin
```cmd
D:\cordovaApp\hostedWebAppDemo>cordova plugin add cordova-plugin-hostedwebapp --save
```
The `cordova-plugin-hostedwebapp` is the heart of engine for building a hosted web app.
* Add additional plugins
```cmd
D:\cordovaApp\hostedWebAppDemo>cordova plugin add cordova-plugin-vibration --save
D:\cordovaApp\hostedWebAppDemo>cordova plugin add cordova-plugin-dialogs --save
D:\cordovaApp\hostedWebAppDemo>cordova plugin add de.appplant.cordova.plugin.local-notification --save
```
* Add manififest file to the root folder of the Cordova application alongside `config.xml`  
Create mainifest.json
```cmd
D:\cordovaApp\hostedWebAppDemo>vim manifest.json
```
manifest.json file:
```json
{
	"name": "Cordova hosted web app",
	"short_name": "hostedWebApp",
	"start_url": "http://192.168.219.118:3000/",
	"mjs_api_access": [
		{ "match": "*", "access": "cordova", "platform": "ios,windows,android" }
	]
}
```
 * start_url: Url for a web site
 * mjs_api_access: it enables cordova plugin API access within web pages.
## Build & Run App on the Android device
* Directly run app through USB cable connection to Android device
```cmd
D:\cordovaApp>cordova run android
```
* Build apk for android
```cmd
D:\cordovaApp>cordova build android
Built the following apk(s):
    D:\cordovaApp\hostedWebAppDemo\platforms\android\build\outputs\apk\android-debug.apk
```
## License

This software is released under the [Apache 2.0 License][apache2_license].

© 2017 Altoran System. All rights reserved

[cordova]: https://cordova.apache.org
[apache2_license]: http://opensource.org/licenses/Apache-2.0

