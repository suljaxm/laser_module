Step1: 在odom_ws下用catkin_make进行编译。
提示:如果编译过程中提示缺少csm库,可以用命令 `sudo apt-get install ros-kinetic-csm` 进行安装。如果你用的 ROS 版本为其它版本,则将CMakeLists.txt 中所有 kinetic 内容改为你的 ROS 版本。其它库安装方式也类似,比如缺少 nav_core,则用 `sudo apt-get install ros-kinetic-nav-core` 安装。

Step2: 在 odom_ws 下,进行 source,具体命令为:`source devel/setup.bash`

Step3: 运行 launch 文件:`roslaunch calib_odom odomCalib.launch`。执行本条指令的时候,必须保证没有任何 ros 节点在运行,roscore 也要关闭。

Step4: 在 Step3 正常的情况下,运行 rviz, fix_frame 选择为 odom。在 Add 选项卡中增加三条 Path 消息。一条订阅的 topic 为:odom_path_pub_;一条订阅的 topic 为:scan_path_pub_;最后一条为:calib_path_pub_。分别选择不同的颜色。

Step5: 进入到 odom_ws/bag 目录下,运行指令: `rosbag play -–clock odom.bag`。

Step6: 如果一切正常,则能看到运行矫正程序的终端会打印数据,并且 rviz 中可以看到两条路径。当打印的数据到达一个的数量之后,则可以开始矫正。

Step7: 矫正的命令为,在 calib_flag 的 topic 下发布一个数据: `rostopic pub /calib_flag std_msgs/Empty "{}"`。

Step8: 程序矫正完毕会输出对应的矫正矩阵,并且会在 rviz 中显示出第三条路径,即 calib_path。可以观察里程计路径 odom_path 和矫正路径 calib_path 的区别来判断此次矫正的效果。参考结果:绿色为 odom,黄色为激光,红色为矫正后的轨迹,可以看到校正后的轨迹跟激光的轨迹接近了很多。
