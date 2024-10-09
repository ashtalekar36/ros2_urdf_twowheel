# ros2_urdf_twowheel
TO CREATE A URDF FILE 
touch myrobot.urdf    #this will create a file in ur home directory
TO EDIT THE FILE
code my_robot.urdf
*TO INSTALL *
sudo apt install ros-humble-urdf-tutorial
Source It
source /opt/ros/humble/setup.bash
*TO CHECK THE PATH DIR OF THWE FILE *
ls
pwd
*TO LAUNCH THAT URDF FILE USE THIS COMMAND *
ros2 launch urdf_tutorial display.launch.py model:=/home/ed/ashish/my_robot.urdf   #here check the path according to ur dir by us
*to create pdf *
ros2 run tf2_tools view_frames  #to seee the relationship between parent and children
*DOCUMENTATION *
http://wiki.ros.org/urdf/XML/link
Double-click (or enter) to edit
THIS CONTAINS THE URDF CODE FOR A TWO WHEEL ROBOT
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
09/10/2024, 18:46 urdf_twowheel_robot - Colab
https://colab.research.google.com/drive/1z2zcHUK0NjJ2sOxIYm3S_s-mQ8RlvNeL#scrollTo=rnhM3JqZwi3t&printMode=true 1/3
            <geometry>
                <box size="0.6 0.4 0.2" />
            </geometry>
            <origin xyz="0 0 0.1" rpy="0 0 0"/>
            <material name="green"/>
        </visual>
    </link>
    <link name= "lidar">
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
09/10/2024, 18:46 urdf_twowheel_robot - Colab
https://colab.research.google.com/drive/1z2zcHUK0NjJ2sOxIYm3S_s-mQ8RlvNeL#scrollTo=rnhM3JqZwi3t&printMode=true 2/3
        <origin xyz="0.2 0.0 -0.05" rpy="0.0 0.0 0.0"/>
        <parent link="base_link"/>
        <child link="caster_wheel"/>
    </joint>
</robot>
