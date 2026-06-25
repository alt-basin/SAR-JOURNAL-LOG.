# DEVLOG #001: INTRODUCTION

 **Duration:** pre-repo work
 
 first ever log for the drone, i have already created the schematic, though i will need to continue creating the <br> drones
 pcb to hold the parts which may take a long time. So lets start by discussing the parts of the drone.

  im currently using a 
   - JMT X4 310MM X4M310L
   - Uangel X2807 1300Kv
   - 6s 5200mah XT60

<img width="1468" alt="7df4a46b-1eed-4ec3-b51c-5aaf73f997b2" src="https://github.com/user-attachments/assets/40fe4ef9-3b4f-493a-aecb-d6235808feec" />
<img width="1344" alt="e7acb897-12b7-4c4b-9561-0c1f1995207d" src="https://github.com/user-attachments/assets/5a8e8c9a-11cf-4d64-85b2-32eefddaecbe" />

---
# DEVLOG #002: INTRO TO SCHEMATIC

 **Duration:** pre-repo work

   ### SENSORS:
   
  - Below me is the schematic for the drone, which includes the parts needed for it to be full automated, so lets start one by one.
    for this dorone i will be using a ESP32-S3-WROOM-N16R8-1 as the flight control, and i will be using a 45A esc 4-in-1.
    
 <img width="605" alt="Screenshot 2026-06-11 200743" src="https://github.com/user-attachments/assets/af78e5a9-d560-40a3-a7d0-d05206c7846e" />
 
<table>
    <thead>
        <tr>
            <th>Component</th>
            <th>Type</th>
            <th>Purpose</th>
            <th>Link</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>MPU-6050</td>
            <td>IMU (Inertial Measurement Unit)</td>
            <td>Measures angular velocity and acceleration for estimating the drone's orientation and movement.</td>
            <td><a href="https://shopee.ph/product/580325202/25288429666">Product Link</a></td>
        </tr>
        <tr>
            <td>PMW3901</td>
            <td>Optical Flow Sensor</td>
            <td>Measures relative ground movement to estimate horizontal velocity and position changes.</td>
            <td><a href="https://shopee.ph/product/1538176896/43426280197">Product Link</a></td>
        </tr>
        <tr>
            <td>VL53L1X + Lid</td>
            <td>Time-of-Flight (ToF) Distance Sensor</td>
            <td>Measures the distance to the ground, providing altitude data for low-altitude indoor flight.</td>
            <td><a href="https://shopee.ph/product/1032050598/22974977435">Product Link</a></td>
        </tr>
        <tr>
            <td>MLX90640BAA</td>
            <td>Thermal Infrared Camera</td>
            <td>Captures thermal images for heat-source detection and thermal environment mapping.</td>
            <td><a href="https://shopee.ph/product/56540719/23154817594">Product Link</a></td>
        </tr>
        <tr>
            <td>45A 4-in-1 ESC</td>
            <td>Electronic Speed Controller</td>
            <td>Controls the speed of the brushless motors and distributes power from the battery.</td>
            <td><a href="https://shopee.ph/product/933050849/26220013460">Product Link</a></td>
        </tr>
        <tr>
            <td>4S 3200mAh 60C LiPo</td>
            <td>Lithium Polymer Battery</td>
            <td>Supplies electrical power to the drone's flight and sensing systems.</td>
            <td><a href="https://shopee.ph/product/1729536151/57358540563">Product Link</a></td>
        </tr>
    </tbody>
</table>

---
# DEVLOG #003: DRONE FRAME 

 **Duration:** pre-repo work

 - The drone frame assembly was completed after the M3 nuts arrived. Below is a showcase of the finished frame from multiple angles.
  
  <img width="2048" height="1289" alt="c05a2e44-0346-4d8f-9d85-8e693a4ecb37" src="https://github.com/user-attachments/assets/f830b4bb-87ad-4105-bba7-587b4fd0105a" />
<img width="2048" height="1080" alt="51f45b0d-6c06-419b-8082-c667ce248333" src="https://github.com/user-attachments/assets/c1e46a0f-3564-4fb7-b8f5-38b5e1ce30d4" />
<img width="2048" height="1149" alt="b290c748-67dc-41cf-a960-94b504ee50dd" src="https://github.com/user-attachments/assets/c97fdf34-7f96-4b94-ab0f-5ec8b3d143d8" />

---
# DEVLOG #004: INTRODUCTION FOR BMI323


 **Duration:** 5 minutes

 - I decided to switch from the MPU6050 to a better IMU, the BMI323. This is mainly because it has lower drift and improved overall performance. I also considered using an ICM-series IMU, but most online stores currently do not have it available.

- The main difference between the two is their sensor performance and accuracy, which includes improvements in noise levels, stability, and motion tracking reliability in the BMI323 compared to the MPU6050. 

