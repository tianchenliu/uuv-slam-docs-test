Run ORB SLAM
=================


Test: ::

    ./Examples/Monocular/mono_tum Vocabulary/ORBvoc.txt /media/tliu/WD_PassPort_1/slam_datasets/self/gopro.yaml /media/tliu/WD_PassPort_1/slam_datasets/self/nbrf/set1


Run ORB SLAM in ROS
---------------------

Monocular Mode Example - Using Laptop/USB Camera

Download and install `USB Camera <https://github.com/bosch-ros-pkg/usb_cam/>`_ in src folder ::
    
    cd src/usb_cam
    mkdir build
    cd build
    cmake ..
    make

Edit device input (e.g., value="/dev/video0") for usb_cam-test.launch file

Edit ORB_SLAM2/Example/ROS/ORB_SLAM2/src/ros_mono.cc ::
    
    ros::Subscriber sub = nodeHandler.subscribe("/image/image_raw", 1, &ImageGrabber::GrabImage,&igb);

to ::
    
    ros::Subscriber sub = nodeHandler.subscribe("/usb_cam/image_raw", 1, &ImageGrabber::GrabImage,&igb);

Rebuild ::
    ./build_ros.sh

Run 

Tab 1 ::
    
    roscore

Tab 2 ::
    
    source devel/setup.bash
    roslaunch usb_cam usb_cam-test.launch
    
Tab 3 ::
    
    source devel/setup.bash
    rosrun ORB_SLAM2 Mono rosrun ORB_SLAM2 Mono src/ORB_SLAM2/Vocabulary/ORBvoc.txt src/ORB_SLAM2/Examples/Monocular/TUM1.yaml 


Plot ORB SLAM Trajectory Results

Install `evo <https://github.com/MichaelGrupp/evo/>`_ ::
    
    sudo pip install evo --upgrade --no-binary evo

Plot ::
    
    evo_traj tum KeyframeTrajectory.txt --plot



Stereo Mode Example

Tab 1 ::
    
    roscore

Tab 2 ::
    
    rosrun ORB_SLAM2 Stereo Vocabulary/ORBvoc.txt Examples/Stereo/EuRoC.yaml true

Tab 3 ::
    
    rosbag play --pause /media/tliu/WD_PassPort_1/slam_datasets/EuRoC/V1_01_easy.bag /cam0/image_raw:=/camera/left/image_raw /cam1/image_raw:=/camera/right/image_raw

Enter space after reading in rosbag info

