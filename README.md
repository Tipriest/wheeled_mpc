# Wheeled MPC Test Benchmark

## 项目简介
用于轮式机器人控制的项目

## 特性
1. 使用手柄控制机器人运动
<div align="center" style="margin: 20px 0;">
  <img src="assets/gif/joystick_control.gif"
       alt="joystick_control" 
       title="joystick_control"
       width="800" 
       style="max-width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);"
       loading="lazy"/>
</div>
2. 使用move_base + pure pursuit进行轮式机器人导航
<div align="center" style="margin: 20px 0;">
  <img src="assets/gif/movebase_nav.gif" 
       alt="movebase_nav" 
       title="movebase_nav"
       width="800" 
       style="max-width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);"
       loading="lazy"/>
</div>

3. Nonlinear Model Pridictive Control (through [ipopt solver](https://coin-or.github.io/Ipopt/))  
4. Wheeled Mobile Robot



## 安装

1. Ubuntu 20.04
2. Install [ROS](http://wiki.ros.org/) Noetic.
3. Install ROS dependencies and other Nonlinear Solver dependencies

```bash
  sudo apt install ros-noetic-costmap-2d \
  ros-noetic-move-base \
  ros-noetic-global-planner \
  ros-noetic-amcl
  ros-noetic-ackermann-msgs

  # install livox_sdk
  cd ~/Downloads
  git clone git@github.com:Tipriest/Livox-SDK.git
  cd Livox-SDK
  cd build && cmake ..
  make
  sudo make install

```
**install IPOPT**
Please refer the two Blogs [Blog1](https://blog.csdn.net/weixin_42277529/article/details/126641660) [Blog2](https://blog.csdn.net/asd22222984565/article/details/130794329) to install `IPOPT`

```bash
  cd ~/Documents
  git clone https://github.com/Tipriest/wheeled_mpc.git
  git submodule update --init --recursive
```

## 编译

```bash
cd ~/Documents/wheeled_mpc
catkin build
```

## 使用方法

#### 1. 手柄控制小车运动
```bash

source devel/setup.bash
# 按住手柄控制小车运动，直接是ps5，xbox等也支持，需要修改Launch文件
roslaunch mpc_ros joystick_control.launch
# 目前是左摇杆上下控制线速度，右摇杆左右控制角速度，可以自行修改
```
#### 2. 小车自主运动
```bash

source devel/setup.bash
roslaunch mpc_ros nav_gazebo.launch
# 如上面的动图所示，在RVIZ中给出3D Nav Goal，然后小车可以规划路径自主移动
```

## 目录结构

```
wheeled_mpc_ros/
├── assets
├── build
├── devel
├── logs
├── README.md
└── src
```
## 目前的问题
1. [UNFIXED]现在有些时候move_base第二次导航会找不到路径
2. [UNFIXED]PurePursuit对于小车终点的处理很粗暴

## 一些想做的点



## 贡献指南

欢迎提交 issue 和 pull request！请先阅读 [贡献指南](CONTRIBUTING.md)。

## 许可证

本项目采用 MIT 许可证，详见 [LICENSE](LICENSE)。

## 联系方式

如有问题或建议，请联系：a1503741059@163.com

