Installation
==============

Steps
********

1. Install ardupilot

a) to test ::

    cd ardupilot/ArduSub
    sim_vehicle.py -L RATBeach --out=udp:0.0.0.0:14550 --map --console


2. Install freebuoyancy_gazebo plugin for buoyancy simulation ::

    https://github.com/bluerobotics/freebuoyancy_gazebo

3. Install link ::

    https://github.com/patrickelectric/ardupilot_gazebo

4. Run BlueRov2 Gazebo model ::

    git clone https://github.com/patrickelectric/bluerov_ros_playground
    cd bluerov_ros_playground
    source gazebo.sh
    gazebo worlds/underwater.world -u
    # Start the simulation

5. Execute ArduPilot SITL ::

    sim_vehicle.py -f gazebo-bluerov2 -L RATBeach --out=udp:0.0.0.0:14550 --console --map


Some Websites
*************

http://www.ardusub.com/