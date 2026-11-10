# Convoy Phone

Minimal standalone Android phone (dialer) app in plain Java, with no external runtime
dependencies. It replaces the stock dialer: place and answer calls, manage contacts,
browse recents, block numbers, and record calls where the device allows it.

## Features

- **Dial pad** and in-call screen (answer, hang up, audio controls)
- **Contacts** list with search, contact details, add to contacts, favorites
- **Recents** (call history) with date filter; export / import call history
- **Call blocking**: block a number, block hidden numbers, block numbers not in contacts
- **Call recording** with a selectable recording source and recordings folder, plus a
  recordings list with playback
- **Settings**: dark mode, call recording on/off, recording source, recordings folder,
  default-dialer status

Call recording is best-effort: whether the other side is audible depends on the device
and Android's restrictions. The built-in compatibility test (**Analyze source
consistency**) helps pick the recording source that works on your phone.

## Build

Requirements: JDK 17 and the Android SDK with platform 34 and build-tools 34
(`sdkmanager "platforms;android-34" "build-tools;34.0.0"`). Android Studio is not needed;
the Gradle 8.2 wrapper is included.

```bash
git clone https://github.com/nano-rex/min-phone.git
cd min-phone
export ANDROID_HOME=$HOME/Android/Sdk      # path to your Android SDK
./gradlew :app:assembleDebug
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

## Example

1. Open **Convoy Phone** and grant the phone, contacts, call-log and microphone permissions.
2. **Settings → Set as default dialer** — Android only lets the default dialer place and
   manage calls, so this is required.
3. Dial a number on the pad and tap **Call**; the call appears in **Recents**.
4. To record calls: **Settings → Call recording** on, choose a **Recording source**
   and a recordings folder (**Choose Folder**). Recordings show up in the recordings
   list for playback.
5. To cut spam: **Settings → Block calls from numbers not in contacts**, or long-press a
   number in Recents → **Block number**.

## License

GPL-3.0, see `LICENSE`.
