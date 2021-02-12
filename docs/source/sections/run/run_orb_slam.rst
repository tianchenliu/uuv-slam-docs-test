Run ORB SLAM
=================


Test: ::

    ./Examples/Monocular/mono_tum Vocabulary/ORBvoc.txt /media/tliu/WD_PassPort_1/slam_datasets/self/gopro.yaml /media/tliu/WD_PassPort_1/slam_datasets/self/nbrf/set1


Run ORB SLAM in ROS
---------------------

Stereo Mode Example

Tab 1 ::

    roscore

Tab 2 ::

    rosrun ORB_SLAM2 Stereo Vocabulary/ORBvoc.txt Examples/Stereo/EuRoC.yaml true

Tab 3 ::

    rosbag play --pause /media/tliu/WD_PassPort_1/slam_datasets/EuRoC/V1_01_easy.bag /cam0/image_raw:=/camera/left/image_raw /cam1/image_raw:=/camera/right/image_raw

Enter space after reading in rosbag info

