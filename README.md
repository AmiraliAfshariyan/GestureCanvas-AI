# 🖐️ AI Gesture Controller & Virtual Canvas via MediaPipe

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0.10%2B-raygeen?logo=google&logoColor=white)](https://developers.google.com/mediapipe)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?logo=opencv&logoColor=white)](https://opencv.org)
[![PyAutoGUI](https://img.shields.io/badge/PyAutoGUI-Automation-orange)](https://pyautogui.readthedocs.io)

An advanced, production-grade Human-Computer Interaction (HCI) application leveraging Google MediaPipe's latest Python Tasks API. This system orchestrates simultaneous multi-model tracking (Face Mesh & Hand Landmarks) to deliver real-time virtual air-drawing, gesture-based OS-level mouse automation, and a dynamic heads-up display (HUD) interface directly over a live webcam feed.

---

## ✨ Key Features

- **Dual-Model Pipeline:** Concurrently processes **Hand Landmarker** (21 3D points) and **Face Landmarker** (468+ points) mesh frameworks without processing bottlenecks.
- **Virtual Air-Drawing Canvas:** Tracks the spatial path of the index finger to draw continuous lines onto an isolated digital canvas matrix.
- **OS Mouse Automation:** Smoothly binds hand/face key coordinates to physical screen coordinate movements via `PyAutoGUI`.
- **Automated Model Asset Provisioning:** Features a built-in network fallback script that automatically fetches official Google MediaPipe `.task` models if missing from the local workspace.
- **Interactive HUD & Hotkeys:** Includes an integrated heads-up display showing state configurations with active runtime controls (`C` to clear canvas, `Q` or `ESC` to gracefully exit).

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python
* **AI Core / Machine Learning Toolkit:** `Google MediaPipe (Tasks API)`
* **Computer Vision Processing:** `OpenCV (cv2)`
* **Automation Bridge:** `PyAutoGUI`
* **Mathematical Operations:** `NumPy` & `Math`

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name

2. Install Required Frameworks

Bash
pip install opencv-python numpy pyautogui mediapipe

3. Model Dependencies
The application requires the official pre-trained MediaPipe task definition bundles:
o . hand_landmarker.task
o . face_landmarker.task
Note: You do not need to download these manually. The repository's download_if_missing() routine handles model retrieval on the first execution.

🚀 Architectural WorkflowThe application code inside draw_with_fingures.ipynb is structured into a clean, object-oriented HandGestureController class following this pipeline:

1. Asset Inspection: Checks for local .task binaries; falls back to an external urllib request if files are missing.
2. Context Initialization: Configures MediaPipe runtime environments utilizing RunningMode.IMAGE optimized for high-frequency video stream frames.
3. Frame Processing Loop:
  o . Extracts localized multi-hand and face landmark coordinates.
  o . Computes distance thresholds (e.g., Euclidean distances between finger nodes).
4. Action Dispatcher: - Draws onto a separate canvas mask when drawing gestures match.
  o . Maps primary tracking coordinates to desktop cursor bounds.
5. HUD Compositing: Merges the raw webcam feed, drawing layers, and text overlays into a single visual window.

🎮 Runtime Controls
Key Bind               Action Description
C / c               Instantly clears the digital drawings from the virtual canvas
Q / q               "Stops camera runtime, flushes buffers, and triggers a clean shutdown"
ESC                 Standard immediate escape hook

📝 Roadmap / Next Steps
o . [ ] Add a multi-color palette selectable via eye-gaze or floating HUD buttons.
o . [ ] Implement multi-finger gesture recognition for advanced triggers (e.g., Pinch to Zoom, Multi-touch scrolling).
o . [ ] Integrate a Kalman Filter to damp coordinates and achieve ultra-smooth brush strokes.

Developed by Amirali Afshariyan
