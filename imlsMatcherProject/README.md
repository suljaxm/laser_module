代码里面有两个工程:champion_nav_msgs 和 imlsProject;需要首先编译安装 champion_nav_msgs,按照 champion_nav_msgs 的 readme 文件执行即可,或运行命令 `sudo bash install.sh`,注意根据自己 ubuntu 的不同版本做修改。

Step2:在 imlsMatcherProject 下,进行 `source devel/setup.bash`;

启 动 roscore , 然 后 在 另 一 个 终 端 进 行 source , 并 运 行 命 令 

`rosrun imlsMatcher imlsMatcher_node` 启动节点。
之后启动 rviz 可以查看激光和里程计的轨迹。



dependencies: libnabo 库

```
git clone git://github.com/ethz-asl/libnabo.git
cd libnabo
mkdir build
cd build && cmake ..
make 
sudo make install
```







