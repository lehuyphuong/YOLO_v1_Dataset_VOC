# YOLO_v1_Dataset_VOC

## 📌 Overview
This project implements **YOLOv1** (You Only Look Once - version 1) for real-time object detection using the Pascal VOC 2012 dataset.
The primary goal is to predict both bounding boxes and class labels from natural images in a single, unified pipeline.

## 📚 Background
**YOLOv1** introduced a revolutionary approach to object detection by framing it as a single regression problem, straight from image pixels to bounding box coordinates and class probabilities.
Its unique contributions include:

- Unified Architecture: Combines localization and classification into one network.
- Global Context Reasoning: Looks at the full image to predict boxes and labels, reducing background errors.
- Real-Time Speed: Achieves detection speeds far beyond traditional region proposal methods like R-CNN.

This makes YOLOv1 a foundational model in the evolution of object detection, inspiring a long family of YOLO variants.

## 🧾 Dataset: Pascal VOC 2012
**Description**

The **PASCAL VOC dataset** is a gold-standard benchmark for object detection, segmentation, and classification tasks. It provides detailed annotations for 20 object classes.

- Total classes: 20 (e.g., person, dog, bicycle, car, dining table)
- Annotations:
    - Bounding boxes around each object
    - Object class labels

**Preprocessing for YOLOv1**

Convert bounding boxes from VOC XML to YOLO format: **[class_id, center_x, center_y, width, height]**

Resize all images to 448×448 pixels to fit YOLO input dimensions.

Transform labels into a 7×7 grid format.

## 📐 Task Adaptation

For YOLOv1 training on Pascal VOC:
- The input image is divided into a 7×7 grid.
- Each grid cell predicts:
    - 2 bounding boxes (each box: center_x, center_y, width, height, objectness score)
    - 20 class probabilities.
- Training focuses on mean squared error (MSE) loss balancing:
    - Localization (box coordinates)
    - Confidence scores
    - Classification outputs

>Special emphasis:
- λ_coord = 5 to prioritize accurate bounding box regression.
- λ_noobj = 0.5 to downweight errors where no object exists.

## 🏗️ Project Structure
```
├── data/
├── YOLO_v1_dataset_VOC.ipynb
```

## 🧪 Training the Model
You can configure parameters like:
- Epochs (default: 30)
- Learning rate (default: 2e-5)
- Batch size (default: 16)

## 🖼️ Sample Visualization

## 📌 References
Paper: [You Only Look Once: Unified, Real-Time Object Detection](https://arxiv.org/abs/1506.02640)

Dataset: [Pascal VOC 2012](http://host.robots.ox.ac.uk/pascal/VOC/)