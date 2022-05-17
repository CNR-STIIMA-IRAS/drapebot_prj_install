# drapebot_prj_install
The  [DrapeBot](https://www.drapebot.eu/) project aims at human-robot collaborative draping. The robot is supposed to assist during the transport of the large material patches and to drape in areas of low curvature.  The project aim at a smooth and efficient interaction between the human and the robot. 
The DrapeBot project runs over a period of four years from January 2021 to December 2024.
## Index

1. [Packages description](#desc)
2. [Install packages](#ros)

## Packages description <a name="desc"></a>

The packages relative to the DrapeBot project are divided into:
1. DrapeCell with ABB robot:
    1. [abb_app](https://github.com/CNR-STIIMA-IRAS/abb_app): contains configuration files to load the control enviroment for the ABB robot  
    2. [abb_description](https://github.com/CNR-STIIMA-IRAS/abb_description): contains URDF and meshes of the ABB robot  
    3. [abb_moveit](https://github.com/CNR-STIIMA-IRAS/abb_moveit): contains moveit configuration files for the ABB robot  

2. TEZ cell with two KUKA robots:
    1. [tez_app](https://github.com/CNR-STIIMA-IRAS/tez_app): contains configuration files to load the control enviroment for the TEZ cell  
    2. [tez_description](https://github.com/CNR-STIIMA-IRAS/tez_description): contains URDF and meshes of the TEZ cell  
    3. [tez_moveit](https://github.com/CNR-STIIMA-IRAS/tez_moveit): contains moveit configuration files of the TEZ cell  

3. Common for communication and control:
    1. [cnr_mqtt](https://github.com/CNR-STIIMA-IRAS/cnr_mqtt): module to convert mqtt message to call ROS FollowJointTrajectoryMsg action  
    2. [cnr_mqtt_hardware_interface](https://github.com/CNR-STIIMA-IRAS/cnr_mqtt_hardware_interface): hardware interface that implements MQTT commnication  
    3. [deformation_ctrl](https://github.com/CNR-STIIMA-IRAS/deformation_ctrl): implements control logic to deviate the robot from a nominal trajectory according to human motions  


## Install ROS packages <a name="ros"></a>
### Preliminaries

As a preliminary, to install required repositories, follow [here](https://github.com/JRL-CARI-CNR-UNIBS/installation/blob/master/installation_single_workspace.md).
Recommended single workspace installation.


### Install required packages for DrapeBot
#### source previous workspace
```
source <path_to_control_ws>/devel/setub.bash
```
#### create and init a new workspace
```
mkdir drapebot_ws
cd drapebot_ws
mkdir src
catkin build -cs
```
#### clone this repository
```
git clone https://github.com/CNR-STIIMA-IRAS/drapebot_prj_install.git
```
#### initialize and merge with wstool
```
wstool init src
wstool merge -t src drapebot_prj_install/drapebot.rosinstall
wstool update -t src
```
#### build and source the workspace
```
catkin build -cs
source devel/setup.bash
```

