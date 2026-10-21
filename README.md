# AI-Enabled Smart Traffic Management & Emergency Vehicle Priority System

An AI-powered traffic management system that uses computer vision, YOLO-based vehicle detection, and ESP32-based IoT integration to monitor traffic density, optimize traffic signal timing, and prioritize emergency vehicles at four-way intersections.

## 📌 Project Overview

Traditional traffic signal systems generally operate using fixed time intervals, regardless of the actual number of vehicles waiting at an intersection. This can lead to unnecessary waiting times, traffic congestion, and delays for emergency vehicles such as ambulances, fire engines, and police vehicles.

The **AI-Enabled Smart Traffic Management & Emergency Vehicle Priority System** aims to address these challenges by combining Artificial Intelligence (AI), Computer Vision, Embedded Systems, and the Internet of Things (IoT).

The system uses **C++, OpenCV, and YOLO** to detect vehicles from camera input and estimate traffic density for different roads. Based on the detected vehicle count, adaptive traffic signal control logic determines the green-light duration for each direction. When an emergency vehicle is detected, the system activates priority-based signal control to help provide a faster passage through the intersection.

An **ESP32 microcontroller** serves as the hardware interface for communicating traffic control decisions to the connected signal-control components.

## 🎯 Project Objectives

- Detect vehicles automatically using YOLO-based object detection.
- Estimate real-time traffic density for each direction of a four-way intersection.
- Dynamically adjust green-light duration based on traffic conditions.
- Detect emergency vehicles and give them higher signal priority.
- Integrate AI-based traffic analysis with ESP32-based embedded hardware.
- Reduce unnecessary vehicle waiting time and improve traffic flow.
- Demonstrate an intelligent, scalable approach to smart-city traffic management.

## ✨ Key Features

### 1. AI-Based Vehicle Detection

The system uses YOLO (You Only Look Once), an object detection model, to identify vehicles in camera frames.

OpenCV handles image and video processing, allowing the system to process incoming frames and prepare visual information for vehicle detection.

Depending on the trained model and its supported classes, the system can detect vehicles such as:

- Cars
- Motorcycles
- Buses
- Trucks

### 2. Real-Time Traffic Density Estimation

The system analyzes detected vehicles in different traffic lanes or road directions to estimate traffic density.

Based on the number of detected vehicles, each direction can be classified into traffic levels such as:

- **Low Traffic:** Fewer vehicles are waiting.
- **Medium Traffic:** A moderate number of vehicles are waiting.
- **High Traffic:** A large number of vehicles are waiting.

This information is used by the traffic control logic to determine which direction requires more green-light time.

### 3. Adaptive Traffic Signal Control

Instead of relying entirely on fixed-duration signals, the system uses traffic density to determine the green-light duration for each road.

For example:

- A road with low traffic receives a shorter green-light duration.
- A road with medium traffic receives a moderate green-light duration.
- A road with high traffic may receive a longer green-light duration.

The controller evaluates the traffic conditions of the four directions and selects the next signal phase according to the programmed scheduling logic.

This adaptive approach can improve traffic flow compared with a purely fixed-time system.

### 4. Emergency Vehicle Detection and Priority

Emergency vehicle priority is a major feature of the project.

The system identifies emergency vehicles, such as ambulances, fire engines, and police vehicles, when the detection model or configured recognition mechanism supports their identification.

When an emergency vehicle is detected, the control logic gives its approach priority over normal traffic scheduling.

The priority mechanism can be designed to:

- Identify the road direction containing the emergency vehicle.
- Temporarily prioritize that direction in the signal-control sequence.
- Coordinate signal transitions to provide a clear passage.
- Resume normal adaptive traffic control after the priority event is handled.

Emergency vehicle recognition depends on the model classes, training data, or additional identification logic used in the implementation.

### 5. ESP32-Based IoT Integration

The ESP32 microcontroller connects the software-based traffic management logic to the hardware control system.

Its role can include:

- Receiving traffic signal commands from the processing system.
- Controlling connected LEDs or signal indicators through GPIO pins.
- Representing red, yellow, and green traffic signal states.
- Executing the signal-control sequence according to received commands.

