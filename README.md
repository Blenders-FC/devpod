# Developer container for BlendersFC
## Setup
1. Install nvidia drivers
```
sudo apt update
```
See recommended drivers for your system
```
ubuntu-drivers devices
```
```
sudo ubuntu-drivers autoinstall
```
or install directly recommended version
```
sudo apt install nvidia-driver-XXX
```

 
2. Install docker

Download [docker](https://docs.docker.com/engine/install/ubuntu/)

Setup [Nvidia Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

## Install
1. Download [devpod](https://devpod.sh/)
2. Clone this repo
3. Run in base dir of repo
```
devpod up .
```
5. Wait for build (takes a while) 
6. ssh blendersdevpod.devpod (should autocomplete with tab key)
## Tips and troubleshooting
1. If terminal looks like this
```
$
```
  and want to change it, run to change to bash terminal.
```
bash
``` 

2. If running
```
colcon build
```
   from ws fails with error: 
```
--- stderr: op3_online_walking_module_msgs CMake Error: 
The current CMakeCache.txt directory /home/ws/build/op3_online_walking_module_msgs/CMakeCache.txt 
is different than the directory /workspace/build/op3_online_walking_module_msgs where CMakeCache.txt was created. 
This may result in binaries being created in the wrong place. 
If you are not sure, reedit the CMakeCache.txt CMake Error: The source directory "/workspace/src/op3_msgs/op3_online_walking_module_msgs" does not exist.
```
  run and retry
```
rm -rf build install log
```
3. If your host machine dies during compilation, run this this flag
```
colcon build --executor sequential
```
4. Remember to:
```
source /opt/ros/humble/setup.bash
source install/setup.bash
```
  or to make it permanent
```
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
echo "source /home/ws/install/setup.bash" >> ~/.bashrc
```
5. To test installation with gazebo, run this
```
ros2 launch src/ROBOTIS-OP3-Simulations/op3_gazebo_ros2/launch/robot_sim.launch.py
```
