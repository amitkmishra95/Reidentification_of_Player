# Reidentification_of_Player
# 🔁 Re-Identification in Single Camera Feed using YOLOv11

## 📌 Project Overview
This project performs **object re-identification** (re-ID) in a **single-camera video stream** using a custom-trained **YOLOv11 model**. The system assigns unique, persistent IDs to players and optionally a ball, tracking them across frames—even when they disappear temporarily and re-enter the scene.

---

## 🎯 Objectives
- Detect and track objects (person and ball) using a custom YOLOv11 model.
- Maintain consistent identity (ID) across video frames.
- Visualize tracking output in annotated video.
- Export tracking details as CSV with object ID, class, bounding boxes, and frame number.
- Analyze appearance time of each tracked entity.




---

## ⚙️ Features & Workflow

### 1. 📥 Model and Video Input
- Upload a trained YOLOv11 model (`best.pt`)
- Upload a short test video (`.mp4`)

### 2. 🤖 YOLO Model Inference
- Load YOLO model using `ultralytics`
- Detect objects (person and optionally ball)

### 3. 📍 Memory-Based Tracker
- Assigns unique IDs to detected objects
- Maintains identities using **centroid tracking**
- Handles temporary disappearance (configurable with `max_missing`)

### 4. 🎥 Video Output with Annotations
- Draws bounding boxes with labels (`PLAYER 0`, `PLAYER 1`, etc.)
- Saves annotated video (`reid_output.mp4`)

### 5. 📊 CSV Output + Stats
- Frame-by-frame logging of:
  - Object ID
  - Class (player or ball)
  - Bounding box coordinates
  - Frame number
- Appearance time statistics (in frames & seconds)

---

## 🚀 How to Run (Colab Recommended)

1. Open the Colab notebook or script.
2. Upload:
   - `best.pt` (YOLOv11 model)
   - A test video file (e.g., `15sec_input_720p.mp4`)
3. Run the main function:
   ```python
   reidentify_and_save_all(model, video_path, "reid_output.mp4", "tracking_data.csv")
4.  View the video and download results directly from the notebook.


   | Tool/Library     | Purpose                    |
| ---------------- | -------------------------- |
| Python           | Core programming language  |
| Ultralytics YOLO | Object detection model     |
| OpenCV           | Video processing & drawing |
| NumPy            | Centroid calculations      |
| Pandas           | CSV generation             |
| Google Colab     | Notebook environment       |

 Sample Output
| Frame | ID | Class  | x1  | y1  | x2  | y2  |
| ----- | -- | ------ | --- | --- | --- | --- |
| 10    | 0  | player | 45  | 60  | 120 | 190 |
| 11    | 0  | player | 48  | 62  | 122 | 195 |
| 12    | 1  | ball   | 310 | 400 | 340 | 430 |

🧩 Limitations

Limited to single-camera re-identification.

Relies on centroid tracking (no appearance-based identity).

May misidentify in heavy occlusion or dense scenes

💡 Future Work
Use deep re-ID features (Siamese Network or DeepSort).

Extend to multi-camera re-identification.

Build real-time dashboard with Streamlit or Flask.

📃 License
his project is for academic and research purposes only. Please cite appropriately if used.

🙌 Acknowledgments
Ultralytics YOLO

OpenCV, NumPy, and Pandas community


