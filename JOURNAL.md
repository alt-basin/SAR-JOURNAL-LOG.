# DEVLOG #001: INTRODUCTION

 **Total Time Spent: 5 minutes** pre-repo work
 
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

 **Total Time Spent: 1 hour** pre-repo work

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

 **Total Time Spent: 17 minutes** 

 - The drone frame assembly was completed after the M3 nuts arrived. Below is a showcase of the finished frame from multiple angles.
  
  <img width="2048" height="1289" alt="c05a2e44-0346-4d8f-9d85-8e693a4ecb37" src="https://github.com/user-attachments/assets/f830b4bb-87ad-4105-bba7-587b4fd0105a" />
<img width="2048" height="1080" alt="51f45b0d-6c06-419b-8082-c667ce248333" src="https://github.com/user-attachments/assets/c1e46a0f-3564-4fb7-b8f5-38b5e1ce30d4" />
<img width="2048" height="1149" alt="b290c748-67dc-41cf-a960-94b504ee50dd" src="https://github.com/user-attachments/assets/c97fdf34-7f96-4b94-ab0f-5ec8b3d143d8" />

---
# DEVLOG #004: INTRODUCTION FOR BMI323


 **Total Time Spent: 5 minutes**

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

**Total Time Spent: 10 minutes**

 - So i just created the new schematic for the drone which included the new IMU (BMI323).
   so the reason why I didnt do this yesterday is because i had assignments, and also i was lazy.

   it took around 4 mins to create the new symbol for the imu since i was trying to find the exact board model
   in a datasheet though i found the model by a youtube video. Which also described how to use it.

  <img width="471" height="437" alt="Screenshot 2026-06-20 142921" src="https://github.com/user-attachments/assets/656dd6a2-f679-4263-9131-98dd4fc3c475" />
  <img width="471" height="437" alt="Screenshot 2026-06-20 143220" src="https://github.com/user-attachments/assets/d3b06de2-813e-4c4f-b145-ca3735b05715" />

https://github.com/alt-basin/SAR-JOURNAL-LOG./blob/main/Schematics%2BPCB/Schematic_drone.pdf

---

# DEVLOG #006: MEASUREMENTS FOR PCB

**Duration: 26 minutes 28 seconds**

- I decided to measure the drone frame (shown below) so I can use it as a reference for the PCB's shape, which will host the ESP32-S3-WROOM-1, IMU (Inertial   Measurement Unit), and other components.

  Right now, I am only preparing the measurements for the PCB since it will be mounted directly onto the frame. I am also waiting for the sensors to arrive so I can measure their pin layouts and dimensions accurately. I believe it is better to rely on measurements taken from the actual physical components rather than using dimensions from online sources.

  Here are the measurements.

  <img width="480" alt="34cc6814-a46b-4476-9909-0267edcaa080" src="https://github.com/user-attachments/assets/2fa67dbd-bcc2-4e36-bfd9-b222d9bc8efa" />
  <img width="370.75" alt="341fd21e-3ca5-4c1e-b4bd-874106287189" src="https://github.com/user-attachments/assets/6a432389-2464-4d20-86c1-fc179580ab7e" />

 - I just wanted to show this to you since I currently have assignments to work on, and I won't be able to create the <br> actual measurements in a 3D model yet. I may have to work on it during the weekend.

---

# DEVLOG #007: UPDATE FOR REPO AND NEW SENSOR

**Total Time Spent: 1 hour 29 mins 54 seconds**

- So since I dont have any assignments today, i decided to create a data table for each sensor. So you could know whats the capabilities, while doing so I realized that my current imu (which is BMI323), is weak. Not that its fully weak but for testing that uses autonomous programming, this would be a problem.

  Then i asked gpt for potential sensors that are better than the current (BMI323) and recommended me to use and ICM-42688-P, which is better over all. The main problem wasnt cost as i have it covered, the main problem is the market availability. Each shopping app basically have this type of sensor, the problem was that it was all out of stock.

**6:27 pm**

- I was talking with Gpt about the sensors to find the common and cheapest, which landed me on the ICM-20602. so comparing this with the current bmi323, here are the data table. Now even though it may just be like a point different from a bmi, i only want to switch as the bmi323 isnt really popular.

  now that i have decided what kind of sensor i will use, i should probably change the BOM first, then i will start on creating the new schematic again.
  i should probably just add the data tables for the sensors tommorow.

