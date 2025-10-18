# ♻️ Smart and Sustainable Waste Sorting System with YOLOv11

### Author: Mhlengeni Miya  
**Supervisor:** Prof. Turgay Celik  
**Institution:** University of the Witwatersrand  
**Project Year:** 2025  

---

## 📘 Project Overview

This project presents the design and development of a **smart, sustainable, and automated waste-sorting system** that integrates **deep learning**, **robotics**, and **edge computing** to classify and sort beverage containers in real time.  
The system leverages a **YOLOv11 object detection model**, optimized with **NVIDIA TensorRT**, and coordinated with a **Cobotta PRO 1300 robotic arm** and **PLC-based motion control** for high-throughput municipal recycling operations.

The implementation supports **active learning** and **federated learning**, enabling decentralized and privacy-preserving model improvements across multiple recycling facilities.

---

## 🎯 Objectives

- Automatically and accurately classify **glass**, **metal**, and **plastic** waste items.  
- Achieve real-time performance for **industrial-scale recycling**.  
- Enable continuous model improvement using **active learning**.  
- Support **federated learning** to share model updates securely without exposing raw data.  
- Promote a **circular economy** and contribute to **sustainable waste management**.

---

## 🧠 Deep Learning Models

### 1. **Convolutional Neural Network (CNN) Classifiers**
- Trained for baseline waste classification on custom datasets.  
- Used for benchmarking against YOLOv11.  

### 2. **YOLOv11 Object Detection**
- **Framework:** Ultralytics YOLOv11  
- **Training Data:** 8,147 waste images (3 main classes: Glass, Metal, Plastic)  
- **Annotation:** Roboflow (bounding-box labels in YOLO format)  
- **Input Resolution:** 640×640 pixels  
- **Optimization:** TensorRT (FP16 and INT8 quantization)  
- **Training Environment:**
  - CPU: AMD Ryzen 5 5600H  
  - GPU: NVIDIA GeForce RTX 3050 (6 GB VRAM)  
  - Epochs: 100  
  - Batch Size: 8  

#### 🧩 YOLOv11 Performance
| Metric | Value |
|--------|--------|
| mAP@50–95 | **0.958** |
| Precision | **0.994** |
| Inference Time | **10.84 ms/image** |
| F1 Score | **0.9936 (epoch 83)** |

---

## ⚙️ System Architecture

The system architecture integrates four main subsystems:

1. **Perception Layer**  
   - Intel RealSense D555 PoE RGB-D camera  
   - Synchronized with conveyor encoder via PLC position-compare trigger  
   - Depth data used for 3D coordinate extraction  

2. **Edge Compute Node (NVIDIA Jetson AGX Orin)**  
   - Runs YOLOv11 TensorRT inference  
   - Executes on-device active learning  
   - Communicates securely with federated learning server (AWS, gRPC/TLS)

3. **Control Layer (PLC + Robot Controller)**  
   - PLC: Conveyor synchronization, encoder tracking, safety control  
   - CRC9 Robot Controller: Executes trajectory interpolation and EtherCAT-based motion control  

4. **Robotic Manipulation**  
   - Cobotta PRO 1300 collaborative robot  
   - Multi-modal two-finger gripper  
   - Throughput: **220 picks/minute**

---

## 🔁 Learning Workflows

### 🧩 Active Learning
- Frames with low detection confidence (<60%) are flagged.  
- Stored locally for manual labeling and on-device retraining.  
- Ensures adaptation to new object types and lighting conditions.

### 🌐 Federated Learning
- Local nodes train independently on their site-specific data.  
- Model updates (weight deltas) are securely sent to a **federated server**.  
- Server aggregates updates using **FedAvg** and redistributes global weights.  
- Ensures **data privacy** and **cross-facility knowledge sharing**.

---

## 🔋 Performance and Efficiency

| Parameter | Value |
|------------|--------|
| System Power | **3.5955 kW** |
| Throughput | **220 picks/min** |
| Cost per Pick | **R0.000921 (0.0921 cents)** |
| Energy per Pick | **0.2724 Wh** |
| Capital Cost | **R646,793.46** |

Latency breakdown confirms the system meets real-time operation requirements within a **252 ms end-to-end cycle**, leaving safe timing margins.

---

## 🌱 Sustainability Impact

- **Environmental:** Diverts waste from landfills and reduces CO₂ emissions via efficient recycling.  
- **Economic:** Enables low-cost, scalable automation and job creation in recycling operations.  
- **Social:** Supports local participation and fair compensation for waste collection.  
- **Sustainable Development Goals (SDGs):**  
  - SDG 9 – Industry, Innovation, and Infrastructure  
  - SDG 11 – Sustainable Cities and Communities  
  - SDG 12 – Responsible Consumption and Production  
  - SDG 13 – Climate Action  

---

## 📈 Future Work

- Deploy physical prototype with real conveyor and robotic arm.  
- Expand dataset to include **paper** and **contaminated waste** classes.  
- Conduct multi-node federated training experiments.  
- Integrate **reinforcement learning** for adaptive pick strategies.  
- Add **predictive maintenance analytics** for industrial deployment.

---

## 📜 Citation

If you use this project or dataset, please cite:

> **Mhlengeni Miya (2025)**  
> *Smart and Sustainable Waste Sorting System for Beverage Containers with YOLOv11: Real-Time Robotic Recycling Using Edge Computing and Federated Learning.*  
> University of the Witwatersrand, Johannesburg.

---

## 📧 Contact

**Author:** Mhlengeni Miya  
**Email:** [mhlengeni.miya@gmail.com]  
**GitHub:** [https://github.com/mhlengeni](https://github.com/mhlengeni)

---

### ⭐ Acknowledgements
Special thanks to **Prof. Turgay Celik** for supervision and guidance.  
This work was supported by the **School of Electrical and Information Engineering, Wits University**, as part of the **Information Engineering Design II** course.
