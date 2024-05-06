## 1. Prerequisites
### 1.1 **Ubuntu** and **ROS**
Ubuntu 64-bit 16.04 or 18.04.
ROS Kinetic or Melodic. [ROS Installation](http://wiki.ros.org/ROS/Installation)


### 1.2. **Ceres Solver**
Follow [Ceres Installation](http://ceres-solver.org/installation.html).

### 1.3. **PCL**
Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).


## 2. Build A-LOAM
Clone the repository and catkin_make:

```
    cd ~/catkin_ws/src
    git clone https://github.com/HKUST-Aerial-Robotics/A-LOAM.git
    If you are using Noetic please check : https://github.com/TixiaoShan/LIO-SAM/issues/206
    Download convBP_VLP.py and convM1600_VLP.py scripts. Make them executable:
    chmod +x convBP_VLP.py
    chmod +x convM1600_VLP.py
    cd ../
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```


## 3.Configuration

    
    Add the following launch files to the launch directory: aloam_velodyne_VLP_16M1600C.launch
    
Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
    
    -Run the converter
    
    -Run the launch file:
    
    -roslaunch aloam_velodyne aloam_velodyne_VLP_16M1600C.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

For the rest of the LiDAR's im yet to get better results

    
