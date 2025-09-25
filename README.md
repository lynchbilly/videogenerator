# Wav2Lip Android APK Tutorial: Kivy + Buildozer & Android Studio + Chaquopy

This repo shows two ways to package a Python-based AI app (e.g., Wav2Lip) as an Android APK:

- **Option 1: Kivy + Buildozer** — Package a Python/Kivy UI as a standalone Android app.
- **Option 2: Android Studio + Chaquopy** — Use native Android UI, call Python code (like Wav2Lip) from Java/Kotlin.

---

## 🟢 Option 1: Kivy + Buildozer

### 1. Prerequisites

- Linux/macOS (Windows: WSL2 recommended)
- Python 3.7–3.10
- [Kivy](https://kivy.org/)
- [Buildozer](https://github.com/kivy/buildozer)
- [Wav2Lip](https://github.com/Rudrabha/Wav2Lip)

### 2. Install Kivy and Wav2Lip

```bash
pip install kivy
git clone https://github.com/Rudrabha/Wav2Lip.git
cd Wav2Lip
pip install -r requirements.txt
```

### 3. Create your Kivy app

See [`main.py`](main.py) for template.

### 4. Build the APK

```bash
pip install buildozer
buildozer init
# Edit buildozer.spec for requirements (see below)
buildozer -v android debug
```
Find your APK in `bin/`.

---

## 🟢 Option 2: Android Studio + Chaquopy

### 1. Prerequisites

- [Android Studio](https://developer.android.com/studio)
- [Chaquopy plugin](https://chaquo.com/chaquopy/)

### 2. Setup

- Create a new Android Studio project.
- Add Chaquopy to your `build.gradle` files ([docs](https://chaquo.com/chaquopy/doc/current/android.html#installation)).
- Place Python files under `src/main/python`.

### 3. Call Python from Java/Kotlin

```java
Python py = Python.getInstance();
PyObject wav2lip = py.getModule("wav2lip_script");
PyObject result = wav2lip.callAttr("generate_video", imagePath, audioPath);
```

---

## 🔗 Resources

- [Wav2Lip](https://github.com/Rudrabha/Wav2Lip)
- [Kivy Documentation](https://kivy.org/doc/stable/)
- [Buildozer](https://github.com/kivy/buildozer)
- [Chaquopy](https://chaquo.com/chaquopy/)

---

## 📁 Suggested Folder Structure

```
videogenerator/
├── main.py             # Kivy app
├── buildozer.spec      # Buildozer config
├── requirements.txt    # Kivy/Wav2Lip deps
├── Wav2Lip/            # Wav2Lip repo code
└── README.md           # This tutorial
```

---

## 🛠 Troubleshooting

- For Buildozer: Use a Linux VM or WSL2 on Windows for best results.
- For Chaquopy: Ensure Python dependencies are Android-compatible.
- For both: Test with simple scripts first, then integrate Wav2Lip.

---

## ✨ Extend This Tutorial

- Add picture upload and audio recording to your Kivy app.
- Integrate Wav2Lip’s inference code for real AI video generation.
- Build a more advanced UI in Android Studio and use Chaquopy for backend AI processing.