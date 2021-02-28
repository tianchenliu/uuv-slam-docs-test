# VIO DEV 

## ROS Camera Package

### Cam Publisher Node

1. Create ROS Package

```
catkin_create_pkg ros_cv std_msgs roscpp rospy cv_bridge sensor_msgs image_transport rosbag
```

2. Create a C++ file

3. Edit `CMakeLists.txt`, use OpenCV as example

```
find_package(OpenCV)
include_directories(${OpenCV_INCLUDE_DIRS})

add_executable(cam_pub src/cam_pub.cpp)
target_link_libraries(cam_pub ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})
```
4. `catkin_make` from ws folder

5. Run

```
roscore
```

```
rosrun ros_cv cam_pub
```

```
rosrun image_view image_view image:=/camera
```

### Cam Subscriber Node

1. Using the same ROS package

2. Create a C++ file

3. Edit `CMakeLists.txt`, use OpenCV as example 

```
add_executable(cam_sub src/cam_sub.cpp)
target_link_libraries(cam_sub ${catkin_LIBRARIES} ${OpenCV_LIBS})
```

4. `catkin_make` from ws folder


5. Make launch file for launching both nodes

6. Run launch file

```
roslaunch ros_cv cam.launch
```

## Ref

- [blog](https://automaticaddison.com/working-with-ros-and-opencv-in-ros-noetic/)
