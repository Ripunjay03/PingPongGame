# Node Pong Game

This is a multiplayer Pong game project built with Node.js, Express, Socket.io, and Capacitor.

## Features

- Real-time multiplayer Pong gameplay using Socket.io
- Cross-platform support with web and Android app via Capacitor

## Running the Web App

1. Install dependencies:
   ```
   npm install
   ```
2. Start the backend server:
   ```
   npm start
   ```
   **Note:** The backend server now runs on port 3001 by default. If you want to use a different port, set the `PORT` environment variable before starting the server, e.g.:
   ```
   PORT=3001 npm start
   ```
3. Open `public/index.html` in a browser to play.

## Building and Running the Android App

1. Make sure you have Android Studio and Android SDK installed.
2. Replace the `socketServerUrl` in `www/client.js` with your backend server IP or domain, including the port if different from 3000, e.g.:
   ```js
   var socketServerUrl = "http://192.168.1.100:3001";
   ```
3. Build the web assets if applicable (add your build command in `package.json` scripts under `build`).
4. Sync Capacitor and build the Android app:
   ```
   npm run android:build
   ```
5. Open the Android project in Android Studio:
   ```
   npm run capacitor:open
   ```
6. Configure app signing for release:
   - Generate a keystore if you don't have one:
     ```
     keytool -genkey -v -keystore release.keystore -alias your-key-alias -keyalg RSA -keysize 2048 -validity 10000
     ```
   - Place the `release.keystore` file in the `android/app` directory.
   - Update `android/app/build.gradle` with your keystore details (store password, key alias, key password).
7. Build a signed APK or AAB for release:
   - In Android Studio, select "Build > Generate Signed Bundle / APK" and follow the prompts.
   - Or use Gradle command line:
     ```
     ./gradlew assembleRelease
     ```
8. Test the signed APK/AAB on devices before publishing.

## Notes

- The Android app uses Capacitor to wrap the web app.
- Socket.io client connects to the backend server specified in `socketServerUrl`.
- Ensure your backend server is accessible from the Android device network.
- The "Search for Match Online" feature allows players to find online opponents via matchmaking.
- If you encounter issues with matchmaking, check the browser console for errors and ensure the backend server is running and accessible.
