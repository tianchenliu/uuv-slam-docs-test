Kimera-VIO-ROS
====================

Installation
---------------

Install ROS: ::

    sudo apt-get install ros-melodic-desktop-full
    echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
    source ~/.bashrc

    sudo apt install python-rosdep
    sudo rosdep init
    rosdep update

    sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential python-catkin-tools

ROS non-default dependencies for mesh_rviz_plugins: ::

    sudo apt-get install ros-melodic-image-geometry ros-melodic-pcl-ros ros-melodic-cv-bridge

System dependencies: ::

    sudo apt-get install -y --no-install-recommends apt-utils
    sudo apt-get install -y \
      cmake build-essential unzip pkg-config autoconf \
      libboost-all-dev \
      libjpeg-dev libpng-dev libtiff-dev \
    # Use libvtk5-dev, libgtk2.0-dev in ubuntu 16.04 \
      libvtk6-dev libgtk-3-dev \
      libatlas-base-dev gfortran \
      libparmetis-dev \
      python-wstool python-catkin-tools \

GTSAM's optional dependencies: ::

    sudo apt-get install libtbb-dev

KimeraVIO ROS wrapper
++++++++++++++++++++++

Code: ::

    mkdir -p ~/kimera_ws/src
    cd ~/kimera_ws/
    catkin init
    catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release
    catkin config --merge-devel
    # echo 'source ~/catkin_ws/devel/setup.bash' >> ~/.bashrc

    cd src
    git clone https://github.com/MIT-SPARK/Kimera-VIO-ROS.git

    wstool init
    wstool merge Kimera-VIO-ROS/install/kimera_vio_ros_https.rosinstall
    wstool update

    catkin build
    source ~/kimera_ws/devel/setup.bash


Current Issues
----------------

'catkin build': 1 package failed


Usage
----------

Example: Euroc rosbag

Tab 1 ::
    
    roscore

Tab 2 ::

    roslaunch kimera_vio_ros kimera_vio_ros_euroc.launch

Tab 3 ::

    rviz -d $(rospack find kimera_vio_ros)/rviz/kimera_vio_euroc.rviz

Tab 4 ::
    
    rosbag play --clock /media/tliu/WD_PassPort_1/slam_datasets/EuRoC/V1_01_easy.bag

If run rosbag offline ::

    roslaunch kimera_vio_ros kimera_vio_ros_euroc.launch online:=false rosbag_path:="PATH/TO/ROSBAG"

