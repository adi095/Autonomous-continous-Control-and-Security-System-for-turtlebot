# TurtleBot Autonomous Navigation and Security Enhancement System

This project is an integrated system for **continuous control navigation** and **real-time anomaly detection** on the **TurtleBot3** platform. The system uses **deep reinforcement learning algorithms (DDPG and SAC)** for autonomous navigation and a **DBSCAN-based anomaly detection model** to enhance robot security by identifying sensor data anomalies from **LiDAR** and **IMU** sensors. Both systems share sensor data inputs from the TurtleBot3's **LiDAR** and **IMU** sensors in real time.

The project is divided into two parts:

- **Part A: Continuous Control Navigation System**
- **Part B: Security Enhancement System Using Anomaly Detection**

---

## 📋 **Project Structure**

```
📂 TurtleBot3_Navigation_and_Security
├── 📂 turtlebot3_custom          # Custom TurtleBot3 package with anomaly detection code
│   ├── src
│   │   └── injection_detection.py  # DBSCAN-based anomaly detection node
│   ├── CMakeLists.txt
│   └── package.xml
├── 📂 Navigation_System          # Code for the navigation system (DDPG/SAC)
│   ├── src
│   │   ├── ddpg_stage_1.py
│   │   └── sac_stage_1.py
│   └── launch
│       └── navigation.launch
├── 📂 Reward_Graphs              # Performance graphs for DDPG and SAC
├── README.md                     # Project documentation
└── LICENSE
```

---

## 🚀 **How to Run the Project**

### **1️⃣ Environment Setup**

1. **Install ROS 2**:

   ```bash
   sudo apt update && sudo apt upgrade
   sudo apt install ros-humble-desktop
   ```

2. **Set up your workspace:**

   ```bash
   mkdir -p ~/ros2_ws/src
   cd ~/ros2_ws/src
   ```

3. **Clone necessary packages for TurtleBot3:**

   ```bash
   git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
   git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
   git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
   ```

4. **Clone and build the custom TurtleBot3 package with anomaly detection code:**

   ```bash
   git clone https://github.com/your-repo-url/turtlebot3_custom.git
   ```

5. **Build the workspace:**

   ```bash
   cd ~/ros2_ws
   colcon build
   source ~/ros2_ws/install/setup.bash
   ```

---

### **2️⃣ Running Part A: Navigation System**

1. **Launch the Gazebo Simulation:**

   ```bash
   roslaunch turtlebot3_gazebo turtlebot3_stage_1.launch
   ```

2. **Run the Navigation Node:**

   - For **DDPG**:
     ```bash
     roslaunch project ddpg_stage_1.launch
     ```
   - For **SAC**:
     ```bash
     roslaunch project sac_stage_1.launch
     ```

---

### **3️⃣ Running Part B: Security Enhancement System**

1. **Run the Security Detection Node from the custom package:**

   ```bash
   roslaunch turtlebot3_custom security_detection.launch
   ```

2. The node will subscribe to **LiDAR** and **IMU** topics and process the incoming data in real time.

3. Anomalies detected using the **DBSCAN model** will trigger an alert and can be used to adjust navigation or flag potential attacks.

---

## 📊 **Data Flow Overview**

### **Part A: Navigation System:**

1. **TurtleBot3 Simulation** provides sensor data.
2. **Navigation Node (DDPG/SAC)** controls the robot based on sensor inputs and environment.
3. **Gazebo** simulation environment updates in real time.

### **Part B: Security Enhancement System:**

1. **LiDAR** and **IMU** data are collected via **rosbags**.
2. The **DBSCAN-based model** processes the data to detect anomalies.
3. **Anomaly alerts** are triggered, and navigation behavior can be adjusted accordingly.

---

## 🧪 **Testing and Results**

- **Navigation Performance:** Reward graphs for DDPG and SAC are included in the `Reward Graphs` folder.
- **Security System:** Logs showing detected anomalies are generated during real-time operation.

---

## 📚 **Further Improvements**

1. **Enhance the DBSCAN algorithm** to handle more complex anomaly patterns.
2. **Integrate adaptive navigation adjustments** based on detected anomalies.
3. **Extend the system to multi-robot environments.**

---

## 📜 **License**

This project is licensed under the MIT License. See the `LICENSE` file for details.

