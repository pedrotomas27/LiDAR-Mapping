FasterLIO is tested in Ubuntu 18.04 and Ubuntu 20.04. Please install the following libraries before compilation.

    ROS (melodic or noetic)
    glog: sudo apt-get install libgoogle-glog-dev
    eigen: sudo apt-get install libeigen3-dev
    pcl: sudo apt-get install libpcl-dev
    yaml-cpp: sudo apt-get install libyaml-cpp-dev

FasterLIO can be compiled by plain cmake or catkin_make. In Ubuntu 20.04, the compile step is relatively simple.

    Plain cmake

1 Use the following commands to build FasterLIO:

mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j4

Note: iVox type should be specified by cmake at compile time. By default we will use linear iVox. Use cmake .. -DWITH_IVOX_NODE_TYPE_PHC=ON to build the FasterLIO with PHC iVox.

    catkin_make

2 Clone this repository to your catkin workspace, e.g., ~/catkin_ws/src, then use catkin_make instead of the above cmake commands. You can also specify the iVox type in catkin_make parameters.

After the compilation, you will get the a libfaster_lio.so and two executable files. If you choose plain cmake build, they will be located in ./build/devel/lib/faster_lio. If you use catkin_make, you could run them with rosrun and roslaunch.

3 -> Download convBP_VLP.py and convM1600_VLP.py scripts. Make them executable:

    chmod +x convBP_VLP.py
    chmod +x convM1600_VLP.py

4 -> Build the workspace:

    cd ..
    catkin_make

Configuration

    Add the following files to the config directory: velodyne_BPC.yaml, velodyne_M1600C.yaml
    Add the following launch files to the launch directory: mapping_velodyneBPC.launch, mapping_velodyneM1600C.launch
    
Running:
For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
    
    -Run the converter
    
    -Run the launch file:
    
    -roslaunch faster_lio mapping_velodyneM1600C.launch
    
    -Play the bag file:
    
    -rosbag play bagfile

For Bpearl:

     Download Bpearl dataset [https://hilti-challenge.com/dataset-2023.html] Site 2 	Robot 	Floor 1 Large room
    
    -Run the converter

    -Run the launch file:
    
    -roslaunch faster_lio mapping_velodyneBPC.launch
    
    -Play the bag file:
    
    -rosbag play bagfile
    

