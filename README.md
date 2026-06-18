# SAR-JOURNAL-LOG.
this is were the drones summary of documentation will be located, be reminded that we would be using this prototype for our schools research
## documentation 
  ### PROJECT OVERVIEW:

  - The goal of this project is to develop a prototype autonomous Search and Rescue (SAR) drone for outdoor disaster scenarios such as earthquakes, landslides, and       floods.

    The system is designed to assist in search operations by capturing aerial data and detecting heat signatures using a thermal camera. This can help identify           potential human presence in outdoor environments with reduced visibility, such as nighttime conditions, smoke, or partially obstructed areas.

    The drone combines thermal imaging with optical flow, an IMU, and a distance sensor to maintain stable flight and estimate motion during flight. It is intended       as a demonstration of how low-cost robotics systems can support SAR-style exploration and situational awareness.

 ### HARDWARE OVERVIEW / BILL OF MATERIALS:
 
 - Here is the list of hardware planned for this project, which also serves as the Bill of Materials (BOM).

| Component | Quantity | Purpose | Link |
|-----------|:--------:|---------|------|
| BMI323 | 1 | IMU | https://s.lazada.com.ph/s.Zg2ofY?c=v&t=p-iGrr7H6-s2LBxeDM |
| PMW3901 | 1 | Optical Flow Sensor | https://shopee.ph/product/1538176896/43426280197 |
| VL53L1X + lid | 1 | Altitude Sensor (ToF) | https://shopee.ph/product/1032050598/22974977435 |
| MLX90640BAA | 1 | Thermal Infrared Camera | https://shopee.ph/product/56540719/23154817594 |
| 45A 4-in-1 ESC | 1 | Electronic Speed Controller | https://shopee.ph/product/933050849/26220013460 |
| 4S 3200mAh 60C LiPo | 1 | Power Battery | https://shopee.ph/product/1729536151/57358540563 |

### SYSTEM OVERVIEW:

**Perception system**
- This subsystem provides the drone’s perception and navigation capability for indoor search and rescue mapping. It combines motion sensing, position estimation, altitude measurement, and thermal imaging to allow controlled flight and environmental scanning in a confined area (2m × 2m).
  
| Component | Type | Purpose |
|-----------|------|--------|
| BMI323 | IMU (Inertial Measurement Unit) | Will be used as the sensor to determine the drone’s yaw, roll, and pitch, as well as its movement using the built-in accelerometer. |
| PMW3901 | Optical Flow Sensor | Will be used to determine the drone’s velocity in mid-air. |
| VL53L1X + lid | Time-of-Flight (ToF) Distance Sensor | This will serve as the main sensor for measuring the drone’s altitude. However, this sensor is weaker outdoors, so testing and demonstrations will be conducted indoors. |
| MLX90640BAA | Thermal Infrared Camera | This will be used to capture thermal images for mapping the environment. |
| 45A 4-in-1 ESC | Electronic Speed Controller | Controls motor speed and power distribution. |
| 4S 3200mAh 60C LiPo | Lithium Polymer Battery | Provides power to the entire drone system. |

 - Collects raw data
 - Filters noise
 - Syncs timestamps
**Control system**
- This subsystem 
