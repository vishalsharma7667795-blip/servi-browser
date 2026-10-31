# SERVI Browser — Android source project

A native Kotlin Android browser starter with a dark navy/electric-blue identity inspired by the SERVI / EduSpace visual direction. It uses Android System WebView; it is not an HTML wrapper.

## Included

- Native Android app (`com.servi.browser`)
- Custom SERVI vector mark, dark theme, and animated fading splash/loading screen
- Address/search bar with Google, Bing, DuckDuckGo and Yahoo options
- Back, forward, reload, home, tabs, new tab, desktop-site request and page sharing
- WebView downloads through Android DownloadManager
- Incognito toggle with a visible mode indicator
- Privacy-first defaults: no saved browser-history list, no password/form saving, no app backup, and temporary cookies/site storage/cache cleared on app exit, on the next launch, when switching privacy modes, or when the user clears session data
- GitHub Actions workflow to build a debug APK

## Privacy behaviour — read this

The app does not write a browsing-history database and does not save passwords. The browser keeps only the WebView's in-memory back/forward history for the currently open tab. Websites may use cookies or site storage temporarily while the app is running so ordinary sign-in flows can work. That temporary session data is cleared on exit and again before the next browser session starts. Android may terminate an app without calling `onDestroy`; startup cleanup is included for that case.

Incognito is a temporary session mode. Switching into or out of it closes the open tabs and clears session data. It is not a separate operating-system profile, VPN, tracker blocker, or anonymity tool. Websites and network providers can still observe requests sent to them. Downloads are saved to the device's Downloads folder and are not automatically deleted with browser session data.

## Build in Android Studio

1. Install Android Studio with Android SDK Platform 35 and JDK 17.
2. Extract this ZIP.
3. In Android Studio choose **Open** and select the extracted `SERVI-Browser-Privacy` folder (the folder containing `settings.gradle.kts`).
4. Let Gradle sync finish.
5. Choose **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. The debug APK is normally created at `app/build/outputs/apk/debug/app-debug.apk`.

The project uses Android Gradle Plugin 8.7.3, Kotlin 2.0.21 and Gradle 8.9. The project ZIP does not include a Gradle wrapper binary; Android Studio can sync the Gradle project, or use the included GitHub Actions workflow.

## Build on GitHub

1. Extract the ZIP on your computer.
2. Open your repository: `https://github.com/vishalsharma7667795-blip/servi-browser`.
3. Choose **Add file → Upload files**.
4. Upload the *contents* of this project folder (including `.github`, `app`, and the root Gradle files), not the ZIP itself.
5. Commit the changes to `main`.
6. Open **Actions → Build SERVI Browser APK**. The workflow also runs on pushes to `main`.
7. When the run succeeds, open it and download **SERVI-Browser-debug-APK** under Artifacts.

## Important limitations

- This is a WebView-based browser. Compatibility and performance depend on the Android System WebView installed on the device; it is not a full Chromium/Chrome replacement.
- Some sites block embedded browsers, use DRM, or require authentication/identity features that WebView may not support.
- This source project has not been represented as a security-audited browser. Review and test it on physical devices before public release.
