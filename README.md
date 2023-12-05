# hl_ws
jaka和realsense-ros都是官方SDK
# tracker_ws
基于ros下应用深度相机的kcf追踪算法实现

# 开发环境：

Ubuntu 20.04 + ros noetic

# 传感器：

只要是有深度信息的RGB相机即可



# 运行：

## 1.首先启动ros环境：
```
$roscore
```
## 2.运行相机的launch文件：
```
$roslaunch realsense2_camera rs_camera.launch
```

## 3.运行底盘launch文件：

要先打开机械臂的控制文件
启动地盘程序：
```
$roslaunch moveit.launch
```
## 4.启动追踪程序
```
$rosrun track_pkg kcf_node
```
## 5.使用程序

程序启动后，在图像窗口内鼠标左键框选所要跟踪的目标.在终端会输出目标中心点的x，y，z信息

# 速度规划

|参数| 数值（单位m）|
|:----:| -------------|
|Min_distance | 1.5|
|Max_distance | 5.0|
|Min_linear_speed | 0.4|
|Max_linear_speed | 0.6|
|Min_rotation_speed | 0|
|Max_rotation_speed | 0.75|

目标距离相机1.5m时开始跟踪，初始速度0.4m/s，速度随着距离的增大而增加，
最大距离5m是速度增加到0.6m/s。旋转速度初始为0, 随着目标偏移相机中心点的角度的增大而增加，
最大叫速度为0.75rad/s。
