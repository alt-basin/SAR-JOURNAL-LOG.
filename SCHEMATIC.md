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

  here are the links for the sensors and stuff
   - https://shopee.ph/product/933050849/26220013460?d_id=665be&uls_trackid=55tbhe3r02fa&utm_content=4B6UvNMwYFsYjngtwRRPe7ygZQL7
   - https://shopee.ph/product/1032050598/22974977435?d_id=665be&rModelId=29401872399&uls_trackid=55tbhrg500c9&utm_content=4B6UvNMwYG7zeCY1TZ1jQJtB12tF
   - https://shopee.ph/product/56540719/23154817594?d_id=665be&rModelId=225632712882&uls_trackid=55tbhuhe00ee&utm_content=4B6UvNMwYGAsUJDXUgrRfQpPxLrb
   - https://shopee.ph/product/1538176896/43426280197?d_id=665be&rModelId=435101552007&uls_trackid=55tbi1jt02fa&utm_content=4B6UvNMwYGDiyaxJLcSYjr8GmYUP
   - https://shopee.ph/product/580325202/25288429666?d_id=665be&rModelId=139141964813&uls_trackid=55tbi5i500ca&utm_content=4B6UvNMwYGGiNivNa4zPTo6BQm5H

  by the way heres the battery
   - https://shopee.ph/product/1729536151/57358540563?d_id=665be&rModelId=128464625546&uls_trackid=55tbic1603c9&utm_content=4B6UvNMwYGNBeaRxWx9MwH5XYdpK
  