| Feature                       | MPU6050                         | BMI323                                           |
| ----------------------------- | ------------------------------- | ------------------------------------------------ |
| Gyro noise density            | ~0.005–0.01 °/s/√Hz             | ~0.003 °/s/√Hz (lower = better)                  |
| Accelerometer noise           | ~400 µg/√Hz                     | ~80–120 µg/√Hz                                   |
| Gyro range                    | ±250 to ±2000 °/s               | ±125 to ±2000 °/s (configurable, cleaner output) |
| Accelerometer range           | ±2g to ±16g                     | ±2g to ±16g                                      |
| Bias instability (gyro drift) | ~10–20 °/hr (worse in practice) | ~2–5 °/hr (much better)                          |
| Output resolution             | 16-bit                          | 16–24 bit effective processing                   |
| Sample rate                   | up to 1 kHz                     | up to 6.4 kHz (depends config)                   |
| Power consumption             | ~3.9 mA                         | ~0.8–1.5 mA (more efficient)                     |



<img width="250" alt="Screenshot 2026-06-17 202725" src="https://github.com/user-attachments/assets/64dfa1e8-335d-4858-bfa8-9bc3af585bfa" />

---
# DEVLOG #005: NEW SYMBOL AND SCHEMATIC

**Duration:** 10 minutes

 - So i just created the new schematic for the drone which included the new IMU (BMI323).
   so the reason why I didnt do this yesterday is because i had assignments, and also i was lazy.

   it took around 4 mins to create the new symbol for the imu since i was trying to find the exact board model
   in a datasheet though i found the model by a youtube video. Which also described how to use it.

  <img width="471" height="437" alt="Screenshot 2026-06-20 142921" src="https://github.com/user-attachments/assets/656dd6a2-f679-4263-9131-98dd4fc3c475" />
  <img width="471" height="437" alt="Screenshot 2026-06-20 143220" src="https://github.com/user-attachments/assets/d3b06de2-813e-4c4f-b145-ca3735b05715" />

https://github.com/alt-basin/SAR-JOURNAL-LOG./blob/main/Schematics%2BPCB/Schematic_drone.pdf

---

# DEVLOG #006: MEASUREMENTS FOR PCB

**Duration:** 26 minutes 28 seconds

- I decided to measure the drone frame (shown below) so I can use it as a reference for the PCB's shape, which will host the ESP32-S3-WROOM-1, IMU (Inertial   Measurement Unit), and other components.

  Right now, I am only preparing the measurements for the PCB since it will be mounted directly onto the frame. I am also waiting for the sensors to arrive so I can measure their pin layouts and dimensions accurately. I believe it is better to rely on measurements taken from the actual physical components rather than using dimensions from online sources.

  Here are the measurements.

  <img width="480" alt="34cc6814-a46b-4476-9909-0267edcaa080" src="https://github.com/user-attachments/assets/2fa67dbd-bcc2-4e36-bfd9-b222d9bc8efa" />
  <img width="370.75" alt="341fd21e-3ca5-4c1e-b4bd-874106287189" src="https://github.com/user-attachments/assets/6a432389-2464-4d20-86c1-fc179580ab7e" />

 - I just wanted to show this to you since I currently have assignments to work on, and I won't be able to create the <br> actual measurements in a 3D model yet. I may have to work on it during the weekend.

---

# DEVLOG #007: UPDATE FOR REPO AND NEW SENSOR

**Duration:**

- So since I dont have any assignments today, i decided to create a data table for each sensor. So you could know whats the capabilities, while doing so I realized that my current imu (which is BMI323), is weak. Not that its fully weak but for testing that uses autonomous programming, this would be a problem.

  Then i asked gpt for potential sensors that are better than the current (BMI323) and recommended me to use and ICM-42688-P, which is better over all. The main problem wasnt cost as i have it covered, the main problem is the market availability. Each shopping app basically have this type of sensor, the problem was that it was all out of stock.

**6:27 pm**

- I was talking with Gpt about the sensors to find the common and cheapest, which landed me on the ICM-20602. so comparing this with the current bmi323, here are the data table. Now even though it may just be like a point different from a bmi, i only want to switch as the bmi323 isnt really popular.

  now that i have decided what kind of sensor i will use, i should probably change the BOM first, then i will start on creating the new schematic again.

| Specification | BMI323 | ICM-20602 |
|--------------|---------|----------|
| Sensor Type | 6-Axis IMU | 6-Axis IMU |
| Accelerometer Range | ±2g, ±4g, ±8g, ±16g | ±2g, ±4g, ±8g, ±16g |
| Gyroscope Range | ±125, ±250, ±500, ±1000, ±2000 °/s | ±250, ±500, ±1000, ±2000 °/s |
| Resolution | 16-bit | 16-bit |
| Gyro Noise Density | ~0.007 °/s/√Hz | **0.004 °/s/√Hz** |
| Accel Noise Density | ~180 µg/√Hz | **100 µg/√Hz** |
| Max Gyro ODR | 6.4 kHz | **8 kHz** |
| Max Accel ODR | 6.4 kHz | 4 kHz |
| FIFO Size | **2 KB** | 1 KB |
| Interfaces | SPI, I²C, I3C | SPI, I²C |
| Supply Voltage | 1.71–3.6 V | 1.71–3.45 V |
| Power Consumption | Lower | Higher |
| Package Size | 2.5 × 3.0 mm | 3.0 × 3.0 mm |
| Release Era | Modern | Older |
| Drone Usage | Limited | Widely Used |
| ESP32 Compatibility | Yes | Yes |

<img width="250" alt="28f02160-13c6-4550-bb51-76e5383b8505" src="https://github.com/user-attachments/assets/46dea2b2-487e-477b-b9cd-f5dcda65f1d9" />




  
