# Android Studio + Chaquopy + Wav2Lip Demo

## Features
- Select image and audio files with Android file picker
- Progress bar updates during video generation (Python→Java)
- Output .mp4 video saved to app storage
- Playback result in VideoView

## Steps
1. Download Wav2Lip repo and model weights (`wav2lip_gan.pth`)
2. Copy all Python files (especially `inference.py` and dependencies) to `app/src/main/python/`
3. Place model file in `/sdcard/` or app storage
4. Build and run the app; select image and audio, then tap "Generate Video"

## Notes
- Progress updates are simulated; for real progress, add update calls inside Wav2Lip’s inference code
- Large models may have performance/storage issues on some devices

## References
- [Wav2Lip GitHub](https://github.com/Rudrabha/Wav2Lip)
- [Chaquopy Docs](https://chaquo.com/chaquopy/)