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
> 
> **测试ROS是否安装成功**
> 打开三个终端 依次输入
> roscore
> rosrun turtlesim turtlesim_node
> rosrun turtlesim turtle_teleop_key（在此终端使用键盘控制乌龟）
> 结果如图
![text](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/%E6%B5%8B%E8%AF%95ros.png)

### HelloWorld实现

*先创建一个工作空间；*
> mkdir -p demo_ws/src
> cd demo_ws
> catkin_make

*再创建一个功能包添加依赖；*
> cd src
> catkin_create_pkg helloworld roscpp rospy std_msgs

*编辑源文件；*                                     
>p.s. python->为py文件添加权限
>             chmod +x helloworld.py          
*编辑配置文件；*
> 编辑 ros 包下的 Cmakelist.txt文件                 
>
add_executable(hello src/helloworld.cpp 
)                                          
target_link_libraries(hello               
  ${catkin_LIBRARIES}                   
)
catkin_install_python(PROGRAMS
scripts/helloworld.py
DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

*编译并执行。*
> cd demo_ws
> catkin_make
![make](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/helloworld.png)
> 另开终端启动核心
> roscore
> cd demo_ws
> source ./devel/setup.bash
> rosrun  helloworld hello  
> rosrun hellowolrd helloworld.py
![helloworld_c](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/helloworld2.png)
![helloworld_py](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/helloworld_py.png)

### vscode配置
![code_cmake](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/vscode%20%E9%85%8D%E7%BD%AE.png)
> *配置中出现的问题*
> c++实现
> 修改 .vscode/c_cpp_properties.json
> 设置 "cppStandard": "c++17"
![code_C](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/vscode_c%2B%2B.png)
> python实现
> 终端中输入 sudo ln -s usr/bin/python3 /usr/bin/python
> *无需编译 软链接*
![code_py](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/vscode_py.png)

launch文件
<launch>
    <node pkg="helloworld" type="demo_hello" name="hello" output="screen" />
    <node pkg="turtlesim" type="turtlesim_node" name="turtle_GUI"/>
    <node pkg="turtlesim" type="turtle_teleop_key" name="turtle_key" />
</launch>
node ---> 包含的某个节点
pkg -----> 功能包
type ----> 被运行的节点文件
name --> 为节点命名
output-> 设置日志的输出目标
运行>> roslaunch helloworld start_turtle.launch

#ROS文件系统及命令
> 还需要多看多熟练
![ros!](http://www.autolabor.com.cn/book/ROSTutorials/chapter1/15-ben-zhang-xiao-jie/151-roswen-jian-xi-tong.html)


*计算图*
> 运行launch文件实现小乌龟案例演示计算图
> 终端输入 rosrun rqt_graph rqt_graph
![rqt_graph](https://github.com/lokiiiiiiiiii/ros_learn/blob/main/img/%E8%AE%A1%E7%AE%97%E5%9B%BE.png)
