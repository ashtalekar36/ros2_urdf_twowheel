TO CREATE A URDF for a Two-Wheel Robot

This repository contains a URDF (Unified Robot Description Format) file for a two-wheel robot.

## Creating the URDF File

To create a URDF file, run the following command:

```bash
touch myrobot.urdf  # This will create a file in your home directory
```
## Edit the File
To edit the URDF file, use:
```bash
code my_robot.urdf
```
## Install Required Packages
To install the necessary packages, run:
```bash
sudo apt install ros-humble-urdf-tutorial
```
## Source the Environment
Source the ROS setup:
```bash
source /opt/ros/humble/setup.bash
```
## Check the Path Directory of the File
To check the path of the directory, use:
```bash
ls
pwd
```
## Launch the URDF File
To launch the URDF file, use the following command:
```bash
ros2 launch urdf_tutorial display.launch.py model:=/home/ed/ashish/my_robot.urdf  # Check the path according to your directory
```
## Create Frames as pdf
To visualize the relationship between parent and children frames, run:
```bash
ros2 run tf2_tools view_frames  # To see the relationship
```
## Documentation
For more information, refer to the URDF documentation: 
http://wiki.ros.org/urdf/XML/joint

## URDF Code for a Two-Wheel Robot

```bash
<?xml version="1.0"?>
<robot name="my_robot">
    <material name="grey">
        <color rgba="0.7 0.7 0.7 1.0"/>
    </material>
    <material name="green">
        <color rgba="0.0 0.6 0.0 1.0"/>
    </material>
    <material name="white">
        <color rgba="1.0 1.0 1.0 1.0"/>
    </material>

    <link name="base_footprint"/>

    <link name="base_link">
        <visual>
            <geometry>
                <box size="0.6 0.4 0.2" />
            </geometry>
            <origin xyz="0 0 0.1" rpy="0 0 0"/>
            <material name="green"/>
        </visual>
    </link>

    <link name="lidar">
        <visual>
            <geometry>
                <cylinder radius="0.1" length="0.05"/>
            </geometry>
            <origin xyz="0 0 0" rpy="0 0 0"/>
            <material name="white"/>
        </visual>
    </link>

    <link name="caster_wheel">
        <visual>
            <geometry>
                <sphere radius="0.05"/>
            </geometry>
            <origin xyz="0.0 0.0 0.0" rpy="0.0 0.0 0.0"/>
            <material name="grey" />
        </visual>
    </link>

    <link name="left_wheel">
        <visual>
            <geometry>
                <cylinder radius="0.1" length="0.05"/>
            </geometry>
            <origin xyz="0.0 0.0 0.0" rpy="1.57 0.0 0.0"/>
            <material name="grey" />
        </visual>
    </link>

    <link name="right_wheel">
        <visual>
            <geometry>
                <cylinder radius="0.1" length="0.05"/>
            </geometry>
            <origin xyz="0.0 0.0 0.0" rpy="1.57 0.0 0.0"/>
            <material name="grey" />
        </visual>
    </link>

    <joint name="base_joint" type="fixed">
        <parent link="base_footprint"/>
        <child link="base_link"/>
        <origin xyz="0.0 0.0 0.1" rpy="0.0 0.0 0.0"/>
    </joint>

    <joint name="base_lidar_joint" type="fixed">
        <parent link="base_link" />
        <child link="lidar" />
        <origin xyz="0 0 0.225" rpy="0 0 0" />
    </joint>

    <joint name="base_left_wheel_joint" type="continuous">
        <parent link="base_link"/>
        <child link="left_wheel"/>
        <origin xyz="-0.15 0.225 0.0" rpy="0.0 0.0 0.0"/>
        <axis xyz="0.0 1.0 0.0"/>
    </joint>

    <joint name="base_right_wheel_joint" type="continuous">
        <parent link="base_link"/>
        <child link="right_wheel"/>
        <origin xyz="-0.15 -0.225 0.0" rpy="0.0 0.0 0.0"/>
        <axis xyz="0.0 1.0 0.0"/>
    </joint>

    <joint name="base_caster_wheel_joint" type="fixed">
        <origin xyz="0.2 0.0 -0.05" rpy="0.0 0.0 0.0"/>
        <parent link="base_link"/>
        <child link="caster_wheel"/>
    </joint>

</robot>
```

## SOURCE 
Robotic Back-End   https://youtu.be/dZ_CyyEvBE0?si=dnXIcTwnBvvCQql2
