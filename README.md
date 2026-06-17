# SAR-JOURNAL-LOG.
this is were the drones summary of documentation will be located, be reminded that we would be using this prototype for our schools research
## documentation 
  ### PROJECT OVERVIEW

  - The goal of this project is to develop a prototype autonomous Search and Rescue (SAR) drone for outdoor disaster scenarios such as earthquakes, landslides, and       floods.

    The system is designed to assist in search operations by capturing aerial data and detecting heat signatures using a thermal camera. This can help identify           potential human presence in outdoor environments with reduced visibility, such as nighttime conditions, smoke, or partially obstructed areas.

    The drone combines thermal imaging with optical flow, an IMU, and a distance sensor to maintain stable flight and estimate motion during flight. It is intended       as a demonstration of how low-cost robotics systems can support SAR-style exploration and situational awareness.

 ### HARDWARE OVERVIEW / BILL OF MATERIALS
 Here is the list of the hardware i plan to use, it may also be used as the bill of materials.

| Component | Quantity | Purpose | Link                         |
|-----------|:--------:|---------|------------------------------|
| BMI323 | 1 | IMU | https://s.lazada.com.ph/s.Zg2ofY?c=v&t=p-iGrr7H6-s2LBxeDM |
| PMW3901 | 1 | Optical Flow | https://shopee.ph/product/1538176896/43426280197 |
| VL53L1X + lid | 1 | Altitude Sensor | https://shopee.ph/product/1032050598/22974977435 |
| MLX90640BAA | 1 | Thermal Camera | https://shopee.ph/product/56540719/23154817594 |
| 45A 4-in-1 Esc | 1 | ESC |  https://shopee.ph/product/933050849/26220013460 |
| 4s 3200mah 60c LiPo | 1 | Battery |  https://shopee.ph/product/933050849/26220013460 |

### SYSTEM OVERVIEW

**Perception system**

*Inputs*

 - **(IMU) BMI323** - Will be used as the sensor to determine the Yaw, Roll, and Pitch of the drone, <br>
   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;As well the movement of the drone by using its built in accelometer.
   
 - **(OPTICAL FLOW) PMW3901** - Will be used as the sensor for the drone to be able to determine its velocity mid air.

 - **(LIDAR SENSOR) VL53L1X** - This will serve as the main sensor for the drone to know its current altitude,<br>
   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;though this sensor is weak outdoors, testing and showcasing would be done indoors.

 - **(THERMAL CAMERA/IR CAMERA) MLX90640** - This would be used as the camera for mapping the area in thermal images.
 
*What this subsystem does:*

 - Collects raw data
 - Filters noise
 - Syncs timestamps
