# mpu6050_esp_ros
## 1. Install Arduino IDE Latest Version 
## 1.1
 **download Arduino IDE** 
 appimage file from [https://downloads.arduino.cc/arduino-ide/arduino-ide_2.2.1_Linux_64bit.AppImage]
 
 Then right click on the downloaded **file > properties > permissions  select allow executing file system**.

## 1.2
 **open file >  preference > url 
 paste the below links
 https://arduino.esp8266.com/stable/package_esp8266com_index.json
 https://dl.espressif.com/dl/package_esp32_index.json**

 ## 1.3
 Open Board Manager > search for ESP32 > Download 

 ## 1.4
 open Library Manager > search **Mpu6050 lib by Electronicscat** and download it.
 
## Dependency for arduino
  ```
  sudo apt-get update
  sudo apt-get install ros-noetic-rosserial-arduino
  sudo apt-get install ros-noetic-rosserial
  sudo apt-get install ros-noetic-serial
  cd ~/Arduino/libraries
  rosrun rosserial_arduino make_libraries.py <path of arduino libraries>
  ```

## Install

Use the following commands to download and compile the package.

```
mkdir -p ~/IMU/src
cd ~/IMU/src
git clone https://github.com/Saifali4604/mpu6050_esp_ros && rm -f Arduino/libraries/ros_lib/ros.h && rm -f Arduino/libraries/ros_lib/ArduinoHardware.h && cd ~/IMU/src/mpu6050_esp_ros && cp ros.h ~/Arduino/libraries/ros_lib/ && cp ArduinoHardware.h ~/Arduino/libraries/ros_lib/
```

now open new terminal 
```
cd ~/IMU
catkin_make
gedit ~/.bashrc
```
and paste ```source ~/IMU/devel/setup.bash``` at the last line

## Arduino code

Connect Your Arduino with mpu6050 board to your PC And upload the code given in this repository.
```
sudo ls -l /dev/ttyACM* 
sudo chmod 777 /dev/ttyACM0
```
or
```
ls -l /dev |grep ttyUSB
sudo chmod 777 /dev/ttyUSB0
```
change the com port 
```
gedit ~/IMU/src/mpu6050_esp_ros/launch/demo.launch
```


## Run the package

1. Run the launch file:
```
roslaunch mpu6050_esp_ros demo.launch
```
