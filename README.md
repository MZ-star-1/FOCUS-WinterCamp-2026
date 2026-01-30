# FOCUS-WinterCamp-2026

#任务点1 按链接跳转页面的教程操作可以实现（注意下载版本20.04不是24.04即可）

#任务点2

#下载unitree_ros及其依赖，在catkin_ws/src下执行

git clone https://github.com/unitreerobotics/unitree_ros --depth 1

cd unitree_ros

git submodule update --init --recursive --depth 1

#安装ROS Noetic依赖包

sudo apt update

sudo apt-get install ros-noetic-controller-interface \

  ros-noetic-gazebo-ros-control \
  
  ros-noetic-joint-state-controller \
  
  ros-noetic-effort-controllers \
  
  ros-noetic-joint-trajectory-controller \
  
  liblcm-dev

#修改unitree_gazebo/worlds/starts.world中的<uri>路径

<include>
  
  <uri>model:///home/unitree/catkin_ws/src/unitree_ros/unitree_gazebo/worlds/building_editor_models/stairs</uri>
  
</include>

#将home后的unitree改为lhy3（文件名）

#回到catkin_ws编译

cd ~/catkin_ws

catkin_make

###提示缺少unitree_legged_msgs这个包，导致catkin_make配置失败

###还会报错cd ~/catkin_ws/src/unitree_ros找不到

#下载unitree_guide在catkin_ws/src目录下

git clone https://github.com/unitreerobotics/unitree_guide --depth 1

#检查缺少的依赖，如果提示找不到move_base_msgs

sudo apt install ros-noetic-move-base-msgs

sudo apt install ros-noetic-move-base

#再次编译

cd ~/catkin_ws

catkin_make

#启动仿真和控制器

source devel/setup.bash

roslaunch unitree_guide gazeboSim.launch

#另一个终端

cd ~/catkin_ws

source devel/setup.bash
./devel/lib/unitree_guide/junior_ctrl



