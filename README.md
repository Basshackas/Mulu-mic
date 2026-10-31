# Direct Bluetooth Mic — Android starter project

An Android app prototype that captures the phone microphone and plays it through the phone's selected media output. When the phone is connected to the RDS mixer's Bluetooth **music/audio input**, Android may route the app's media output to that mixer.

## Included
- `android/`: Kotlin Android Studio project source.
- `phone-browser-prototype.html`: experimental one-file browser prototype to try directly on Android.
- This project is source code, **not a prebuilt APK**.

## Important reality check
This cannot be fully built into an installable APK in this environment because Android SDK/build tools are not available here. The source project is provided, but an APK still needs an Android build environment (Android Studio or another Android SDK/Gradle setup).

The browser prototype may work when opened in Android Chrome, but local-file microphone permissions vary by browser/version. If Chrome refuses microphone access to the local file, this prototype needs to be hosted over HTTPS; it is not a guaranteed installable app.

## Use the Android app source
1. Open the `android` folder in Android Studio.
2. Let Gradle sync.
3. Connect your Android phone with USB debugging enabled, or build an APK.
4. Install and open `Direct Bluetooth Mic`.
5. Pair/connect the phone to the mixer as you normally do for Bluetooth music playback.
6. Start at low volume and test with the speakers muted first, then raise the volume carefully.

## How the audio route works
The app uses Android `AudioRecord` to capture microphone audio and `AudioTrack` with `STREAM_MUSIC` to play it. Android controls the media output route; the app does not force a specific Bluetooth device. If the mixer is the active Bluetooth media output, Android may route the voice there.

## Known limitations
- Bluetooth A2DP is intended for media, not live microphone monitoring. Buffering may create a noticeable delay.
- This prototype does not guarantee professional low-latency live PA performance.
- Acoustic echo cancellation is attempted only if Android reports that the effect is available. It may not cancel sound coming back from Bluetooth speakers.
- If the phone mic hears the speakers, move the phone away from the speakers or use a suitable external microphone.
- Keep the speaker volume low during first tests. If loud squealing/feedback occurs, stop the app and lower the mixer volume.
- The app does not stream audio over Wi-Fi and does not need a computer or network receiver.

## Test checklist
- Connect phone to the mixer's Bluetooth audio.
- Start with mixer channel/master/speakers muted.
- Start microphone stream.
- Raise mixer level slowly.
- Speak from a distance away from speakers.
- If you hear a delayed repeat, mute speakers and move phone away to determine whether the microphone is recapturing speaker sound.
