# ArduPilot-Gazebo-ROS SITL Guide
A guide for setting up ArduPilot, Gazebo and ROS.

An example project: https://github.com/yanhwee/helium

## Software Covered
- ArduPilot
- ArduPilot Gazebo Plugin (khancyr)
- Gazebo 9
- ROS Noetic
- MAVROS (ROS package)

## Requirements
Tested on Native Ubuntu 20.04.

## Quick Installation
Script defaults to the home directory as the initial working directory, modifiable in the script.
Script will use this working directory to git clone ArduPilot & ArduPilot Gazebo Plugin repositories.

`wget -O - https://raw.githubusercontent.com/ParasInternKhushPatil/ardupilot-gazebo-ros-guide/master/install.bash | bash`

Script will refresh the sudo timeout every 10 mins so intallation will not be interrupted. Please do not `sudo bash`. This will run as root and script will not work.

Please restart after the installation is done.

The guide below walks through the steps found in the script.

## References
1. ROS Melodic Ubuntu Installation  
http://wiki.ros.org/noetic/Installation/Ubuntu

2. ArduPilot  
https://ardupilot.org/dev/docs/building-setup-linux.html

3. khancyr ArduPilot Gazebo Plugin  
https://github.com/khancyr/ardupilot_gazebo

4. ROS package: MAVROS  
https://github.com/mavlink/mavros/tree/master/mavros

## Installation Guide

### 0. Prerequisites
1. Git
    - `sudo apt install git`

### 1. ROS (and Gazebo)
1. Follow all steps:  
http://wiki.ros.org/melodic/Installation/Ubuntu
    - Install: `ros-<distro>-desktop-full`
    - For our case: `ros-noetic-desktop-full`
    - Gazebo will be installed alongside ROS

### 2. ArduPilot
1. Git clone:  
https://ardupilot.org/dev/docs/building-setup-linux.html#cloning-with-the-command-line

2. Install required packages:  
https://ardupilot.org/dev/docs/building-setup-linux.html#install-some-required-packages

### 3. ArduPilot Gazebo Plugin (khancyr)
1. Git clone:  
https://github.com/khancyr/ardupilot_gazebo#usage-
    - Skip directly to  
    `git clone https://github.com/khancyr/ardupilot_gazebo`

2. Build:  
https://github.com/khancyr/ardupilot_gazebo#usage-
    - Continue after the git clone
    - Set the paths as well

### 4. MAVROS
1. Binary Installation  
https://github.com/mavlink/mavros/tree/master/mavros#binary-installation-deb
    - `sudo apt-get install ros-noetic-mavros ros-noetic-mavros-extras`

2. Install GeographicLib  
https://github.com/mavlink/mavros/tree/master/mavros#binary-installation-deb

### 5. Recommended
1. catkin_tools  
https://ardupilot.org/dev/docs/ros-install.html#installing-mavros
    - `sudo apt-get install python-catkin-tools`

### 6. Optional
1. RQT (ROS package)  
https://ardupilot.org/dev/docs/ros-install.html#installing-mavros
    - `sudo apt-get install ros-noetic-rqt ros-noetic-rqt-common-plugins ros-noetic-rqt-robot-plugins`

## Quick Test
1. Without ROS  
    1. https://ardupilot.org/dev/docs/using-gazebo-simulator-with-sitl.html#start-the-simulator
    2. https://ardupilot.org/dev/docs/copter-sitl-mavproxy-tutorial.html

2. With ROS  
    - Check out Intelligent Quad Videos
    - Or look at Learning Resources (Connecting to ROS) & continue with Quick Test (Without ROS step 2)

## Software Architecture Overview
These psuedo-diagrams are for you to get an idea of how the whole thing works.

### Typical Drone System (Physical Components)
![Physical Diagram](physical-drone-system.svg)

### Software-in-the-Loop (SITL Components)
![SITL Diagram](sitl-architecture.svg)

