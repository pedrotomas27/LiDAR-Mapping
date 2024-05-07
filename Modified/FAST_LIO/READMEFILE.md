## Getting Started

To get started with LIO_SAM_6AXIS, follow these steps:

1. Clone the repository:

```bash
git clone https://github.com/JokerJohn/LIO_SAM_6AXIS.git

```

2. Install the dependencies:

 [ROS](http://wiki.ros.org/ROS/Installation) (tested with Kinetic and Melodic. Refer to [#206](https://github.com/TixiaoShan/LIO-SAM/issues/206) for Noetic)
  ```
  sudo apt-get install -y ros-kinetic-navigation
  sudo apt-get install -y ros-kinetic-robot-localization
  sudo apt-get install -y ros-kinetic-robot-state-publisher
  ```
- [gtsam](https://gtsam.org/get_started/) (Georgia Tech Smoothing and Mapping library)
  ```
  sudo add-apt-repository ppa:borglab/gtsam-release-4.2
  sudo apt install libgtsam-dev libgtsam-unstable-dev
```bash
cd LIO_SAM_6AXIS
catkin build
```

3. Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
   
    
    -Run the launch file:
    
    roslaunch lio_sam_6axis test_m1600.launch


    
