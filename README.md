# SAR-JOURNAL-LOG.
this is were the drones summary of documentation will be located, be reminded that we would be using this prototype for our schools research
  ### PROJECT OVERVIEW:

   **Main description:**
  
  - The goal of this project is to develop a prototype autonomous Search and Rescue (SAR) drone for outdoor disaster scenarios such as earthquakes, landslides, and       floods.

    The system is designed to assist in search operations by capturing aerial data and detecting heat signatures using a thermal camera. This can help identify           potential human presence in outdoor environments with reduced visibility, such as nighttime conditions, smoke, or partially obstructed areas.

    The drone combines thermal imaging with optical flow, an IMU, and a distance sensor to maintain stable flight and estimate motion during flight. It is intended       as a demonstration of how low-cost robotics systems can support SAR-style exploration and situational awareness.

  **Reason for build:**

  - I created this project since I originally wanted to use the parts for my main drone for an upcoming robothon (on 2027) though I realized the drone isnt capable to be used as a cargo build. And because of that, I decided to repurpose the parts (that one we can see on log 13/06/2026 10:09 pm) as a school project.

    And originally I wanted to sell these parts, though I realized no-one from my country would buy a fiber glass drone, so I had to come up with ideas which landed on using it as a school project

    So at the end of the day, I regretted my descision for relying on gemini to see which parts should i choose (im a total begginer). Though my other drone is finilized, I hope that by the end of month im able to finish this repo and get the parts I need.

  **Curent status:**
  - Finalizing the Hardware
  - Creating the New schematic
  - Learning how to use EKF
  - finishing the BOM.CSV file
    
---

### HARDWARE OVERVIEW:
**Hardware list:**
- Here is the hardware parts and their respective links.
<table>
    <thead>
        <tr>
            <th>Component</th>
            <th>Purpose</th>
            <th>Link</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>BMI323</td>
            <td>Inertial Measurement Unit for orientation tracking</td>
            <td><a href="https://s.lazada.com.ph/s.Zg2ofY?c=v&t=p-iGrr7H6-s2LBxeDM">Product Link</a></td>
        </tr>
        <tr>
            <td>PMW3901</td>
            <td>Optical flow sensor for velocity estimation</td>
            <td><a href="https://shopee.ph/product/1538176896/43426280197">Product Link</a></td>
        </tr>
        <tr>
            <td>VL53L1X + lid</td>
            <td>Time-of-Flight distance sensor for altitude measurement</td>
            <td><a href="https://shopee.ph/product/1032050598/22974977435">Product Link</a></td>
        </tr>
        <tr>
            <td>MLX90640BAA</td>
            <td>Thermal infrared imaging camera for heat signature detection</td>
            <td><a href="https://shopee.ph/product/56540719/23154817594">Product Link</a></td>
        </tr>
        <tr>
            <td>Uangel X2807 1300KV Motor</td>
            <td>Brushless motors for thrust generation and flight control</td>
            <td><a href="https://shopee.ph/product/53025630/22476350635">Product Link</a></td>
        </tr>
        <tr>
            <td>45A 4-in-1 ESC</td>
            <td>Electronic speed controller for motor control</td>
            <td><a href="https://shopee.ph/product/936939040/27822252961">Product Link</a></td>
        </tr>
        <tr>
            <td>4S 3200mAh 60C LiPo</td>
            <td>Lithium polymer battery for system power supply</td>
            <td><a href="https://shopee.ph/product/1729536151/57358540563">Product Link</a></td>
        </tr>
         <tr>
            <td>JMT X4 310MM Drone frame</td>
            <td>The Frame of the drone that will hold all the parts together</td>
            <td><a href="https://shopee.ph/product/936939040/18971876269">Product Link</a></td>
        </tr>
    </tbody>
</table>

**Schematic:**

<img width="437" height="437" alt="Screenshot 2026-06-20 143220" src="https://github.com/user-attachments/assets/ed66fdbb-d4ec-4317-a78e-23893baee086" />

[Drone Schematic](Schematics+PCB/Schematic_drone.pdf)


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

   
