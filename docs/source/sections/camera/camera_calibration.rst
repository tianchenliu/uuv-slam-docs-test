Camera Calibration
====================

Using ROS
------------

In ROS workspace,

Install usb_cam ::

    git clone https://github.com/ros-drivers/usb_cam
    cd ..
    catkin_make

Edit ros_mono.cc

Run 

Tab 1 ::
    
    roscore

Tab 2 ::
    
    source devel/setup.bash
    roslaunch usb_cam usb_cam-test.launch
    
Tab 3 ::
    
    source devel/setup.bash
    rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.108 image:=/usb_cam/image_raw camera:=/usb_cam

Click 'Save' button, will display ('Wrote calibration data to', '/tmp/calibrationdata.tar.gz')


OpenCV Calibration
---------------------


