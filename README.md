# ros_learn
Record of learning ros

## 第一章
### 安装ROS

> 终端添加ros镜像源
> sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
> 
> 添加密钥
> sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
> 
> 安装ROS
> sudo apt update
> 
> 安装桌面完整版
> sudo apt install ros-noetic-desktop-full
> 
> 设置环境变量
> echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
> source ~/.bashrc
> **测试ROS是否安装成功**
> 打开三个终端 依次输入
> roscore
> rosrun turtlesim turtlesim_node
> rosrun turtlesim turtle_teleop_key（在此终端使用键盘控制乌龟）
> 结果如图
![text](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/%E6%B5%8B%E8%AF%95ros.png)
