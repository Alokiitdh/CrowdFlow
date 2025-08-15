# CrowdFlow — Real-time People Detection & Counting

CrowdFlow is a computer vision project for detecting, tracking, and counting people moving in and out of a defined region in a video feed.
It uses **YOLOv8** for object detection, **SORT** for tracking, and **OpenCV / cvzone** for image processing and visualizations.

---

## 🚀 Features

* **Real-time video processing** from camera or video file.
* **YOLOv8-based object detection** for accurate person recognition.
* **SORT tracker** for assigning unique IDs to tracked individuals.
* **Region masking** to limit detection to specific areas.
* **Directional counting** (e.g., people moving up vs. down).
* **Graphical overlays** for counts, bounding boxes, and tracker IDs.

---

## ⚙️ Requirements

Install dependencies:

```bash
pip install opencv-python cvzone ultralytics numpy
```

Ensure **`sort.py`** is present in the project root — this is required for object tracking.

---

## 📥 Model Weights

Download YOLOv8 weights:

```bash
# From ultralytics repo or directly via:
yolo download yolov8n.pt
```

Place them in:

```
YOLO-Weights/yolov8n.pt
```

---

## ▶️ How to Run

```bash
python crowdflow.py
```

You can change the video source:

```python
# Use webcam
cap = cv2.VideoCapture(0) # For this you have to modify the mask according to the need

# Use video file
cap = cv2.VideoCapture("Dataset/people.mp4")
```

---

## 📌 How It Works

1. **Load YOLOv8 Model** — Detects all objects, filters for `person` class.
2. **Apply Region Mask** — Ignores irrelevant areas.
3. **Track Objects** — SORT assigns unique IDs to each detected person.
4. **Count Movement** — Lines define "up" and "down" zones; crossing increments counters.
5. **Display Results** — Bounding boxes, IDs, and count overlays are drawn on the frame.

---

## 📄 License

This project is open-source under the MIT License.