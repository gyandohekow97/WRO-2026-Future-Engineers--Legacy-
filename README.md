# WRO Future Engineers - Team [Your Team Name]

Welcome to our official engineering repository for the World Robot Olympiad (WRO) Future Engineers category. This repository contains the complete open-source software architecture, hardware designs, and documentation for our fully autonomous robotic vehicle.

## ─── Project Overview ───
Our solution utilizes a **Raspberry Pi 4** as the primary computational unit, leveraging computer vision to navigate a track, obey traffic indicators (passing red obstacles on the right and green on the left), and successfully execute an automated parking sequence.

*   **Primary Controller:** Raspberry Pi 4 (4GB)
*   **Vision Engine:** Custom-trained YOLOv8-nano optimized via ONNX Runtime
*   **Language/Frameworks:** Python 3, OpenCV, PyTorch/Ultralytics

---

## ─── Repository Structure ───
*   `src/`: Core autonomous driving pipeline (perception, planning, and PID actuation modules).
*   `doc/`: Engineering schematics, flowcharts, and markdown documentation files.
*   `hardware/`: 3D printing STL files for custom chassis components and camera mounts.
*   `models/`: Exported neural network weights used for real-time obstacle detection.

---

## ─── Software Architecture & Obstacle Strategy ───

### 1. Modular Pipeline
To optimize performance on the Raspberry Pi 4's multi-core CPU, our software utilizes a micro-service architecture with independent threads synchronized via thread-safe queues:
*   **Perception:** Captures high-frame-rate video feeds and runs object detection inference.
*   **Planning:** Evaluates obstacle positioning and shifts the track centerline setpoint.
*   **Actuation:** Computes a closed-loop PID response to output PWM signals to the steering servo and drive motor.

### 2. Finite State Machine (FSM)
The high-level logic transitions predictably through distinct states: `INIT_WAIT` ➔ `LANE_FOLLOW` ➔ `PILOT_PILLAR` ➔ `PARK_SEEK` ➔ `PARK_EXEC` ➔ `MISSION_END`.

---

## ─── Installation & Local Setup ───

### Prerequisites
Ensure your Raspberry Pi or local development environment has Python 3.10+ installed.

### Setup Steps
1. Clone this repository:
   ```bash
   git clone [https://github.com/gyandohekow97/WRO-2026-Future-Engineers--Legacy-](https://github.com/gyandohekow97/WRO-2026-Future-Engineers--Legacy-))
   cd WRO-2026-Future-Engineers--Legacy-

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   
3. Run the primary orchestrator:
   ```bash
   python src/main.py

---

## ─── Performance Metrics ───
   Inference Speed: ~22-25 FPS on Raspberry Pi 4 CPU using ONNX quantization.
   Tracking Accuracy: Mean Cross-Track Error kept under 2.3 cm during variable
   corridor tracking tests.
   
   