The exact communication method depends on the implementation, such as serial communication or a supported wireless protocol.

### 6. Four-Way Intersection Management

The system is designed around a four-way intersection with four traffic directions.

Each direction is evaluated using vehicle detection and traffic density estimation. The signal controller uses these values to determine the appropriate sequence and duration of green-light phases.

Signal transitions must be coordinated to prevent conflicting green lights and support safe intersection operation.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| C++ | Core programming and traffic control logic |
| OpenCV | Image processing and video frame handling |
| YOLO | Vehicle object detection |
| ESP32 | Embedded control and hardware integration |
| IoT | Communication between software and hardware components |
| Arduino IDE | ESP32 programming and development, if used |
| Camera / Video Input | Traffic observation and vehicle detection |

## 🏗️ System Architecture

The project follows a pipeline that connects camera input, AI-based analysis, traffic decision-making, and embedded hardware control.

```text
          Camera / Video Input
                   |
                   v
          OpenCV Frame Processing
                   |
                   v
           YOLO Vehicle Detection
                   |
                   v
       Vehicle Classification / Counting
                   |
                   v
        Traffic Density Estimation
                   |
                   v
       Emergency Vehicle Identification
                   |
                   v
        Adaptive Signal Control Logic
                   |
                   v
             ESP32 Controller
                   |
                   v
         Traffic Signal Indicators
```

The emergency vehicle identification and traffic density analysis feed into the signal control logic, which determines the appropriate signal phase and duration.

## ⚙️ Working Methodology

### Step 1: Capture Traffic Data

A camera or recorded video provides traffic footage from the intersection. The system processes the available frames using OpenCV.

### Step 2: Detect Vehicles

YOLO processes the frames to identify vehicles and return detection results, such as object classes and bounding boxes.

### Step 3: Estimate Traffic Density

The system counts the detected vehicles within configured road regions or lanes. These counts are used to estimate the traffic level for each direction.

### Step 4: Identify Emergency Vehicles

The emergency detection mechanism checks whether a recognized emergency vehicle is approaching from a particular direction. This requires appropriate model support or additional identification logic.

### Step 5: Calculate Signal Priority

The traffic control algorithm compares the traffic conditions across all four directions. Under normal conditions, it allocates green-light time according to traffic density. When an emergency vehicle is identified, the priority logic adjusts the normal scheduling sequence.

### Step 6: Send Control Commands

The selected signal state and timing information are communicated to the ESP32 through the configured interface.

### Step 7: Update Traffic Signals

The ESP32 controls the connected signal indicators according to the received commands. The system continues processing new traffic frames and updates its decisions as conditions change.

## 💻 Software and Hardware Requirements

### Software

- C++ compiler
- OpenCV
- YOLO model and its required inference framework
- Arduino IDE or another supported ESP32 development environment
- Git and GitHub

### Hardware

- ESP32 development board
- Camera or traffic video source
- LEDs or traffic signal indicators
- Appropriate resistors and connecting wires
- Breadboard or prototype circuit
- USB cable and power supply

