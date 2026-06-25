# SAR-JOURNAL-LOG.
this is were the drones summary of documentation will be located, be reminded that we would be using this prototype for our schools research
  ### PROJECT OVERVIEW:
# SAR-JOURNAL-LOG

This repository contains the documentation, development progress, and technical records for a prototype Search and Rescue (SAR) drone. The project is being developed as part of a school research initiative and serves as a platform for exploring autonomous aerial systems and low-cost disaster-response technologies.

### Main Description

* The goal of this project is to develop a prototype autonomous Search and Rescue (SAR) drone for outdoor disaster scenarios such as earthquakes, landslides, and floods.

* The system is designed to assist search operations by capturing aerial data and detecting heat signatures using a thermal camera. This capability may help identify potential human presence in outdoor environments with reduced visibility, including nighttime conditions, smoke, or partially obstructed areas.

* The drone combines thermal imaging, optical flow, an Inertial Measurement Unit (IMU), and distance sensors to maintain stable flight and estimate motion during operation. The project serves as a demonstration of how low-cost robotics systems can support SAR-style exploration, environmental monitoring, and situational awareness.

### Reason for Build

* This project originated from hardware that was initially intended for a larger cargo-drone design being developed for a future robotics competition. During the planning stage, it became apparent that the selected components were not suitable for the intended cargo-drone requirements.

* Rather than discarding or selling the components, the decision was made to repurpose them into a Search and Rescue drone prototype that could also serve as a school research project.

* The project provides an opportunity to gain practical experience in drone development, autonomous navigation, sensor integration, state estimation, and embedded systems while making effective use of existing hardware resources.

### Current Status

* Finalizing hardware selection
* Learning and implementing an Extended Kalman Filter (EKF)
* Researching autonomous navigation and localization methods
* Preparing documentation and development logs

---

### HARDWARE OVERVIEW:
**Hardware list:**
- Here is the hardware parts and their respective links.
<table> <thead> <tr> <th>Component</th> <th>Purpose</th> <th>Link</th> </tr> </thead> <tbody> <tr> <td>BMI323</td> <td>Inertial Measurement Unit (IMU) for orientation and motion tracking</td> <td><a href="https://s.lazada.com.ph/s.Zg2ofY?c=v&t=p-iGrr7H6-s2LBxeDM">Product Link</a></td> </tr> <tr> <td>PMW3901</td> <td>Optical flow sensor for horizontal velocity estimation</td> <td><a href="https://shopee.ph/product/1538176896/43426280197">Product Link</a></td> </tr> <tr> <td>VL53L1X (ToF Module)</td> <td>Time-of-Flight sensor for altitude measurement and vertical stability</td> <td><a href="https://shopee.ph/product/1032050598/22974977435">Product Link</a></td> </tr> <tr> <td>MLX90640BAA</td> <td>Thermal infrared camera for heat signature detection and mapping</td> <td><a href="https://shopee.ph/product/56540719/23154817594">Product Link</a></td> </tr> <tr> <td>Uangel X2807 1300KV Motor</td> <td>Brushless motors for thrust generation and flight control</td> <td><a href="https://shopee.ph/product/53025630/22476350635">Product Link</a></td> </tr> <tr> <td>45A 4-in-1 ESC</td> <td>Electronic speed controller for regulating motor speed</td> <td><a href="https://shopee.ph/product/936939040/27822252961">Product Link</a></td> </tr> <tr> <td>4S 3200mAh 60C LiPo Battery</td> <td>Main power source for propulsion and onboard electronics</td> <td><a href="https://shopee.ph/product/1729536151/57358540563">Product Link</a></td> </tr> <tr> <td>JMT X4 310mm Frame</td> <td>Structural frame supporting all drone components</td> <td><a href="https://shopee.ph/product/936939040/18971876269">Product Link</a></td> </tr> <tr> <td>ESP32-S3-WROOM-1 (N16R8, Camera Variant)</td> <td>Main flight controller for sensor fusion (EKF), optical flow processing, PID control, and telemetry</td> <td><a href="https://www.espressif.com/en/products/socs/esp32-s3">Product Reference</a></td> </tr> </tbody> </table>

**Schematic:**

<img width="437" height="437" alt="Screenshot 2026-06-20 143220" src="https://github.com/user-attachments/assets/ed66fdbb-d4ec-4317-a78e-23893baee086" />

[Drone Schematic](SCHEMATIC/SCHEMATIC.pdf)


---

### SYSTEM OVERVIEW:

&ensp;**Perception system:**

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
            <td>BMI323</td>
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

&ensp; **Control system:**

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
            <td>BMI323 (IMU)</td>
            <td rowspan="3">Extended Kalman Filter (EKF)</td>
            <td>Provides acceleration and angular velocity measurements used to predict the drone's state. Required for nonlinear attitude estimation.</td>
        </tr>
        <tr>
            <td>PMW3901 (Optical Flow)</td>
            <td>Provides optical flow used to correct velocity estimates. Depends on altitude and orientation, making the model nonlinear.</td>
        </tr>
        <tr>
            <td>VL53L1X (ToF)</td>
            <td>Provides range measurements for altitude estimation. Requires tilt compensation (roll/pitch), making the measurement nonlinear.</td>
        </tr>
        <tr>
            <td>MLX90640 (Thermal Camera)</td>
            <td>Not part of EKF</td>
            <td>Used for thermal imaging and environment mapping. Operates independently from state estimation.</td>
        </tr>
    </tbody>
</table>

**Editors note**
- Now before you question my way of creating this repo, be reminded that this is still in progress. I still havent made much research on the software though I have already studied how to connect these parts. and my first pcb design would need the measurements of the drone frame, so before i start i would also need the hardware first before i actually start on creating the pcb.

- so if you have any questions regarding the build, yes i will be giving the pcb designs and place him here for you to copy, and yes i will also create a file compiling all the grueling work of the program into here

  i sincerely hope no-one woudl take credit since i will be putting my face in the pcb.

   
