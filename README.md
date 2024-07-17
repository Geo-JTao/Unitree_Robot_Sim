## Instruction
The project provides a mapping and navigation package for Unitree quadruped robots in Gazebo(Ubantu18.04).

The content is divided into three parts: 

    (1) Basic motion control of quadruped robot(C++)

    (2) Dynamic obstacle avoidance navigation(ROS)

    (3) SLAM mapping based on LiDAR(ROS)

    
Give it a star if it helps you, thank you ~
- [The page of a handsome man ](https://space.bilibili.com/485363351?spm_id_from=333.788.0.0)

## Reference 
- [Unitree document](https://support.unitree.com/home/zh/Algorithm_Practice/about_unitreeguide)
- [Video Explanations](https://www.bilibili.com/video/BV1EZ421T7Eo/?spm_id_from=333.999.list.card_archive.click&vd_source=63cd8055657905c0ac8a9388d7a972ed)
- [Project in Baidu web disk](https://pan.baidu.com/s/1RsSyCLD6KC6fJqOELFD-KQ?pwd=1234)

## Code example
1. Motion control
    Switch the robot state according to the keyboard keys, read the reference Unitree document for details.
   
    FreeStand state:W-A-S-D-I-J-K-L,Trotting state:W-A-S-D-J-L
   
    The project in Baidu web disk provides a detailed code annotation.
   
Terminal_1:
```
    cd ~/unitree_ws
    source ./devel/setup.bash
    roslaunch unitree_guide gazeboSim.launch
```
Terminal_2:
```
    cd ~/unitree_ws
    source ./devel/setup.bash
    sudo ./devel/lib/unitree_guide/junior_ctrl
```

2. Navigation

    Note: you need to set(MOVE_BASE ON) in the unitree_guide/CMakeLists.txt file.
```
    roslaunch unitree_move_base gazebo_move_base.launch
```
```
    sudo ./devel/lib/unitree_guide/junior_ctrl
```
```
    roslaunch unitree_move_base rvizMoveBase.launch
```

3. SLAM mapping

    Note: Check the contents of the robot_description parameter in the src\unitree_guide\unitree_move_base\launch\move_base.launch file
          to ensure that the robot model loaded with radar is used.
```
    roslaunch unitree_move_base gazebo_move_base.launch
```
```
    sudo ./devel/lib/unitree_guide/junior_ctrl
```
```
    roslaunch unitree_move_base slam_gmapping.launch
```

In terminal_4, You can write code to control the robot's walk to complete the mapping, just send data to the cmd_vel topic.Or refer to key control:

```
    rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

