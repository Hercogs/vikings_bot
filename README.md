# Vikings Bot bringup package
<hr>
Description: contains files to bringup files related with Vikings Bot project
<hr>

### Dependencies: ...

<hr>

__To clone this project:__
```
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
git clone git@github.com:Hercogs/vikings_bot.git -b dev_kriss
cd ~/ros2_ws/src/vikings_bot
git submodule init
git submodule update
git submodule update --recursive --remote

# clone external dependencies
cd ~/ros2_ws/src
git clone git@github.com:pal-robotics/realsense_gazebo_plugin.git -b foxy-devel
git clone git@github.com:IntelRealSense/realsense-ros.git

# build (realsense2_camera requires realsense sdk, it is not needed for simulation)
cd ~/ros2_ws
colcon build --packages-skip realsense2_camera
source install/setup.bash
```
To update repo, use:
```
git submodule update --recursive --remote
```


<hr>

__To launch gazebo world, execute:__
```
ros2 launch vikings_bot_bringup start_simulation.launch.xml
```

__To spawn one robot, execute:__
```
ros2 launch vikings_bot_bringup bringup_first_bot.launch.xml
```

__To spawn two robots, execute:__
```
ros2 launch vikings_bot_bringup bringup_two_bots.launch.xml
```
Then in Rviz enable second robot visualization.

To move robots with keypad, execute:

For first robot:
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r cmd_vel:=vikings_bot_1/cmd_vel
```

For second robot
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r cmd_vel:=vikings_bot_2/cmd_vel
```

__To test Nav2, in Rviz us `2D Goal Pose` button to send goal to robot.__


In case something is not working, let me know!




