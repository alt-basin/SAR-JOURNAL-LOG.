# SAR-JOURNAL-LOG.
this is were the drones summary of documentation will be located, be reminded that we would be using this prototype for our schools research

## Current Status

* Finalizing hardware selection
* Learning and implementing an Extended Kalman Filter (EKF)
* Researching autonomous navigation and localization methods
* Preparing documentation and development logs


---

  ### PROJECT OVERVIEW:

- This repository contains the documentation, development progress, and technical records for a prototype Search and Rescue (SAR) drone. The project is being developed as part of a school research initiative and serves as a platform for exploring autonomous aerial systems and low-cost disaster-response technologies.

#### Main Description

- The goal of this project is to develop a prototype autonomous-capable Search and Rescue (SAR) drone intended for outdoor disaster scenarios such as earthquakes, landslides, and floods.

  The system is designed to assist search operations by capturing aerial data and detecting heat signatures using a thermal camera. This capability may help identify potential heat sources associated with human presence in outdoor environments with reduced visibility, including nighttime conditions, smoke, or partially obstructed areas.

  The drone combines thermal imaging, optical flow, an Inertial Measurement Unit (IMU), and distance sensors to support stable flight and estimate its motion during operation. The project serves as a demonstration of how low-cost robotic aerial systems can contribute to SAR-oriented exploration, environmental monitoring, and situational awareness.

#### Reason for Build

- This project originated from hardware that was initially intended for a larger cargo-drone design being developed for a future robotics competition. During the planning stage, it became apparent that the selected components were not suitable for the intended cargo-drone requirements.

   Rather than discarding or selling the components, the decision was made to repurpose them into a Search and Rescue drone prototype that could also serve as a school research project.

   The project provides an opportunity to gain practical experience in drone development, autonomous navigation, sensor integration, state estimation, and embedded systems while making effective use of existing hardware resources.

---

### HARDWARE OVERVIEW:
#### Hardware list:
*sensor + electronics selection:*
<table border="1" cellpadding="10" cellspacing="0" style="border-collapse: collapse; width: 100%; font-family: Arial, sans-serif;">
  <thead>
    <tr style="background-color: #1a1a2e; color: white;">
      <th>Component</th>
      <th>Function</th>
      <th>Purpose in the Project</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>ICM-20602</strong></td>
      <td>Measures linear acceleration and angular velocity using a 3-axis accelerometer and 3-axis gyroscope.</td>
      <td>Provides orientation and motion data for flight stabilization, attitude estimation, and autonomous navigation.</td>
      <td><a href="https://shopee.ph/product/1541768712/47054536700" target="_blank">View Product</a></td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>PMW3901</strong></td>
      <td>Tracks the movement of the ground beneath the drone using optical flow technology.</td>
      <td>Estimates horizontal velocity and position, allowing stable flight in GPS-denied indoor environments.</td>
      <td><a href="https://shopee.ph/product/1538176896/43426280197" target="_blank">View Product</a></td>
    </tr>
    <tr>
      <td><strong>VL53L1X</strong></td>
      <td>Uses a laser Time-of-Flight (ToF) system to accurately measure the distance to nearby surfaces.</td>
      <td>Maintains altitude, enables vertical positioning, and assists in autonomous takeoff and landing.</td>
      <td><a href="https://shopee.ph/product/1032050598/22974977435" target="_blank">View Product</a></td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>MLX90640BAA</strong></td>
      <td>Captures a 32×24 thermal image by measuring infrared radiation emitted from objects.</td>
      <td>Detects heat signatures, performs thermal mapping, and assists in locating people or heat sources during search-and-rescue operations.</td>
      <td><a href="https://shopee.ph/product/1622086447/43117260078" target="_blank">View Product</a></td>
    </tr>
    <tr>
      <td><strong>ESP32-S3-WROOM-1 (N16R8)</strong></td>
      <td>Processes sensor data, executes control algorithms, and manages communication between all hardware components.</td>
      <td>Acts as the drone's primary controller, performing sensor fusion (EKF), flight control, autonomous navigation, telemetry, and system coordination.</td>
      <td>—</td>
    </tr>
  </tbody>
</table>

