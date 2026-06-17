# 13/06/206 10:09 pm
 
 first ever log for the drone, i have already created the schematic, though i will need to continue creating the drones
 pcb to hold the parts which may take a long time. So lets start by discussing the parts of the drone

  im currently using a 
   - JMT X4 310MM X4M310L
   - Uangel X2807 1300Kv
   - 6s 5200mah XT60

<img width="1468" height="880" alt="7df4a46b-1eed-4ec3-b51c-5aaf73f997b2" src="https://github.com/user-attachments/assets/40fe4ef9-3b4f-493a-aecb-d6235808feec" />
<img width="1344" height="900" alt="e7acb897-12b7-4c4b-9561-0c1f1995207d" src="https://github.com/user-attachments/assets/5a8e8c9a-11cf-4d64-85b2-32eefddaecbe" />

 
# 14/06/2026 9:35 am
  
  Below me is the schematic for the drone, which includes the parts needed for it to be full automated, so lets start one by one.
  for this dorone i will be using a ESP32-S3-WROOM-N16R8-1 as the flight control, and i will be using a 45A esc 4-in-1.
  
   ### SENSORS:
    
   - MPU6050 - This will act as the imu of the drone, giving it access to the yaw, roll, ang pitch.
   - PMW3901 - This is an optical flow camera, which will provide the drone its velocity by visual feedback.
   - VL53L1X - This is a lidar sensor, which will help the drone know its altitude, though testing and showcasing will only be done indoors.
   - MLX90640BAB - This is the thermal camera, due to budget cuts im only gonna be using this.
   - 45A 4-in-1 esc 

  below me is the Schematic for the drone, this includes the connection for each sensor to function
  
<img width="605" height="562" alt="Screenshot 2026-06-11 200743" src="https://github.com/user-attachments/assets/af78e5a9-d560-40a3-a7d0-d05206c7846e" />

  
now currently i dont have any of these components, so here are the links were i browsed the products, 
and mind you they may also have a discount. These products are from shopee which is a common delivery app from my country.

Esc:

  - https://shopee.ph/product/933050849/26220013460?d_id=665be&uls_trackid=55tbhe3r02fa&utm_content=4B6UvNMwYFsYjngtwRRPe7ygZQL7

VL53L1X wth lid:

   - https://shopee.ph/product/1032050598/22974977435?d_id=665be&rModelId=29401872399&uls_trackid=55tbhrg500c9&utm_content=4B6UvNMwYG7zeCY1TZ1jQJtB12tF

MLX90640BAA

   - https://shopee.ph/product/56540719/23154817594?d_id=665be&rModelId=225632712882&uls_trackid=55tbhuhe00ee&utm_content=4B6UvNMwYGAsUJDXUgrRfQpPxLrb

PMW3901 
 
   - https://shopee.ph/product/1538176896/43426280197?d_id=665be&rModelId=435101552007&uls_trackid=55tbi1jt02fa&utm_content=4B6UvNMwYGDiyaxJLcSYjr8GmYUP

MPU-6050
  
   - https://shopee.ph/product/580325202/25288429666?d_id=665be&rModelId=139141964813&uls_trackid=55tbi5i500ca&utm_content=4B6UvNMwYGGiNivNa4zPTo6BQm5H

Battery: 

   - https://shopee.ph/product/1729536151/57358540563?d_id=665be&rModelId=128464625546&uls_trackid=55tbic1603c9&utm_content=4B6UvNMwYGNBeaRxWx9MwH5XYdpK

# 15/06/2026 8:28 pm 

  I just finished building the frame when the m3 nuts arrived, below me is the showcase
  in multiple angles.
  
  <img width="2048" height="1289" alt="c05a2e44-0346-4d8f-9d85-8e693a4ecb37" src="https://github.com/user-attachments/assets/f830b4bb-87ad-4105-bba7-587b4fd0105a" />
<img width="2048" height="1080" alt="51f45b0d-6c06-419b-8082-c667ce248333" src="https://github.com/user-attachments/assets/c1e46a0f-3564-4fb7-b8f5-38b5e1ce30d4" />
<img width="2048" height="1149" alt="b290c748-67dc-41cf-a960-94b504ee50dd" src="https://github.com/user-attachments/assets/c97fdf34-7f96-4b94-ab0f-5ec8b3d143d8" />

# 17/06/2026 8:21 pm

 - I decided to switch from the MPU6050 to a better IMU, the BMI323. This is mainly because it has lower drift and improved overall performance. I also considered using an ICM-series IMU, but most online stores currently do not have it available.

The main difference between the two is their sensor performance and accuracy, which includes improvements in noise levels, stability, and motion tracking reliability in the BMI323 compared to the MPU6050.

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


  
