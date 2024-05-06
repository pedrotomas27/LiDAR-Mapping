FAST_LIO Workspace Setup Guide

This guide will help you set up the FAST_LIO Workspace on Ubuntu.
## 1. Prerequisites
### 1.1 **Ubuntu** and **ROS**
**Ubuntu >= 16.04**

For **Ubuntu 18.04 or higher**, the **default** PCL and Eigen is enough for FAST-LIO to work normally.

ROS    >= Melodic. [ROS Installation](http://wiki.ros.org/ROS/Installation)

### 1.2. **PCL && Eigen**
PCL    >= 1.8,   Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).

Eigen  >= 3.3.4, Follow [Eigen Installation](http://eigen.tuxfamily.org/index.php?title=Main_Page).

### 1.3. **livox_ros_driver**
Follow [livox_ros_driver Installation](https://github.com/Livox-SDK/livox_ros_driver).

*Remarks:*
- Since the FAST-LIO must support Livox serials LiDAR firstly, so the **livox_ros_driver** must be installed and **sourced** before run any FAST-LIO luanch file.
- How to source? The easiest way is add the line ``` source $Livox_ros_driver_dir$/devel/setup.bash ``` to the end of file ``` ~/.bashrc ```, where ``` $Livox_ros_driver_dir$ ``` is the directory of the livox ros driver workspace (should be the ``` ws_livox ``` directory if you completely followed the livox official document).
2.2 Build from source
Clone the repository and catkin_make:

```
    cd ~/$A_ROS_DIR$/src
    git clone https://github.com/hku-mars/FAST_LIO.git
    cd FAST_LIO
    git submodule update --init
    cd ..
    Download convBP_VLP.py and convM1600_VLP.py scripts. Make them executable:
    chmod +x convBP_VLP.py
    chmod +x convM1600_VLP.py
    cd ..
    catkin_make
    source devel/setup.bash
```
- Remember to source the livox_ros_driver before build (follow 1.3 **livox_ros_driver**)
- If you want to use a custom build of PCL, add the following line to ~/.bashrc
```export PCL_ROOT={CUSTOM_PCL_PATH}```
## 2. Directly run
Noted:

A. Please make sure the IMU and LiDAR are **Synchronized**, that's important.

B. The warning message "Failed to find match for field 'time'." means the timestamps of each LiDAR points are missed in the rosbag file. That is important for the forward propagation and backwark propagation.

C. We recommend to set the **extrinsic_est_en** to false if the extrinsic is give. As for the extrinsic initiallization, please refer to our recent work: [**Robust Real-time LiDAR-inertial Initialization**](https://github.com/hku-mars/LiDAR_IMU_Init).


Configuration

    Add the following files to the config directory: bg_velodyneBpearlC.yaml, bg_velodyneM1600C.yaml, MID70.yaml
    Add the following launch files to the launch directory: lio_MID70.launch, lio_bg_velodyneM1600C.launch, lio_bg_velodyneBPearlC.launch
    
Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
    
    -Run the converter
    
    -Run the launch file:
    
    -roslaunch ig_lio lio_bg_velodyneM1600C.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

For Bpearl:

     Download Bpearl dataset [https://hilti-challenge.com/dataset-2023.html] Site 2 	Robot 	Floor 1 Large room
    
    -Run the converter

    -Run the launch file:
    
    -roslaunch ig_lio lio_bg_velodyneBPearlC.launch
    
    -Play the bag file:
    
    -rosbag play bagfile
    
For Livox MID70:

     Download Livox MID70 dataset [https://hilti-challenge.com/dataset-2021.html] Construction Site Outdoor 1
    
    -Run the launch file:
    
    -roslaunch ig_lio lio_MID70.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

