# VINS Fusion

## Installation

```
sudo apt-get install cmake
sudo apt-get install libgoogle-glog-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libeigen3-dev
sudo apt-get install libsuitesparse-dev

tar zxf ceres-solver-1.14.0.tar.gz
mkdir ceres-bin
cd ceres-bin
cmake ../ceres-solver-1.14.0
make -j3
make test
make install
```

Issue with Ceres-2.0.0 version: Eigen member error.

## Compile VINS-Fusion

```
cd PATH_TO_WS/src
git clone https://github.com/HKUST-Aerial-Robotics/VINS-Fusion.git
cd ..
catkin_make
source devel/setup.bash
```

## Run

Run on [EuRoC](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets) datasets:

```
roscore
```

```
roslaunch vins vins_rviz.launch
```

```
rosrun vins vins_node src/VINS-Fusion/config/euroc/euroc_mono_imu_config.yaml
```

```
rosrun loop_fusion loop_fusion_node src/VINS-Fusion/config/euroc/euroc_mono_imu_config.yaml
```

```
rosbag play /media/tliu/WD_PassPort_1/slam_datasets/EuRoC/V1_01_easy.bag
```




