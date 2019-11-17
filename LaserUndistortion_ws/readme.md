本题目为实现一个里程计去除激光雷达运动畸变的代码模块,作业里面有两个工程:champion_nav_msgs 和 LaserUndistortion。大家需要首先编译安装 champion_nav_msgs,按照champion_nav_msgs 的 readme 文件执行即可,或运行命令 `sudo bash install.sh`,注意如果你的ubuntu 版本不是 kinetic,要将所有 kinetic 的地方修改成你的 ros 版本。

Step2:在 LaserUndistortion 下,进行 `source:source devel/setup.bash`;

Step3:运行 launch 文件:`roslaunch LaserUndistortion LaserUndistortion.launch`,执行本条指令的时候,必须保证没有任何ROS 节点在运行, roscore 也要关闭;

Step4:进入到 /bag 目录下,运行指令:`rosbag play -–clock laser.bag`;

Step5:如果一切正常,则会看到 pcl 的可视化界面,当可视化界面中存在数据的时候,按 R 键即可看到结果(红色为畸变矫正前,绿色为畸变矫正后)。
