ORB SLAM Installation
======================

https://github.com/raulmur/ORB_SLAM2


Prerequisites
-----------------

* Pangolin
https://github.com/stevenlovegrove/Pangolin

* OpenCV
http://opencv.org

* Eigen3
http://eigen.tuxfamily.org


Building Library and Examples
-------------------------------
Download from GitHub :

    git clone https://github.com/raulmur/ORB_SLAM2.git ORB_SLAM2
    

Build ::
    
    cd ORB_SLAM2
    chmod +x build.sh
    ./build.sh

Fix compile issue, add ::

    #include <unistd.h> 

in System.h. 


Monocular Examples
---------------------------

Download a sequence from http://vision.in.tum.de/data/datasets/rgbd-dataset/download 
and uncompress it.

Execute the following command. Change TUMX.yaml to TUM1.yaml,TUM2.yaml or TUM3.yaml for freiburg1, freiburg2 and freiburg3 sequences respectively. Change PATH_TO_SEQUENCE_FOLDER to the uncompressed sequence folder. ::

    ./Examples/Monocular/mono_tum Vocabulary/ORBvoc.txt Examples/Monocular/TUMX.yaml PATH_TO_SEQUENCE_FOLDER

Quick test: ::

    ./Examples/Monocular/mono_tum Vocabulary/ORBvoc.txt Examples/Monocular/TUM1.yaml /media/tliu/WD_PassPort_1/slam_datasets/tum/rgbd_dataset_freiburg1_xyz



Stereo Examples
---------------------




RGB-D Example
----------------



ROS Example
-----------------




