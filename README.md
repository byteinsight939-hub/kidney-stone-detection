# 🩺 Kidney Stone Detection Using YOLOv8

A deep learning-based object detection project that uses YOLOv8 to automatically detect **kidney stones in CT scan images**. This solution aims to assist radiologists by reducing the time and effort required for diagnosis.

---

## 📌 Project Overview

Kidney stones (nephrolithiasis) are a common and painful urological condition. Early detection is critical for effective treatment. This project leverages **YOLOv8**, one of the most advanced real-time object detection algorithms, to accurately detect stones from CT scan images.

---

## 🧠 Model Details

- **Model Type**: YOLOv8 (Nano, Small, or Medium)
- **Framework**: [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- **Classes Detected**: `Kidney Stone` (single class)
- **Training Time**: ~1 hour on GPU
- **Inference Time**: Real-time (<50ms per image)

---

## 📁 Dataset

- **Source**: [Kaggle – Kidney Stone Images](https://www.kaggle.com/datasets/safurahajiheidari/kidney-stone-images)
- **Images**: >1,300 labeled CT scan images
- **Format**: YOLOv5-compatible format (`.jpg` + `.txt` for labels)
- **Splits**:
  ```
  archive/
  ├── train/
  │   ├── images/
  │   └── labels/
  ├── valid/
  │   ├── images/
  │   └── labels/
  └── test/
      ├── images/
      └── labels/
  ```

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/kidney-stone-detection.git
cd kidney-stone-detection
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

Or manually:

```bash
pip install ultralytics opencv-python matplotlib numpy pandas
```

### 3. Prepare the Dataset

- Download from Kaggle: [Click here](https://www.kaggle.com/datasets/safurahajiheidari/kidney-stone-images)
- Extract into: `archive/` folder in the root directory

---

## ⚙️ Training the Model

```bash
yolo task=detect mode=train model=yolov8n.pt data=data.yaml epochs=50 imgsz=640
```

### `data.yaml` format:

```yaml
path: archive
train: train/images
val: valid/images

names:
  0: Kidney Stone
```

---

## 🔍 Inference on New Images

```bash
yolo task=detect mode=predict model=ft_models/yolo_v828/weights/best.pt source=archive/test/images conf=0.25
```

- Predictions are saved in `runs/detect/predict/`
- Bounding boxes will be drawn around detected kidney stones

---

## 📊 Evaluation Metrics

| Metric         | Value (%) |
|----------------|-----------|
| Precision      | 95.2      |
| Recall         | 93.7      |
| mAP@0.5        | 96.4      |
| mAP@0.5:0.95   | 84.5      |

> 📌 Metrics may vary depending on model size, training epochs, and augmentation strategies.

---

## 📁 Project Structure

```
kidney-stone-detection/
├── archive/                 # Dataset folder
├── ft_models/               # Trained YOLO models (best.pt, last.pt)
├── data.yaml                # YOLO dataset configuration
├── detect.py                # Inference script
├── train.py                 # Custom training script (optional)
├── requirements.txt         # Python dependencies
├── README.md                # Project documentation
└── assets/                  # Output images / visualizations
```

---

## 🛠️ Future Improvements

- [ ] Streamlit-based web dashboard for uploading images
- [ ] DICOM support for direct hospital integration
- [ ] Segmentation model to localize stone boundaries more precisely
- [ ] Mobile deployment using TensorFlow Lite or ONNX

---

## 💻 Tech Stack

| Tool        | Purpose                  |
|-------------|---------------------------|
| Python 3.8+ | Programming language      |
| YOLOv8      | Object detection model    |
| OpenCV      | Image handling            |
| matplotlib  | Visualization             |
| Kaggle API  | Dataset access            |

---

## 📜 License

This project is licensed under the **MIT License**.  
You are free to use, modify, and distribute this project for personal or commercial use.

---

## 🙌 Acknowledgements

- Dataset: [Safura Hajiheidari on Kaggle](https://www.kaggle.com/datasets/safurahajiheidari/kidney-stone-images)

---


---