| Specification | BMI323 |  | ICM-20602 |
|---|---|---|---|
| Sensor Type | 6-Axis IMU | = | 6-Axis IMU |
| Accelerometer Range | ±2g, ±4g, ±8g, ±16g | = | ±2g, ±4g, ±8g, ±16g |
| Gyroscope Range | **±125, ±250, ±500, ±1000, ±2000 °/s** | > | *±250, ±500, ±1000, ±2000 °/s* |
| Resolution | 16-bit | = | 16-bit |
| Gyro Noise Density | *~0.007 °/s/√Hz* | < | **0.004 °/s/√Hz** |
| Accel Noise Density | *~180 µg/√Hz* | < | **100 µg/√Hz** |
| Max Gyro ODR | *6.4 kHz* | < | **8 kHz** |
| Max Accel ODR | **6.4 kHz** | > | *4 kHz* |
| FIFO Size | **2 KB** | > | *1 KB* |
| Interfaces | **SPI, I²C, I3C** | > | *SPI, I²C* |
| Supply Voltage | **1.71–3.6 V** | > | *1.71–3.45 V* |
| Power Consumption | **Lower** | > | *Higher* |
| Package Size | **2.5 × 3.0 mm** | > | *3.0 × 3.0 mm* |
| Release Era | **Modern** | > | *Older* |
| Drone Usage | *Limited* | < | **Widely Used** |
| ESP32 Compatibility | Yes | = | Yes |

<img width="250" alt="28f02160-13c6-4550-bb51-76e5383b8505" src="https://github.com/user-attachments/assets/46dea2b2-487e-477b-b9cd-f5dcda65f1d9" />

**8:05 pm**

- Here is the thing the schematic. i only keep chagning the schematic so i could have a visual guideline for the pcb.

<img width="250" alt="Screenshot 2026-06-25 200450" src="https://github.com/user-attachments/assets/91fa9381-10de-4739-8fd6-baaaf60da865" />
<img width="250" alt="Screenshot 2026-06-25 200708" src="https://github.com/user-attachments/assets/66f7e95b-cbd3-4dcd-9b42-64f16a564928" />


https://github.com/alt-basin/SAR-JOURNAL-LOG./blob/main/BOM.xlsx <br>
https://github.com/alt-basin/SAR-JOURNAL-LOG./blob/main/SCHEMATIC/SCHEMATIC.pdf

- hello its me again, now im not actually saying that the ICM 20602 is better than the BMI323, just that the specs arent really built for an automated drone. Even though the bmi wins by 8 that doesnt automatically guarentee that the imu its great. just that its for other projects not for mine.

---

# DEVLOG #008: FOOTPRINT

**Total Time Spent: 4 hours**

 - Hello! It's been a while since my last update because I've been swamped with schoolwork. During my free time, I decided to work on creating the PCB footprints for the custom board I'm designing.

   At the moment, the PCB isn't fully complete. I still need to add the through-hole solder pads so the board can be connected to the components properly. I wasn't able to accurately track the total amount of time I spent on this task since I was constantly switching between EasyEDA and Google Docs for documentation and planning. However, I'd estimate that I spent around **4 hours** working on it.

<img width="430" alt="Screenshot 2026-07-01 142828" src="https://github.com/user-attachments/assets/9b335d06-f7b8-4efe-8107-bc1da945436d" />
<img width="430" alt="Screenshot 2026-07-01 142834" src="https://github.com/user-attachments/assets/1e43e35d-237f-43e7-a166-ff3fbc56bb45" />

 - so probably im just going to add this to the pcb development file, but soon i will replace it with a more refined version with the through-hole solder pads.
   I re-synced all of my project files and didn't realize it would reset their timestamps.

   also be minded this is my first time making a footprint, so i dont really know if its bad or not

---

# DEVLOG #009: idk

**Total Time Spent: 10 mins**

- While working on my PCB design yesterday, I realized that I had been using copper traces instead of the board outline. I corrected that mistake, so here's the updated version.

   I'm also writing today's devlog a bit earlier because I forgot to do it yesterday, and I really want to get to sleep early since I only got around three hours of sleep. I also had to attend the birthday celebration of a family friend today, which took up most of my evening.
   
   <img width="250" height="250" alt="Screenshot 2026-07-05 215957" src="https://github.com/user-attachments/assets/1a3bc900-93e3-4a5c-876f-9b4d25778429" />
   <img width="250" height="250" alt="Screenshot 2026-07-05 220011" src="https://github.com/user-attachments/assets/8fdc0f94-cc1d-4325-a87c-fbb13fd6c4ac" />
   <br>
   <img width="250" height="250" alt="Screenshot 2026-07-05 220023" src="https://github.com/user-attachments/assets/0f557cfe-b46c-4e6b-8c52-927cd76beb13" />
   <img width="250" height="250" alt="Screenshot 2026-07-05 220034" src="https://github.com/user-attachments/assets/4d5bcede-a662-4c4d-ac38-63da1ae563d8" />

