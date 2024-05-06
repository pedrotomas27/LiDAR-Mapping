# Light-LOAM
News: Our paper has been accepted by the RA-L journal! 
This is the implementation for the Paper ``Light-LOAM: A Lightweight LiDAR Odometry and Mapping based on Graph-Matching''. This code is modified from [A-LOAM](https://github.com/HKUST-Aerial-Robotics/A-LOAM).

## Requirements
* PCL
* ROS
* ceres

## Introduction
This is the beta version, and the final implementation code is coming soon. The research paper [Light-LOAM: A Lightweight LiDAR Odometry and Mapping based on Graph-Matching](https://arxiv.org/abs/2310.04162) is now availble on arXiv.

Download convBP_VLP.py and convM1600_VLP.py scripts. Make them executable:

   
    chmod +x convM1600_VLP.py


    
Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
    
    -Run the converter
    
    -Run the launch file:
    
    -roslaunch light_loam aloam_velodyne_VLP_16.launch 
    
    -Play the bag file:
    
    -rosbag play bagfile


    
