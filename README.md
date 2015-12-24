Krexus OTA Updates (based on SlimOTA)
-------
A very simple OTA checker with Android Settings look and feel.

How it works
------------
It parses the OTA xml file that you put in your file hosting and compares the version number with the local one.
If the version is newer, it notifies the user for a new ROM update.

How to use
----------
* Prepare the OTA xml file. Use this [template](https://raw.githubusercontent.com/krexus/packages_apps_KrexusOTA/mr1/examples/ota_marshmallow.xml).
* Upload it to your file hosting and create a hot link of it
* Copy the [ota_conf template](https://raw.githubusercontent.com/krexus/packages_apps_KrexusOTA/mr1/examples/ota_conf) to app/src/main/assets folder
  * If you are buiding this app as part of the ROM, you need to copy ota_conf in the android root folder.
  * The Android.mk will pick it up and copy it to app/src/main/assets folder automatically.
* Replace the "ota_url" with your OTA xml hot link
* Define how KrexusOTA should know about the "version". The version must be parseable to a date.
  * Usually, the version is a part of a build name. For example, the 151221 in the krexus_mm-151221-hammerhead.
* Adjust the OTA configuration according to your build name on how should KrexusOTA parse the version
  * Find a key in build.prop that represents the krexus_mm-151221-hammerhead and set it in the "version_name"
  * Set the delimiter in "version_delimiter" to "-"
  * Set the date format in "version_format" to "yyMMdd"
  * Set the position in "version_position" to "2" (zero based)
* Find a key in build.prop that represents your device name and set it in the "device_name"
  * KrexusOTA will search this device name in the OTA xml file

How to build
------------
* As part of the ROM
  * Add this repo in your manifest
  * Include this app in the build process
* As a standalone app
  * With Android.mk: make KrexusOTA
  * With Android Studio: Import this repo to your Android Studio and build it from there
  
Credits
-------
* [Slim team](http://slimroms.net/)
  * For the original idea of the SlimCenter and app icon
* [CommonsWare Android Components](https://github.com/commonsguy/cwac-wakeful)
  * For the wakeful intent service that is used in this app

Screenshots
-----------
<img alt="Screenshot"
   width="270" height="480" 
   src="https://raw.githubusercontent.com/krexus/packages_apps_KrexusOTA/mr1/screenshots/Screenshot_20151224-025423.png" />
