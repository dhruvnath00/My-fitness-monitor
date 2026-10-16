# My Fitness Monitor — Android

The same app as the web version (Personal info, Target, Meals, Activity, Health, Progress) plus a
**Settings** tab, on a light sage background (`#D6E6DF`). The app is a native Android shell around a web page
(`app/src/main/assets/www/index.html`), so there is one file to edit for almost every change.

## Get an APK without installing anything (free)

1. Create a free GitHub account and a new empty repository (private is fine).
2. Upload the **contents** of this folder to it. Keep the hidden `.github` folder: it holds the build recipe.
   Easiest way: on the repo page choose *Add file → Upload files* and drag everything in, including `.github`.
   If the browser skips hidden folders, use GitHub Desktop or `git push` instead.
3. Open the **Actions** tab → **Build APK** → **Run workflow** (it also runs on every push to `main`).
4. When it finishes (about 5–8 minutes), open the run and download **MyFitnessMonitor-debug-apk** at the bottom.
   Unzip it to get `app-debug.apk`.
5. Copy the APK to your phone and open it. Android will ask you to allow installs from that source once.

## Build in Android Studio instead

Open this folder in Android Studio (Ladybug or newer) → let Gradle sync → *Build → Build APK(s)*, or press Run
with a phone or emulator connected.

## Turn on the AI features

Meal-photo analysis and the suggestions use Claude through **your own Anthropic API key**.

1. Create a key at <https://console.anthropic.com> (API usage is billed to your Anthropic account).
2. In the app, open **Settings**, paste the key, press **Save**, then **Test key**.

The key is stored only on your phone and sent only to `api.anthropic.com`. Everything else (BMI, BMR, calories,
the target forecast, charts) works offline without a key. Your data stays on the device.

## Notes

- The APK is signed with the debug key, which is fine for installing on your own phone. Publishing on Google Play needs
  a release keystore and a $25 developer account.
- Camera and gallery open through Android's own camera and photo picker, so no camera permission is requested.
- Fitness apps and wearables cannot be logged into from a web page. Choose the source in the Activity tab and
  import its CSV or JSON export, or enter the numbers by hand.
- Change the background in two places: `--bg` in `index.html`, and `app_bg` in `app/src/main/res/values/colors.xml`.
