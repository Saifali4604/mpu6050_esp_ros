# mpu6050_esp_ros
## Install Arduino IDE Latest Version 
 download Arduino IDE 2 appimage file from [https://downloads.arduino.cc/arduino-ide/arduino-ide_2.2.1_Linux_64bit.AppImage] 
 
 Then right click on the downloaded file / properties / permissions  select allow executing file system.
 
## Dependency for arduino
  ```
  sudo apt-get update
  sudo apt-get install ros-noetic-rosserial-arduino
  sudo apt-get install ros-noetic-rosserial
  sudo apt-get install ros-noetic-serial
 ```
create a libraries folder inside arduino folder and then
  ```
  cd ~/Arduino/libraries
  rosrun rosserial_arduino make_libraries.py <path of arduino libraries>
  ```

## Install

Use the following commands to download and compile the package.

```
mkdir -p ~/IMU/src
cd ~/IMU/src
git clone https://github.com/Saifali4604/mpu6050_esp_ros && rm -f Arduino/libraries/ros_lib/ros.h && rm -f Arduino/libraries/ros_lib/ArduinoHardware.h && cd IMU/src/ros_mpu6050_arduino/ && cp ros.h Arduino/libraries/ros_lib/ && cp Arduinohardware.h Arduino/libraries/ros_lib/
```

now open new terminal 
```
cd ~/IMU
catkin_make
gedit ~/.bashrc
```
and paste ```source ~/< work_space >/devel/setup.bash``` at the last line
## Arduino code
Connect Your Arduino with mpu6050 board to your PC And upload the code given in this repository.
**Download Mpu6050 lib by Electronicscat**(https://github.com/ElectronicCats/mpu6050)
```
sudo ls -l /dev/ttyACM* 
sudo chmod 777 /dev/ttyACM0
```
or
```
ls -l /dev |grep ttyUSB
sudo chmod 777 /dev/ttyUSB0
```
**Note:** Always use Serial.begin(115200) in the code

## Run the package
1. Start the ROS master
```
roscore
```
2. Run the launch file:
```
roslaunch mpu6050_esp_ros demo.launch
```
