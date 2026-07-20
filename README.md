# Sensor-Controlled Thermal Mapping for Search and Rescue Operations (SCOUT) 

**Editor's Note**

- This project is still a work in progress. Software development has not yet begun. While I have studied how the hardware components interface with one another, I have not yet started the implementation phase. My current priority is designing the custom PCB. Since the PCB layout depends on the exact physical dimensions of the drone frame and its components, obtaining the hardware is a necessary first step to ensure accurate measurements, footprints, and component placement.

  If you have any questions or suggestions regarding the project, feel free to reach out. As development progresses, I will publish the PCB design files, complete development logs, and software documentation in this repository for others to reference, learn from, or reuse. All project materials will be openly shared with proper attribution. The PCB design will also include my personal signature as a mark of authorship.

**For Forge Reviewers**

- I hope the components listed in the Bill of Materials (BOM) can be funded so I can verify their physical dimensions before completing the PCB design. This will help ensure accurate footprints, proper component placement, and minimize alignment issues during assembly.

  I will cover the cost of PCB fabrication myself and will upload the completed PCB design files to this GitHub repository once they are finalized.


**Current Status**

* Learning and implementing an Extended Kalman Filter (EKF)
* Researching autonomous navigation and localization methods
* Preparing documentation and development logs

---

  ### PROJECT OVERVIEW:
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
      <td><strong>55A 4-in-1 ESC</strong></td>
      <td>Controls the speed and direction of each brushless motor by regulating electrical power from the battery.</td>
      <td>Enables precise motor control for stable flight, attitude correction, and autonomous maneuvers.</td>
      <td><a href="https://shopee.ph/product/709543365/28338653787" target="_blank">View Product</a></td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>6S 5200mAh 60C LiPo Battery</strong></td>
      <td>Supplies electrical power to the motors, flight controller, sensors, and other onboard electronics.</td>
      <td>Acts as the drone's primary power source, providing sufficient energy for flight operations and autonomous missions.</td>
      <td>—</td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>PRO MINI560</strong></td>
      <td> is a <strong>DC-DC buck converte</strong> that efficiently reduces a higher input voltage to a stable lower output voltage for electronic devices.</td>
      <td>Acts as the drone's primary power source, providing sufficient energy for flight operations and autonomous missions.</td>
      <td><a href="https://shopee.ph/product/1400942760/28687044552" target="_blank">View Product</a></td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>7040 Gemfan Tri-Blade</strong></td>
      <td> Converts the motor's rotational force into thrust, allowing the UAV to generate lift and maneuver during flight.</td>
      <td> Provides stable and efficient lift for the SCOUT UAV while carrying its onboard sensors and thermal camera during autonomous missions.</td>
      <td>—</td>
    </tr>
  </tbody>
</table>

#### Schematic:

<table>
  <tr>
    <!-- Left Column -->
    <td width="55%" valign="top">

<h2>Hardware Connections</h2>

<table>
  <thead>
    <tr>
      <th>Component</th>
      <th>Connection</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>VL53L1X</strong></td>
      <td>SDA → GPIO 8<br>SCL → GPIO 9</td>
    </tr>
    <tr>
      <td><strong>MLX90640BAA</strong></td>
      <td>SDA → GPIO 8<br>SCL → GPIO 9</td>
    </tr>
    <tr>
      <td><strong>ICM-20602</strong></td>
      <td>SAO/SDO → GPIO 13<br>SDA/SDI → GPIO 11<br>SCL/SPC → GPIO 12</td>
    </tr>
    <tr>
      <td><strong>PMW3901</strong></td>
      <td>MISO → GPIO 13<br>CLK → GPIO 12<br>MOSI → GPIO 11<br>CS → GPIO 10</td>
    </tr>
    <tr>
      <td><strong>45A 4-in-1 ESC</strong></td>
      <td>
        M1 → GPIO 4<br>
        M2 → GPIO 5<br>
        M3 → GPIO 6<br>
        M4 → GPIO 7<br>
        GND → IN−<br>
        VCC → IN+
      </td>
    </tr>
  </tbody>
</table>

> **Note:** The VL53L1X and MLX90640BAA share the same I²C bus (GPIO 8 & 9), while the ICM-20602 and PMW3901 share the SPI bus (GPIO 11–13).

</td>

<!-- Right Column -->
<td width="45%" align="center" valign="top">

<img width="480" height="702" alt="Screenshot 2026-07-14 184025" src="https://github.com/user-attachments/assets/5ba21b90-08f9-441e-a6dc-6de97789491d" />

<br><br>

<i>Figure 1. Current hardware wiring diagram.</i>

</td>
</tr>
</table>

[Drone Schematic](SCHEMATIC/GENERAL.SCHEMATIC.v1.png)


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