## Learning Resources
1. Intelligent Quad  
    1. YouTube  
    https://www.youtube.com/playlist?list=PLy9nLDKxDN683GqAiJ4IVLquYBod_2oA6
    2. GitHub  
    https://github.com/Intelligent-Quads/iq_tutorials

2. ROS
    1. Tutorials  
    http://wiki.ros.org/ROS/Tutorials
    2. Understanding package.xml  
    http://wiki.ros.org/roslaunch/XML
    3. IDEs  
    http://wiki.ros.org/IDEs

3. Catkin
    1. Workspaces  
    http://wiki.ros.org/catkin/workspaces
    2. catkin_tools  
    https://catkin-tools.readthedocs.io/en/latest/quick_start.html

4. CMake
    1. Understanding CMakeLists.txt  
    https://www.youtube.com/playlist?list=PLK6MXr8gasrGmIiSuVQXpfFuE1uPT615s
    2. Documentation  
    https://cmake.org/cmake/help/v3.17/manual/cmake.1.html

5. ArduPilot
    1. Connecting to ROS  
    https://ardupilot.org/dev/docs/ros-sitl.html
    2. SITL Architecture  
    https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html#sitl-architecture
    3. Using SITL (sim_vehicle.py & MAVProxy)  
    https://ardupilot.org/dev/docs/using-sitl-for-ardupilot-testing.html
    4. SITL Examples  
    https://ardupilot.org/dev/docs/sitl-examples.html

6. ArduCopter
    1. Paramters List  
    https://ardupilot.org/copter/docs/parameters.html
    2. Flight Modes  
    https://ardupilot.org/copter/docs/flight-modes.html

7. MAVLink
    1. MAVLink Messages  
    https://mavlink.io/en/messages/common.html
    2. Copter Commands (Guided)  
    https://ardupilot.org/dev/docs/copter-commands-in-guided-mode.html#copter-commands-in-guided-mode
    3. Copter Commands (Auto / Mission)  
    https://ardupilot.org/copter/docs/common-mavlink-mission-command-messages-mav_cmd.html
    4. Pymavlink (Also applicable to ArduCopter)  
    https://www.ardusub.com/developers/pymavlink.html

8. Gazebo
    1. Tutorials  
    http://gazebosim.org/tutorials
    2. Digitial Elevation Map (DEM)
        1. Tool for getting real-life DEM  
            https://terrain.party/
        2. Heightmap Tutorial  
        https://vimeo.com/58409707
    3. SDFormat Specification  
    http://sdformat.org/spec


## Troubleshooting
### 1. ArduPilot
1. sim_vehicle.py not found
    - Restart Ubuntu

### 2. Gazebo
1. Slow Gazebo startup or  
libcurl: (6) Could not resolve host: api.ignitionfuel.org
    - https://bitbucket.org/osrf/gazebo/issues/2607/error-restcc-205-during-startup-gazebo
    - In ~/.ignition/fuel/config.yaml, change to:  
        - url: https://fuel.ignitionrobotics.org/1.0/models

2. Bad lighting
    - https://answers.gazebosim.org//question/848/lighting-and-shadow-effect-problems/
    - In world file, set shadow to 0
    - Or in Gazebo >> World >> Scene >> Disable Shadow

### 3. Visual Studio Code
1. Linting for cpp files
    1. Find ROS cpp path
        1. Can be found by  
        `cd / && sudo find -name 'ros.h'`
    2. Add path to "c_cpp_properties.json' include path

### 4. Mavproxy
1. Any Problems
    - Try `pip install -U mavproxy`

2. Re-requesting WPs
    - https://github.com/ArduPilot/MAVProxy/issues/402
    - In the MAVProxy Terminal
        - Type: `wp list`

## Tips
### 1. QGroundControl
1. Rebooting ArduPilot
    1. Click on the Gear Icon (Vehicle Setup), top-left of the screen.
    2. Click on the Parameter Tab, bottom left of the Vehicle Setup screen.
    3. Click Tools, top-right of the screen.
        - If not found, click on the Clear Button beside the Search Bar first.
    4. Click "Reboot Vehicle"
