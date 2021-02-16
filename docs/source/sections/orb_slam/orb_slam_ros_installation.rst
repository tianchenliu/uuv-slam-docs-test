ORB SLAM ROS Installation
=============================

Code: ::

    mkdir ros_slam_ws1
    cd ros_slam_ws1

    mkdir src
    cd src
    catkin_init_workspace 

    cd ..
    catkin_make
    cd src
    git clone https://github.com/tianchenliu/ORB_SLAM2
    git clone https://github.com/stevenlovegrove/Pangolin

    cd Pangolin
    mkdir build
    cd build
    cmake ..
    make
    sudo make install
    cd ..

    cd eigen-3.2.10/
    mkdir build
    cd build
    cmake ..
    sudo make install
    cd ..

    cd ~/ros_slam_ws1/src/ORB_SLAM2/Thirdparty/DBoW2/
    mkdir build
    cd build
    cmake .. -DCMAKE_BUILD_TYPE=Release
    make

    cd ~/ros_slam_ws1/src/ORB_SLAM2/Thirdparty/g2o/
    mkdir build
    cd build
    cmake .. -DCMAKE_BUILD_TYPE=Release
    make

    cd ~/ros_slam_ws1/src/ORB_SLAM2
    mkdir build
    cd build
    cmake .. -DROS_BUILD_TYPE=Release
    make

