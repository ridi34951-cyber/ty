# SonicShield 0.2.0 — Powered by Ridi

Android Studio project with a real-time Bluetooth microphone monitoring / software audio-processing prototype and GitHub Actions APK build workflow.

## Upload to GitHub

Extract this ZIP and upload **all contents directly to the repository root** (do not upload an extra enclosing folder). Keep the `.github` folder.

## Build APK

1. Open the repository's **Actions** tab.
2. Select **SonicShield Android Build** and run **Run workflow**, or push to `main` / `master`.
3. Download `SonicShield-debug-apk` from the successful workflow's Artifacts section.

## What 0.2.0 does

- Checks Bluetooth audio input and output separately.
- Attempts to route both microphone input and audio output through a Bluetooth headset/TWS communication profile.
- `Transparency` monitors the TWS microphone and plays the captured audio back to the TWS.
- `Software Reduce` enables Android's available `NoiseSuppressor` effect on that microphone stream and plays the processed signal back at conservative gain. If the Android device does not expose the effect or the TWS microphone route, the mode reports an error rather than pretending it is working.
- `Off` stops the audio engine.
- Mode selection has a persistent visual indicator; the screen uses safe system insets and a scrollable layout so controls do not sit underneath Android navigation buttons.

## Important acoustic limitation

This is **not true Active Noise Cancellation (ANC)**. It does not generate phase-inverted anti-noise. A phone app cannot reliably cancel sound that travels directly through the earbud shell/ear tip because Bluetooth microphone-to-speaker latency is too high for precise acoustic cancellation. `Software Reduce` is filtered microphone monitoring; it can only affect the sound captured by the microphone and played back by the app. It cannot guarantee that outside noise becomes quieter inside the ear. The available Android NoiseSuppressor effect is also device-dependent.

Some TWS models expose only A2DP playback and do not expose a Bluetooth headset microphone route. In that case the app will stop and show that the TWS mic is unavailable; it will not silently switch to the phone microphone.

## Safety

Start at a low listening volume. Stop the mode if you hear feedback, echo, or uncomfortable sound. Do not use the app as hearing protection or while you need to hear traffic and other safety signals.
