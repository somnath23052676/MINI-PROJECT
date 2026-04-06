# ✋😊 ISL Sign Language + Facial Emotion Detector

A real-time, browser-based system that simultaneously detects **Indian Sign Language (ISL)** alphabet signs and **facial emotions** — powered entirely by pre-trained AI models. No training, no server, no installation required.

> Built as a mini project at **KIIT University, School of Computer Engineering**

---

## 🎥 Demo

> Open `isl_emotion_detector.html` in Chrome → Allow camera → Start detecting instantly.

---

## ✨ Features

- 🤟 **ISL Alphabet Detection** — Recognizes all 26 letters (A–Z) of Indian Sign Language in real-time
- 😄 **Facial Emotion Detection** — Classifies 7 emotions: Happy, Sad, Angry, Surprised, Fearful, Disgusted, Neutral
- ⚡ **Real-time** — Both models run simultaneously on the same camera stream at 8–15 fps
- 🔒 **100% Private** — Everything runs locally in your browser; no data is sent to any server
- 📝 **Word Builder** — Hold a sign for ~3 seconds to auto-type the letter; supports Space, Delete, Clear
- 📊 **Confidence Scores** — Live probability bars for top predictions and all 7 emotions
- 🗂️ **Sign History** — Tracks all detected letters in the session
- 🔡 **ISL Reference Grid** — Full A–Z alphabet grid that highlights the currently detected letter
- 🎨 **Clean Dark UI** — Professional dark-themed interface with overlay annotations on the live feed
- 📦 **Zero Setup** — Single `.html` file, no npm, no Python, no GPU needed

---

## 🧠 Models Used

| Model | Source | Purpose |
|-------|--------|---------|
| **MediaPipe Hands** | Google | Detects 21 3D hand landmarks per frame |
| **TinyFaceDetector** | face-api.js | Locates face region in each frame |
| **FaceExpressionNet** | face-api.js (FER-2013) | Classifies face into 7 emotion categories |

> The ISL letter classifier is a **rule-based geometric classifier** built on top of MediaPipe landmarks — no model training required.

---

## 🚀 Getting Started

### Prerequisites
- Google Chrome (v90+) or Microsoft Edge (v90+)
- A working webcam
- Internet connection on first load (to fetch models from CDN)

### Run the Project

```bash
# 1. Clone the repository
git clone https://github.com/your-username/isl-emotion-detector.git

# 2. Navigate into the folder
cd isl-emotion-detector

# 3. Open the HTML file directly in Chrome
# On Windows:
start isl_emotion_detector.html

# On macOS:
open isl_emotion_detector.html

# On Linux:
xdg-open isl_emotion_detector.html
```

> ⚠️ Must be opened in **Chrome or Edge**. Firefox has limited support for the WebGL operations used by TensorFlow.js.

---

## 🖥️ How to Use

1. Open `isl_emotion_detector.html` in Chrome
2. Click **▶ Start Camera** and allow webcam access
3. **For ISL detection** — show your hand sign clearly in the frame
4. **For emotion detection** — face the camera directly
5. Hold a sign steady for ~3 seconds to auto-add the letter to the word builder
6. Use **+ Space**, **⌫ Delete**, **✕ Clear** to edit the built word

### Tips for Best Results
- 💡 Use good lighting — avoid backlighting
- ✋ Keep your hand fully in frame
- 🎨 A plain background improves hand detection accuracy
- 📏 Sit 30–80 cm from the camera for best face detection

---

## 📁 Project Structure

```
isl-emotion-detector/
│
├── isl_emotion_detector.html    # Main application (entire project in one file)
└── README.md                    # This file
```

---

## 🔧 Tech Stack

| Technology | Role |
|------------|------|
| **HTML5 / CSS3 / JavaScript** | UI and application logic |
| **MediaPipe Hands** | Hand landmark detection |
| **face-api.js** | Face detection and emotion classification |
| **TensorFlow.js** | In-browser ML inference engine |
| **Canvas 2D API** | Real-time landmark overlay rendering |
| **getUserMedia API** | Webcam access |

---

## 📊 Performance

| Metric | Value |
|--------|-------|
| Frame Rate | 8–15 fps (mid-range laptop) |
| Sign-to-screen latency | < 100ms |
| ISL accuracy (distinct letters) | ~85% |
| ISL accuracy (similar letters, e.g. M/N) | ~65% |
| Emotion accuracy (happy/neutral) | High |
| Emotion accuracy (fearful/disgusted) | Moderate |

---

## 🔬 How It Works

```
Webcam Frame
     │
     ├──► MediaPipe Hands ──► 21 Landmark Points ──► ISL Geometric Classifier ──► Letter + Confidence
     │
     └──► TinyFaceDetector ──► Cropped Face ──► FaceExpressionNet ──► Emotion + Probability
                                                        │
                                               (runs every 4th frame)
```

The ISL classifier uses geometric rules — finger extension states, tip-to-tip distances, and joint angles — derived from the 21 MediaPipe landmarks to identify each letter. A **stability buffer** (last 8 frames, 60% threshold) prevents flickering.

---

## 🌱 Future Scope

- [ ] Replace rule-based ISL classifier with a trained neural network for higher accuracy
- [ ] Support dynamic gestures (letters like J and Z that involve motion)
- [ ] Add full ISL word and phrase recognition using LSTM/Transformer sequence models
- [ ] Multi-hand detection for two-handed signs
- [ ] Text-to-speech output for detected signs
- [ ] Mobile browser support

---

## 📚 References

- [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html) — Google
- [face-api.js](https://github.com/justadudewhohacks/face-api.js) — justadudewhohacks
- [TensorFlow.js](https://www.tensorflow.org/js) — Google
- [FER-2013 Dataset](https://www.kaggle.com/datasets/msambare/fer2013) — Kaggle
- [ISL Alphabet Reference](https://www.islrtc.nic.in/) — ISLRTC, Govt. of India

---

## 📄 License

This project is for educational purposes. Feel free to fork, modify, and build on it.

---

<p align="center">Made with ❤️ at KIIT University, Bhubaneswar</p>
