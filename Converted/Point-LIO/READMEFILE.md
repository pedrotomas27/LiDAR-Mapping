# **1. Prerequisites**

## **1.1 Ubuntu and [ROS](https://www.ros.org/)**
We tested our code on Ubuntu18.04 with ros melodic and Ubuntu20.04 with noetic. Additional ROS package is required:
```
sudo apt-get install ros-xxx-pcl-conversions
```

## **1.2 Eigen**
Following the official [Eigen installation](eigen.tuxfamily.org/index.php?title=Main_Page), or directly install Eigen by:
```
sudo apt-get install libeigen3-dev
```

## **1.3 livox_ros_driver**
Follow [livox_ros_driver Installation](https://github.com/Livox-SDK/livox_ros_driver).

*Remarks:*
- Since the Point-LIO supports Livox serials LiDAR, so the **livox_ros_driver** must be installed and **sourced** before run any Point-LIO luanch file.
- How to source? The easiest way is add the line ``` source $Licox_ros_driver_dir$/devel/setup.bash ``` to the end of file ``` ~/.bashrc ```, where ``` $Licox_ros_driver_dir$ ``` is the directory of the livox ros driver workspace (should be the ``` ws_livox ``` directory if you completely followed the livox official document).

## 2. Build
Clone the repository and catkin_make:

```
    cd ~/$A_ROS_DIR$/src
    git clone https://github.com/hku-mars/Point-LIO.git
    cd Point-LIO
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


Configuration

    Add the following files to the config directory: MID70.yaml, velody16BPC.yaml, velody16M1600C.yaml
    Add the following launch files to the launch directory: mapping_MID70.launch, mapping_velody16BPC.launch, mapping_velody16M1600C.launch
    
Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
    
    -Run the converter
    
    -Run the launch file:
    
    -roslaunch point_lio mapping_velody16M1600C.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

For Bpearl:

     Download Bpearl dataset [https://hilti-challenge.com/dataset-2023.html] Site 2 	Robot 	Floor 1 Large room
    
    -Run the converter

    -Run the launch file:
    
    -roslaunch point_lio mapping_velody16BPC.launch
    
    -Play the bag file:
    
    -rosbag play bagfile
    
For Livox MID70:

     Download Livox MID70 dataset [https://hilti-challenge.com/dataset-2021.html] Construction Site Outdoor 1
    
    -Run the launch file:
    
    -roslaunch point_lio mapping_MID70.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

