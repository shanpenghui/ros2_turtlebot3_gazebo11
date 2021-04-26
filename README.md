# ros2_turtlebot3_gazebo11

## Launch turtlebot3 nav2

### 1. Install pkgs
```shell
sudo apt install -y gazebo11 ros-foxy-gazebo-ros-pkgs ros-foxy-cartographer ros-foxy-cartographer-ros ros-foxy-navigation2 ros-foxy-nav2-bringup ros-foxy-turtlebot3*
```

### 2. Install sources

```shell
sudo apt install python3-vcstool
mkdir -p ~/turtlebot3_ws/src
cd ~/turtlebot3_ws
wget https://raw.githubusercontent.com/ROBOTIS-GIT/turtlebot3/ros2/turtlebot3.repos
vcs import src < turtlebot3.repos
```

**Remember to change branch to you ros-distro**

### 3. Compile

```shell
source /opt/ros/<ros2-distro>/setup.bash
colcon build --symlink-install --parallel-workers 12
```

### 4. Start
```shell
source install/setup.bash
export TURTLEBOT3_MODEL=waffle
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/opt/ros/<ros2-distro>/share/turtlebot3_gazebo/models
source /usr/share/gazebo-11/setup.sh
ros2 launch nav2_bringup tb3_simulation_launch.py
```
