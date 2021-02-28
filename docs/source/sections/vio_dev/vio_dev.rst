
VIO DEV
=======

ROS Camera Package
------------------

Cam Publisher Node
^^^^^^^^^^^^^^^^^^


#. Create ROS Package

.. code-block::

   catkin_create_pkg ros_cv std_msgs roscpp rospy cv_bridge sensor_msgs image_transport rosbag


#. 
   Create a C++ file

#. 
   Edit ``CMakeLists.txt``\ , use OpenCV as example

.. code-block::

   find_package(OpenCV)
   include_directories(${OpenCV_INCLUDE_DIRS})

   add_executable(cam_pub src/cam_pub.cpp)
   target_link_libraries(cam_pub ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})


#. 
   ``catkin_make`` from ws folder

#. 
   Run

.. code-block::

   roscore

.. code-block::

   rosrun ros_cv cam_pub

.. code-block::

   rosrun image_view image_view image:=/camera

Cam Subscriber Node
^^^^^^^^^^^^^^^^^^^


#. 
   Using the same ROS package

#. 
   Create a C++ file

#. 
   Edit ``CMakeLists.txt``\ , use OpenCV as example 

.. code-block::

   add_executable(cam_sub src/cam_sub.cpp)
   target_link_libraries(cam_sub ${catkin_LIBRARIES} ${OpenCV_LIBS})


#. ``catkin_make`` from ws folder


#. 
   Make launch file for launching both nodes

#. 
   Run launch file

.. code-block::

   roslaunch ros_cv cam.launch

Ref
---


* `blog <https://automaticaddison.com/working-with-ros-and-opencv-in-ros-noetic/>`_
