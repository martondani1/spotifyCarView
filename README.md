# Spotify car view app
Bring back car view into your spotify client!
Since spotify removed the car view at 2021 november, I'd like to create a spotify car view app client. I plan to make it using vue.js and nest it into cordova, so it can be deployed to any phone.


I've used cordova as a plugin for vue with this npm package:
https://www.npmjs.com/package/vue-cli-plugin-cordova


- To run the application, use: **npm run dev**
- To build andriod / ios versions, use: **cordova build android/ios**
- To emulate the app: **cordova emulate android/ios**

The **vue build** is configured in the _/config/index.js_ file, so the vue app needs to be builded first, before build the mobile versions. (The builded app by vue will go into the /www folder)

After that, the **cordova builds** are going to go into the **/build** folder