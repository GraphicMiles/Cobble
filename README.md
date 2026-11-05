# Cobble

A lightweight Android screen recorder. MediaProjection captures the display,
MediaCodec encodes H.264 and MediaMuxer writes an MP4, with the file saved to
MediaStore or a folder you choose.

## Why it exists

Screen recorders on Android tend to be large, ad-supported, or fragile at the
edges: recording stops when the app is backgrounded, the file is unplayable, or
the permission prompt is handled in a way that breaks on the next release. Cobble
is a small native app that does one job and survives being left running.

This build is native-first. The earlier Flutter packaging made the APK much
larger for a utility that draws almost nothing, so the current version keeps the
recording features and drops the framework.

## What you can do

- **Record the screen** to MP4, H.264, from a minimal native interface.
- **Keep recording in the background**, through a foreground service.
- **Start and stop from the Quick Settings tile**, which works from anywhere.
- **Save to `Movies/Screen Recorder/`** by default, or pick a folder through the
  Storage Access Framework.
- **Stop from the notification** while a recording is running.
- **Triple-tap to start** while the Cobble screen is open.

## What is not here

- No editing, trimming, GIF export or upload.
- No audio mixing controls beyond what the platform capture provides.
- A system-wide triple-tap detector is not available to ordinary apps without
  overlays or elevated privileges, so the global control is the Quick Settings
  tile. That is a platform limit, not a missing feature.
- Android only, and the capture depends on the device's encoder support.

## Build

```bash
cd android
./gradlew :app:assembleRelease
```

`.github/workflows/android-apk.yml` builds a single installable release APK and
uploads it as `cobble-release-apk`.

## How it is built

```
android/        the native app: UI, recording engine, service, tile
lib/            shared Dart-facing pieces kept from the Flutter build
pubspec.yaml    the remaining Flutter shell
```

## Licence

No licence file is included in this repository.
