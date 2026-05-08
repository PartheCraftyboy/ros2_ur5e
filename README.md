# Autonomous Motherboard Assembly with UR5e

An industrial robotics simulation project using **ROS 2 Humble**, **MoveIt 2**, and **Gazebo**. This project demonstrates a UR5e robotic arm performing repetitive high-precision assembly (screwing) tasks on a motherboard within a simulated environment.

## 🚀 Overview
The goal of this project is to automate the process of securing a motherboard onto a chassis. The system uses a UR5e manipulator equipped with a screwdriver end-effector to trace a cyclic path from a home position to specific screw coordinates on a motherboard.

### Key Features
* **ROS 2 Framework:** Built on the Humble/Iron distribution for robust node communication.
* **MoveIt 2 Planning:** Handles Inverse Kinematics (IK) and collision-free trajectory planning.
* **Gazebo Simulation:** A high-fidelity physics environment including a laboratory room, industrial table, and motherboard.
* **Automated Looping:** A Python-based execution node that cycles through approach, screw, and retract sequences indefinitely.

## 🛠 Tech Stack
* **Robot:** UR5e (6-DOF)
* **Software:** ROS 2, MoveIt 2, Gazebo Classic/Ignition
* **Language:** Python 3, C++ (for URDF/Xacro)
* **Controllers:** `joint_trajectory_controller`, `robot_state_publisher`

## 🏗 System Architecture
The project follows a standard ROS 2 architecture:
1.  **URDF/Xacro:** Defines the physical hierarchy (Table -> Robot Base -> Tool Flange).
2.  **MoveIt Config:** Configures the kinematic solver and planning groups.
3.  **Task Node:** A Python script using the `MoveGroupInterface` to send goal poses to the robot.

## 📦 Installation
1.  **Clone the repository:**
    ```bash
    mkdir -p ~/ros2_ws/src
    cd ~/ros2_ws/src
    git clone <your-repo-link>
    ```
2.  **Install dependencies:**
    ```bash
    cd ~/ros2_ws
    rosdep install --from-paths src --ignore-src -r -y
    ```
3.  **Build the workspace:**
    ```bash
    colcon build --symlink-install
    source install/setup.bash
    ```

## 🎮 Running the Simulation
1.  **Launch Gazebo and MoveIt:**
    ```bash
    ros2 launch custom_ur5e_tool ur5e_lab_moveit_gazebo.launch.py run_autonomous_task:=false
    ```
2.  **Run the Scene and Autonomy Script:**
    ```bash
    ros2 launch custom_ur5e_tool ur5e_lab_moveit_gazebo.launch.py run_autonomous_task:=true
    ```


---
Developed for the **Robotics and Automation** course.
