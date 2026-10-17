# StudySpark AI — Android wrapper project

This project packages the existing hosted StudySpark AI web app in a native Android WebView shell.

Live web app: https://studyspark-ai-mvfo4d.v2.appdeploy.ai/

## Build an APK with Android Studio

1. Install the current stable Android Studio.
2. Extract this ZIP.
3. In Android Studio choose **Open** and select the `StudySparkAI-Android` folder.
4. Allow Gradle sync and install any SDK components Android Studio requests.
5. For a test APK, choose **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. Android Studio will show the output location, usually `app/build/outputs/apk/debug/app-debug.apk`.
7. Copy that APK to your Android phone and open it. If Android asks, allow installing apps from the app you used to open the APK.

## Important notes

- This is a buildable Android Studio project, **not a prebuilt APK**. A compatible Android SDK/Gradle environment is required to compile it.
- The app loads the hosted StudySpark AI website, so an internet connection is required. StudySpark AI's server-side AI features and student sign-in continue to use the existing web service.
- This project does not bundle the website for offline use, and it does not bypass the site's authentication or server requirements.
- Before public distribution, change the application ID in `app/build.gradle.kts`, add a proper signing configuration, and test on multiple Android devices.
- The WebView restricts navigation to the app's own site. External links open in the browser.


## Build the APK using only your phone (GitHub Actions)

This route uses GitHub's cloud computer to compile the APK; you do not need Android Studio on your phone. It requires a GitHub account and an internet connection.

1. In your phone browser, open GitHub and create a **new repository** named `StudySparkAI-Android`. A private repository is fine.
2. Upload the **contents** of this folder to the repository (including the hidden `.github/workflows/build-apk.yml` file). If GitHub's mobile website does not show hidden folders, switch the browser to Desktop site or use GitHub's web upload page from a browser that supports selecting the folder. Make sure `.github/workflows/build-apk.yml` is included.
3. Open the repository's **Actions** tab. Select **Build StudySpark AI APK** and tap **Run workflow**. If prompted, choose the `main` branch.
4. Wait for the workflow to finish successfully. Open the completed workflow run, scroll to **Artifacts**, and download `StudySparkAI-debug-apk`.
5. Extract the downloaded artifact ZIP on your phone. Inside it, find `app-debug.apk`, tap it, and allow installs from that source if Android asks. Only install APKs you built or trust.

The workflow creates a **debug APK** for testing and personal sharing. It is not a Play Store release and is not signed with a personal release key. Anyone receiving it may need to allow installation from their browser/file manager. The app loads the hosted StudySpark AI website, so it needs internet access.

If you publish the repository publicly, its source code will be visible. Use a private repository if you want to keep it private.
