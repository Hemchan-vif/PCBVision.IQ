# PCBVision.IQ

## PCB Defect Detection and Quality Inspection Platform using Machine Learning

PCBVision.IQ is a machine learning-based PCB inspection platform developed for automated defect detection and quality assessment in Printed Circuit Board (PCB) manufacturing environments. The project leverages modern object detection models to identify manufacturing defects with high precision while providing a structured framework for dataset preparation, model training, validation, benchmarking, and performance evaluation.

The platform benchmarks multiple YOLO architectures, including YOLOv8, YOLOv10, and YOLOv11, to evaluate their effectiveness for industrial PCB inspection tasks and to understand the trade-offs between detection accuracy, robustness, and inference performance.

---

## Overview

The rapid advancement of electronics, communication systems, embedded devices, consumer technology, and computing infrastructure has significantly increased the demand for reliable Printed Circuit Boards (PCBs). As production volumes continue to grow, ensuring manufacturing quality has become increasingly important.

PCB defects such as open circuits, short circuits, pin-holes, mousebites, spurious copper, and spurs can affect circuit functionality, reliability, and product lifespan. Traditional manual inspection processes are often labor-intensive and difficult to scale for high-volume manufacturing.

PCBVision.IQ provides a machine learning-driven inspection framework capable of automatically detecting PCB defects and supporting quality assurance processes through data-driven inspection workflows.

---

## Project Objectives

* Develop an automated PCB defect detection framework.
* Evaluate the effectiveness of modern object detection models for industrial inspection.
* Compare YOLOv8, YOLOv10, and YOLOv11 performance on PCB defect detection tasks.
* Analyze model accuracy, localization capability, and inference efficiency.
* Provide a reusable training and evaluation pipeline for manufacturing inspection applications.

---

## Key Features

* Automated PCB defect detection
* Multi-model benchmarking framework
* YOLOv8, YOLOv10, and YOLOv11 evaluation
* End-to-end training and validation workflows
* Dataset preprocessing and annotation handling
* High-resolution defect localization
* Performance analysis using standard detection metrics
* Modular architecture for future quality inspection enhancements

---

## Supported Defect Classes

PCBVision.IQ supports detection of six commonly occurring PCB manufacturing defects.

| Class ID | Defect Type   |
| -------- | ------------- |
| 0        | Copper        |
| 1        | Mousebite     |
| 2        | Open Circuit  |
| 3        | Pin-hole      |
| 4        | Short Circuit |
| 5        | Spur          |

These defects represent critical failure points that can impact electrical connectivity and manufacturing quality.

---

## Dataset

PCBVision.IQ utilizes a PCB defect dataset derived from the publicly available DeepPCB benchmark dataset.

### Dataset Characteristics

* 6 defect categories
* High-resolution PCB imagery
* YOLO-compatible annotations
* Multiple defect instances per image
* Training, validation, and testing splits
* Augmented samples for improved model generalization

### Dataset Preparation

The original dataset was processed and prepared for object detection training by:

* Converting annotations into YOLO format
* Normalizing bounding-box coordinates
* Organizing training, validation, and testing splits
* Applying image augmentation techniques
* Preparing deployment-ready dataset structures

### Dataset Structure

```text
dataset/
│
├── train/
│   ├── images/
│   └── labels/
│
├── valid/
│   ├── images/
│   └── labels/
│
├── test/
│   ├── images/
│   └── labels/
│
└── data.yaml
```

---

## Methodology

The project follows a supervised machine learning workflow consisting of:

1. Dataset preparation and annotation processing
2. Model training
3. Validation and performance monitoring
4. Inference and prediction analysis
5. Comparative benchmarking
6. Performance evaluation

The primary focus is to evaluate object detection models for identifying PCB defects under realistic manufacturing conditions.

---

## Model Architectures Evaluated

### YOLOv8

YOLOv8 serves as a strong baseline model and provides reliable object detection performance across multiple defect categories.

### YOLOv10

YOLOv10 introduces architectural optimizations that improve inference efficiency and throughput, making it suitable for real-time inspection applications.

### YOLOv11

YOLOv11 incorporates enhanced feature extraction and localization mechanisms, improving detection performance on small and challenging defect instances while maintaining practical deployment efficiency.

---

## Training Configuration

| Parameter   | Value            |
| ----------- | ---------------- |
| Image Size  | 640 × 640        |
| Epochs      | 100 – 150        |
| Batch Size  | 16 / 32          |
| Framework   | Ultralytics YOLO |
| Environment | Google Colab     |
| GPU         | NVIDIA Tesla T4  |

---

## Evaluation Metrics

The models are evaluated using standard object detection metrics:

### Precision

Measures the proportion of correctly detected defects among all predicted defects.

### Recall

Measures the ability of the model to identify all actual defects present in an image.

### mAP@0.5

Evaluates detection accuracy at an Intersection-over-Union threshold of 0.5.

### mAP@0.5:0.95

Provides a comprehensive evaluation across multiple IoU thresholds.

### Inference Speed

Measures processing performance and suitability for practical inspection workflows.

---

## Experimental Findings

The evaluation demonstrates that all three YOLO variants provide strong defect detection performance.

Key observations include:

* YOLOv11 achieves the strongest overall localization performance.
* YOLOv10 provides the highest inference speed.
* YOLOv8 offers competitive detection performance with a mature deployment ecosystem.
* YOLOv11 demonstrates improved robustness when detecting small and complex defect patterns.

These findings indicate that YOLOv11 provides a strong balance between accuracy and efficiency for PCB inspection applications.


---

## Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/PCBVision.IQ.git
```

### Install Dependencies

```bash
pip install ultralytics
```

---

## Training

### YOLOv11

```bash
yolo task=detect mode=train model=yolo11n.pt data=dataset/data.yaml epochs=150 batch=32 imgsz=640
```

### YOLOv10

```bash
yolo task=detect mode=train model=yolov10n.pt data=dataset/data.yaml epochs=100 batch=32 imgsz=640
```

### YOLOv8

```bash
yolo task=detect mode=train model=yolov8m.pt data=dataset/data.yaml epochs=100 batch=32 imgsz=640
```

---

## Validation

```bash
yolo task=detect mode=val model=runs/detect/train/weights/best.pt data=dataset/data.yaml
```

---

## Prediction

```bash
yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=dataset/test/images
```

---

## Potential Applications

* PCB Manufacturing Inspection
* Automated Optical Inspection (AOI)
* Electronics Production Quality Control
* Manufacturing Process Monitoring
* Industrial Computer Vision Research
* Smart Manufacturing Systems

---

## Future Scope

* Defect severity estimation
* PCB quality scoring
* Production batch analytics
* Statistical defect reporting
* Interactive inspection dashboard
* Edge deployment optimization
* Manufacturing intelligence modules

---

## Acknowledgements

This project utilizes publicly available PCB defect datasets and modern object detection frameworks for educational, research, and industrial inspection experimentation. The work focuses on advancing machine learning applications in manufacturing quality inspection and automated defect detection.
