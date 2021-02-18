Kimera-VIO
====================

Github: https://github.com/MIT-SPARK/Kimera-VIO

Installation
---------------

Code: ::

    sudo apt-get update
    sudo apt-get install -y --no-install-recommends apt-utils
    sudo apt-get install -y cmake
    sudo apt-get install -y libboost-all-dev

    # (libvtk5-dev, libgtk2.0-dev in ubuntu 16.04)
    sudo apt-get install -y \
      build-essential unzip pkg-config \
      libjpeg-dev libpng-dev libtiff-dev \
      libvtk6-dev \
      libgtk-3-dev \
      libparmetis-dev \
      libatlas-base-dev gfortran

Install GTSAM: ::

    sudo apt-get install libtbb-dev
    git clone https://github.com/borglab/gtsam.git
    cd gtsam
    mkdir build
    cd build
    cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DCMAKE_BUILD_TYPE=Release -DGTSAM_USE_SYSTEM_EIGEN=OFF -DGTSAM_POSE3_EXPMAP=ON -DGTSAM_ROT3_EXPMAP=ON -DGTSAM_TANGENT_PREINTEGRATION=OFF ..
    # run unit tests
    make -j $(nproc) check
    sudo make -j $(nproc) install

Install OpenCV: ::

    git clone https://github.com/opencv/opencv.git
    cd opencv
    git checkout tags/3.3.1
    mkdir build
    cd build
    cmake -DWITH_VTK=On .. # Use -DWITH_TBB=On if you have TBB
    sudo make -j $(nproc) install


Install OpenGV: ::

    git clone https://github.com/laurentkneip/opengv.git
    cd opengv
    mkdir build
    cd build
    # Replace path to your GTSAM's Eigen
    cmake .. -DEIGEN_INCLUDE_DIR=/home/tliu/kimera_ws/gtsam/gtsam/3rdparty/Eigen -DEIGEN_INCLUDE_DIRS=/home/tliu/kimera_ws/gtsam/gtsam/3rdparty/Eigen
    sudo make -j $(nproc) install

Install DBoW2: ::

    git clone https://github.com/dorian3d/DBoW2.git
    cd DBoW2
    mkdir build
    cd build
    cmake ..
    sudo make -j $(nproc) install

Install Kimera-RPGO: ::

    git clone https://github.com/MIT-SPARK/Kimera-RPGO.git
    cd Kimera-RPGO
    mkdir build
    cd build
    cmake ..
    sudo make -j $(nproc)

Glog, Gflags: ::

    sudo apt-get install libgflags-dev libgoogle-glog-dev

Install Kimera-VIO: ::

    git clone https://github.com/MIT-SPARK/Kimera-VIO.git
    cd Kimera-VIO
    mkdir build
    cd build
    cmake ..
    make -j $(nproc)

(For docker installation, check https://github.com/MIT-SPARK/Kimera-VIO/blob/master/docs/kimera_vio_install.md)

Error: /home/tliu/kimera_ws/Kimera-VIO/build/testKimeraVIO: error while loading shared libraries: libmetis-gtsam.so: cannot open shared object file: No such file or directory

Solution: ::

    sudo cp /usr/local/lib/libmetis-gtsam.so /usr/lib


Run
---------

Code: ::

    cd Kimera-VIO
    bash ./scripts/euroc/yamelize.bash -p /media/tliu/WD_PassPort_1/slam_datasets/EuRoC
    
Run: ::

    cd Kimera-VIO
    bash ./scripts/stereoVIOEuroc.bash -p "/media/tliu/WD_PassPort_1/slam_datasets/EuRoC/V1_01_easy"

or directly by: ::

    ./build/stereoVIOEuroc


Installation Kimera-VIO-ROS
-----------------------------

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

