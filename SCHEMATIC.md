# 13/06/206 10:09 pm
 
 first ever log for the drone, i have already created the schematic, though i will need to continue creating the drones
 pcb to hold the parts which may take a long time. So lets start by discussing the parts of the drone

  im currently using a 
   - JMT X4 310MM X4M310L
   - Uangel X2807 1300Kv
   - 6s 5200mah XT60

# 14/06/2026 9:35
  
  Below me is the schematic for the drone, which includes the parts needed for it to be full automated, so lets start one by one.
  for this dorone i will be using a ESP32-S3-WROOM-N16R8-1 as the flight control, and i will be using a 45A esc 4-in-1.
  
   ### SENSORS:
    
   - MPU6050 - This will act as the imu of the drone, giving it access to the yaw, roll, ang pitch.
   - PMW3901 - This is an optical flow camera, which will provide the drone its velocity by visual feedback.
   - VL53L1X - This is a lidar sensor, which will help the drone know its altitude, though testing and showcasing will only be done indoors.
   - MLX90640BAB - This is the thermal camera, due to budget cuts im only gonna be using this.
   - 45A 4-in-1 esc 

  below me is the Schematic for the drone, this includes the connection for each sensor to function
  
  ![Image](images/image1.png)
  
