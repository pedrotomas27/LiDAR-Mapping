IG Lio Workspace Setup Guide

This guide will help you set up the IG Lio Workspace on Ubuntu 18.04 or Ubuntu 20.04. Please make sure you have the necessary dependencies installed before proceeding.
Prerequisites

    Ubuntu version >= 18.04 (Ubuntu 20.04 is recommended)
    GCC & G++ version >= 9
    TBB version >= 2020 (Installation Guide)
    Livox ROS Driver (GitHub Repo)
    glog (libgoogle-glog-dev)

Installation Steps

1 -> Clone the Livox ROS Driver repository:
git clone https://github.com/Livox-SDK/Livox-SDK
cd Livox-SDK
mkdir build
cd build
cmake ..
make -j
sudo make install

2 -> Install glog:
sudo apt-get install -y libgoogle-glog-dev

3 -> Clone the IG Lio Workspace repository and download necessary scripts:
cd <your_workspace>
mkdir src
cd src
git clone https://github.com/zijiechenrobotics/ig_lio_workspace.git
git clone https://github.com/Livox-SDK/livox_ros_driver

4 -> Download convBP_VLP.py and convM1600_VLP.py scripts. Make them executable:
chmod +x convBP_VLP.py
chmod +x convM1600_VLP.py

5 -> Build the workspace:
cd ..
catkin_make

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