Additional hardware may be required depending on the camera setup and communication method.

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/nileshpatidar62/AI-Enabled-Smart-Traffic-Management-Emergency-Vehicle-Priority-System.git
```

### 2. Navigate to the Project Directory

```bash
cd AI-Enabled-Smart-Traffic-Management-Emergency-Vehicle-Priority-System
```

### 3. Install Dependencies

Install OpenCV and the dependencies required by your selected YOLO implementation.

For example, on an Ubuntu-based system, OpenCV development libraries can be installed using:

```bash
sudo apt update
sudo apt install build-essential cmake libopencv-dev
```

If your implementation uses a particular YOLO inference framework, follow that framework's installation instructions and download the compatible model weights.

### 4. Configure the Project

Before running the application:

- Configure the camera or video input source.
- Set the correct path to the YOLO model and its configuration files.
- Configure the detection classes and traffic-region boundaries.
- Set the traffic density thresholds and signal timing rules.
- Configure the ESP32 communication interface and hardware pin assignments.

Use the actual filenames and configuration options provided in your repository.

### 5. Build and Run

The exact build and execution commands depend on the project's source files and build configuration. If the project uses a standard C++ source file and OpenCV, a basic compilation command may look like this:

```bash
g++ main.cpp -o traffic_system `pkg-config --cflags --libs opencv4`
```

Run the application with:

```bash
./traffic_system
```

This example assumes that the entry point is `main.cpp`, the installed OpenCV version is discoverable through `pkg-config`, and the required YOLO inference dependencies are configured. Adapt the command to match the actual project structure.

### 6. Configure the ESP32

Open the ESP32 firmware in Arduino IDE or the development environment used by your project.

1. Select the correct ESP32 board and communication port.
2. Configure the GPIO pins for the signal indicators.
3. Set up the communication interface.
4. Upload the firmware to the ESP32.
5. Verify that received signal commands produce the intended indicator states.

## 📊 Expected Results

When correctly configured, the system is intended to demonstrate the following behavior:

- Vehicles are detected from camera or video input.
- Traffic density is estimated for all configured intersection directions.
- Signal duration changes according to traffic conditions.
- Emergency vehicles receive priority when successfully identified.
- The ESP32 controls connected traffic signal indicators according to the control commands.

Actual detection accuracy, response time, and traffic-flow improvements depend on the model, camera conditions, hardware configuration, and signal-control implementation. These should be measured during testing rather than assumed.

## 🔬 Testing and Evaluation

The system can be evaluated using different traffic scenarios:

| Test Scenario | Expected Behavior |
|---|---|
| Low traffic | Shorter green-light duration |
| Medium traffic | Moderate green-light duration |
| High traffic | Longer green-light duration, subject to configured limits |
| Unequal traffic across roads | Signal timing adapts to relative traffic demand |
| Emergency vehicle detected | Priority logic selects the emergency vehicle's approach |
| Traffic conditions change | New detections update the control decision |
| Hardware communication | ESP32 receives valid commands and updates signal indicators |

Useful performance metrics include:

- Vehicle detection precision and recall
- Vehicle counting accuracy
- Emergency vehicle detection accuracy
- Signal response time
- Average waiting time in controlled test scenarios
- Reliability of software-to-ESP32 communication

## 🌍 Applications

- Smart-city traffic management
- Intelligent transportation systems
- Emergency vehicle priority systems
- Adaptive traffic signal control
- IoT-based traffic monitoring
- Academic projects in AI, embedded systems, and computer vision

## 🔮 Future Enhancements

- Train or fine-tune a model specifically for emergency vehicle recognition.
- Add ambulance siren detection using audio processing.
- Introduce vehicle tracking to reduce repeated counting across video frames.
- Implement pedestrian detection and pedestrian crossing phases.
- Develop a real-time dashboard to display traffic density and signal status.
- Store traffic statistics for historical analysis and congestion forecasting.
- Integrate multiple intersections for coordinated traffic management.
- Evaluate reinforcement learning or other optimization techniques for signal scheduling.
- Add fault detection, communication monitoring, and a safe fallback mode.

## ⚠️ Limitations and Safety Considerations

The project's performance depends on camera placement, lighting, weather, occlusion, detection-model accuracy, and communication reliability.

Emergency vehicle identification must be validated carefully. A false detection or missed emergency vehicle can lead to incorrect signal decisions.

A physical traffic signal deployment would require additional safeguards, including conflict-free phase transitions, yellow and all-red clearance intervals, hardware interlocks where appropriate, fail-safe behavior, and compliance with applicable traffic engineering standards. This prototype should not be connected to live public-road traffic signals without professional validation and authorization.

## 👨‍💻 Author

**Nilesh Patidar**

Electronics Engineering Student | Embedded Systems | AI & Computer Vision | IoT

- GitHub: [nileshpatidar62](https://github.com/nileshpatidar62)

## 📄 License

Add a license such as the MIT License if you want others to reuse and modify the project under its terms. Include a `LICENSE` file in the repository before claiming that the project is distributed under that license.

---

**Project Summary:** An AI-enabled traffic management prototype that combines YOLO-based vehicle detection, OpenCV image processing, adaptive signal scheduling, emergency vehicle prioritization, and ESP32-based hardware control to demonstrate intelligent traffic management at four-way intersections.