- also, pcbdoc.

---

# DEVLOG #010: SCHEMATIC REFINING

**Total time spent: 4 mins**

- I also updated the schematic by adding a Mini560 buck converter. This allows the ESC to supply a stable regulated voltage to the microcontroller instead of powering it directly from the battery. The buck converter steps down the battery voltage to a level that is safe for the microcontroller and other low voltage electronics, improving the reliability and safety of the power distribution system.

<img width="713" height="737" alt="Screenshot 2026-07-09 220412" src="https://github.com/user-attachments/assets/0cf83e75-781d-4ee8-8baf-3c5f3e2fa02c" />

---

# DEVLOG #011: Motor Mounting Issue and Assembly Lesson

**Total time spent: 3 Minute**

<img width="1756" height="996" alt="5b88c2b6-0f94-4790-9b57-e16fb2b95f28" src="https://github.com/user-attachments/assets/135f9d00-3efa-4403-a635-288d64581544" />

*Figure X. Example of motor winding damage observed after assembly.
This image shows one example of the damage found on the brushless motors. While this motor shows visible copper wire damage, several other motors exhibited deeper cuts that were difficult to properly capture through photography due to their location and severity.*


- For future iterations, motor mounting depth will be checked before installation, and appropriate screw lengths will be selected to prevent interference with internal components.

  During the early assembly phase of the drone prototype, the motor mounting screws used were found to be longer than required. This caused the screws to contact the internal motor components, resulting in visible damage to the copper winding area of the brushless motors.

  Initial inspection was performed by comparing the phase resistance of each motor using a multimeter. The readings remained consistent across the motors, indicating that electrical continuity was maintained. However, this incident highlighted the importance of verifying hardware dimensions and screw length before mechanical assembly.

# DEVLOG #012: ADDRESSING THE DELAY

**Total time spent: 3 Minutes**

- Hello! The reason progress on the robot has been slower than expected is that I've been working on a detailed project analysis that will be reviewed by my teacher as part of my research project.

  Since my groupmates are not very experienced with robotics, I considered switching to a simpler project, the smartwatch prototype, which would require less complex programming. However, that project also presents a challenge. Its primary function is detecting hazardous gases, such as carbon monoxide, so I need to build a proof of concept by testing the sensors. To do that properly, I need to consult with an engineer from our main campus.

  Because of this, I am currently preparing the project overview and technical analysis to compare both projects and determine which one is the most feasible to pursue for our research.

  <img width="1918" height="897" alt="Screenshot 2026-07-18 144104" src="https://github.com/user-attachments/assets/a178a82b-c447-4c9b-907e-c201bb93f8d6" />


# DEVLOG #013: HEADSUP

**Total time spent: 1 Minute**

- Hello again, just be reminded I had to re-sync the entries because i had to add parsed time "Total time spent: 3 Minutes", since i thought it should be "duration: ". okay good bye.

  <img width="988" height="523" alt="Screenshot 2026-07-18 144424" src="https://github.com/user-attachments/assets/31c61a86-eef7-43de-a368-63fec3d63f68" />

 # DEVLOG #014: FENDERS FOR THE DRONE

 **Total time spent: 20 Minute**

<img width="798" height="601" alt="Screenshot 2026-07-20 183040" src="https://github.com/user-attachments/assets/ea012e89-df40-4098-8bd1-189017568df3" />
<img width="712" height="497" alt="Screenshot 2026-07-20 183047" src="https://github.com/user-attachments/assets/9a4da026-bcf5-4478-9e09-b34210ab0f20" />

*Figure X shows an example of Joseph Fraser's prop guard design. This design is particularly useful during testing because it helps protect the propellers from accidental impacts with walls, obstacles, or other objects during indoor flight. It also improves safety by reducing the risk of damage to both the drone and its surroundings, making it well suited for prototype development and testing.*

6:32 pm

- Hello! A while back, while working on my SAR drone, I realized that the entire research is mainly intended for indoor use. Because of that, I decided that adding prop guards would make the drone much safer during testing.

  At first, I planned to design and create my own prop guards. However, after considering my current schedule, I realized that it would take time away from more important parts of the project. I still need to revise the research paper, especially since the project overview will be reviewed by an engineer, so I want to make sure I use my time wisely.

  Because of this, I decided to use an open source prop guard design instead. This allows me to focus on completing the drone itself while still improving safety for indoor operation.

  The prop guard design I will be using was created by **Joseph Fraser**. You can find it here:

https://www.printables.com/model/465552-7-75-inch-fpv-drone-prop-guards-and-bumpers/files

- I would like to give full credit to Joseph Fraser for creating and sharing this design with the community.
