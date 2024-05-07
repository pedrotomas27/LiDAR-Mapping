## 1. Build

### 1.1 Docker Container

The docker-based standard development environment is available at https://github.com/zijiechenrobotics/ig_lio_workspace

### 1.2 Build from source

#### 1.2.1 Prerequisites

:one: **Ubuntu and ROS**

Ubuntu >= 18.04. And Ubuntu 20.04 is recommended.

:two: **GCC & G++ (only for Ubuntu 18.04)**

gcc & g++ >= 9

:three: **TBB (only for Ubuntu 18.04)**

TBB >= 2020. Please follow https://github.com/oneapi-src/oneTBB

:four: **livox_ros_driver**

```bash
git clone https://github.com/Livox-SDK/Livox-SDK
cd Livox-SDK
mkdir build
cd build
cmake ..
make -j
sudo make install
```

:five: **glog**

```bash
sudo apt-get install -y libgoogle-glog-dev
```

#### 1.2.2 Build

```bash
cd <your workspace>
mkdir src
cd src
git clone https://github.com/pedrotomas27/ig_lio
git clone https://github.com/Livox-SDK/livox_ros_driver
cd ..
catkin_make
```


#### 2. Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
 
    
    -Run the launch file:
    
    -roslaunch ig_lio lio_velodyne_m1600.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

For Bpearl:

     Download Bpearl dataset [https://hilti-challenge.com/dataset-2023.html] Site 2 	Robot 	Floor 1 Large room
    
   
    -Run the launch file:
    
    -roslaunch ig_lio BPEarl.launch 
    
    -Play the bag file:
    
    -rosbag play bagfile
    
For Livox MID70:

     Download Livox MID70 dataset [https://hilti-challenge.com/dataset-2021.html] Construction Site Outdoor 1
    
    -Run the launch file:
    
    -roslaunch ig_lio lio_MID70.launch
    
    -Play the bag file:
    
    -rosbag play bagfile



    