*Airframe and Power System*
<table border="1" cellpadding="10" cellspacing="0" style="border-collapse: collapse; width: 100%; font-family: Arial, sans-serif;">
  <thead>
    <tr style="background-color: #1a1a2e; color: white;">
      <th>Component</th>
      <th>Function</th>
      <th>Purpose in the Project</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>JMT X4 310mm Frame</strong></td>
      <td>Provides the structural framework for mounting and protecting all electronic and mechanical components.</td>
      <td>Serves as the drone's main chassis, ensuring stability, durability, and proper component placement during flight.</td>
      <td><a href="https://shopee.ph/product/936939040/18971876269" target="_blank">View Product</a></td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>Uangel X2807 1300KV Motor</strong></td>
      <td>Converts electrical energy into rotational motion to spin the propellers and generate thrust.</td>
      <td>Provides the lift and maneuverability required for stable flight, navigation, and autonomous operation.</td>
      <td><a href="https://shopee.ph/product/53025630/22476350635" target="_blank">View Product</a></td>
    </tr>
    <tr>
      <td><strong>45A 4-in-1 ESC</strong></td>
      <td>Controls the speed and direction of each brushless motor by regulating electrical power from the battery.</td>
      <td>Enables precise motor control for stable flight, attitude correction, and autonomous maneuvers.</td>
      <td><a href="https://shopee.ph/product/936939040/27822252961" target="_blank">View Product</a></td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>4S 3300mAh 60C LiPo Battery</strong></td>
      <td>Supplies electrical power to the motors, flight controller, sensors, and other onboard electronics.</td>
      <td>Acts as the drone's primary power source, providing sufficient energy for flight operations and autonomous missions.</td>
      <td><a href="https://shopee.ph/product/1400942760/28687044552" target="_blank">View Product</a></td>
    </tr>
  </tbody>
</table>

#### Schematic:
<img width="250" height="250" alt="Screenshot 2026-07-09 175718" src="https://github.com/user-attachments/assets/856acfcf-5dd7-4bc3-9b82-e8f52a9c49c9" />

[Drone Schematic](SCHEMATIC/GENERAL.SCHEMATIC.v1.pdf)


---

### SYSTEM OVERVIEW:

#### Perception system:

- This subsystem provides the drone’s perception and navigation capability for indoor search and rescue mapping. It combines motion sensing, position estimation, altitude measurement, and thermal imaging to allow controlled flight and environmental scanning in a confined area (2m × 2m).
  
<table>
    <thead>
        <tr>
            <th>Component</th>
            <th>Type</th>
            <th>Purpose</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ICM-20602</td>
            <td>IMU (Inertial Measurement Unit)</td>
            <td>Will be used as the sensor to determine the drone’s yaw, roll, and pitch, as well as its movement using the built-in accelerometer.</td>
        </tr>
        <tr>
            <td>PMW3901</td>
            <td>Optical Flow Sensor</td>
            <td>Will be used to determine the drone’s velocity in mid-air.</td>
        </tr>
        <tr>
            <td>VL53L1X + lid</td>
            <td>Time-of-Flight (ToF) Distance Sensor</td>
            <td>This will serve as the main sensor for measuring the drone’s altitude. However, this sensor is weaker outdoors, so testing and demonstrations will be conducted indoors.</td>
        </tr>
        <tr>
            <td>MLX90640BAA</td>
            <td>Thermal Infrared Camera</td>
            <td>This will be used to capture thermal images for mapping the environment.</td>
        </tr>
  </tbody>
</table>

#### **Control system:**

&emsp; *closed-loop system:*
- This part of the the subgroup measures the raw output of the sensors and filters them, allowing for smooth control.
<table>
    <thead>
        <tr>
            <th>Component</th>
            <th>Kalman Filter Category</th>
            <th>Reason</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>ICM-20602</td>
            <td>Extended Kalman Filter (EKF)</td>
            <td>Provides acceleration and angular velocity measurements used to predict the drone's state. Required for nonlinear attitude estimation.</td>
        </tr>
        <tr>
            <td>PMW3901</td>
            <td>Extended Kalman Filter (EKF)</td>
            <td>Provides optical flow used to correct velocity estimates. Depends on altitude and orientation, making the model nonlinear.</td>
        </tr>
        <tr>
            <td>VL53L1X</td>
            <td>Extended Kalman Filter (EKF)</td>
            <td>Provides range measurements for altitude estimation. Requires tilt compensation (roll/pitch), making the measurement nonlinear.</td>
        </tr>
        <tr>
            <td>MLX90640</td>
            <td>Not part of EKF</td>
            <td>Used for thermal imaging and environment mapping. Operates independently from state estimation.</td>
        </tr>
    </tbody>
</table>

---

**Editors note**

- This documentation is still a work in progress. Software development hasn't started yet. I've studied how the components connect, but haven't done extensive research on the implementation side. My first step is finalizing the PCB design, which depends on the drone frame's physical measurements, so sourcing the hardware is a prerequisite before I can begin.

  If you have any questions about the build, feel free to ask. Once complete, I'll share the PCB design files here for anyone to reference or reuse. I'll also compile the full development log and program documentation into this repository as the project progresses.

  All work will be openly shared with attribution. I'll be including my own mark on the PCB design as a form of authorship.


 **For Forge Reviewers**
  - I hope the components listed in the BOM can be funded, so I can measure and verify their physical dimensions before designing the PCB. This will help ensure the footprints and component placements are accurate and prevent alignment issues.
  
    I'll cover the cost of PCB fabrication myself and will upload the PCB design files to the project's GitHub repository once they're complete.

