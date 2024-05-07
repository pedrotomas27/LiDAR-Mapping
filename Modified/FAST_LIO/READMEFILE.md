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


## 2. Build
If you want to use docker conatiner to run fastlio2, please install the docker on you machine.
Follow [Docker Installation](https://docs.docker.com/engine/install/ubuntu/).
### 2.1 Docker Container
User can create a new script with anyname by the following command in linux:
```
touch <your_custom_name>.sh
```
Place the following code inside the ``` <your_custom_name>.sh ``` script.
```
#!/bin/bash
mkdir docker_ws
# Script to run ROS Kinetic with GUI support in Docker

# Allow X server to be accessed from the local machine
xhost +local:

# Container name
CONTAINER_NAME="fastlio2"

# Run the Docker container
docker run -itd \
  --name=$CONTAINER_NAME \
  --user mars_ugv \
  --network host \
  --ipc=host \
  -v /home/$USER/docker_ws:/home/mars_ugv/docker_ws \
  --privileged \
  --env="QT_X11_NO_MITSHM=1" \
  --volume="/etc/localtime:/etc/localtime:ro" \
  -v /dev/bus/usb:/dev/bus/usb \
  --device=/dev/dri \
  --group-add video \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  --env="DISPLAY=$DISPLAY" \
  kenny0407/marslab_fastlio2:latest \
  /bin/bash
```
execute the following command to grant execute permissions to the script, making it runnable:
```
sudo chmod +x <your_custom_name>.sh
```
execute the following command to download the image and create the container.
```
./<your_custom_name>.sh
```

*Script explanation:*
- The docker run command provided below creates a container with a tag, using an image from Docker Hub. The download duration for this image can differ depending on the user's network speed.
- This command also establishes a new workspace called ``` docker_ws ```, which serves as a shared folder between the Docker container and the host machine. This means that if users wish to run the rosbag example, they need to download the rosbag file and place it in the ``` docker_ws ``` directory on their host machine.
- Subsequently, a folder with the same name inside the Docker container will receive this file. Users can then easily play the file within Docker.
- In this example, we've shared the network of the host machine with the Docker container. Consequently, if users execute the ``` rostopic list ``` command, they will observe identical output whether they run it on the host machine or inside the Docker container."
### 2.2 Build from source
Clone the repository and catkin_make:

```
    cd ~/$A_ROS_DIR$/src
    git clone https://github.com/hku-mars/FAST_LIO.git
    cd FAST_LIO
    git submodule update --init
    cd ../..
    catkin_make
    source devel/setup.bash
```
- Remember to source the livox_ros_driver before build (follow 1.3 **livox_ros_driver**)
- If you want to use a custom build of PCL, add the following line to ~/.bashrc
```export PCL_ROOT={CUSTOM_PCL_PATH}```
## 3. Directly run
Noted:

A. Please make sure the IMU and LiDAR are **Synchronized**, that's important.

B. The warning message "Failed to find match for field 'time'." means the timestamps of each LiDAR points are missed in the rosbag file. That is important for the forward propagation and backwark propagation.

C. We recommend to set the **extrinsic_est_en** to false if the extrinsic is give. As for the extrinsic initiallization, please refer to our recent work: [**Robust Real-time LiDAR-inertial Initialization**](https://github.com/hku-mars/LiDAR_IMU_Init).


For Velodyne M1600:

     Download Velodyne M1600 dataset [https://zenodo.org/records/7913307] 2_human_walking_illuminated_2023-01-23-001.zip
   
    
    -Run the launch file:
    
    -roslaunch fast_lio mapping_velodyneM1600.launch
    
    -Run the bagfile


    
