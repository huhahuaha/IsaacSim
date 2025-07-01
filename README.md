# IsaacSim

## MIC实验室仿真一期效果及说明
## 1. 效果演示
### 1.1 整体静态效果视频
mic_lab

https://github.com/user-attachments/assets/8c3bcdeb-5777-4edc-9d09-cd1e7b505b06

### 1.2 RealMan机械臂效果演示
realman

https://github.com/user-attachments/assets/8331ce4c-cbbc-4d08-bc2a-8fe932847232



### 1.3 RealMan机械臂关节控制效果
realman

https://github.com/user-attachments/assets/9108e7ad-200a-4345-8e74-8c95484b6db9



### 1.4 双臂协同机械臂效果演示

双臂机械臂效果演示

https://github.com/user-attachments/assets/7309ab8e-b64b-46b5-bf1e-26558404eda8

### 1.5 差分控制效果演示
差分控制


https://github.com/user-attachments/assets/19ed3103-1f24-4893-98f8-9347a6e033c5

### 1.6 摄像头数据发布效果演示
摄像头全局视角

https://github.com/user-attachments/assets/d83fef06-b6c9-464f-8af8-3f8f025c3b4f

ROS_camera

https://github.com/user-attachments/assets/62b65bc4-ac42-4345-a6d3-361fa0edbf98

ROS_topic

https://github.com/user-attachments/assets/b65a10b2-130b-408a-8e15-b245d1117d2a

## 2. 使用及控制说明
### 2.1 差分控制实现
目前差分控制器只在isaac Sim中实现键盘映射，也可以通过ROS2 的keyboard实现
![image](https://github.com/user-attachments/assets/cf96da46-b026-4ab0-991f-148d8f983b57)

具体控制按键：
  - W：前进
  - S：后退
  - A：左转
  - D：右转

### 2.2 RealMan机械臂控制实现
关节发布话题：joint_command
关节订阅话题：joint_states

```
publish topic name：joint_states
subscribe topic name ：joint_command
```

订阅joint状态指令 ： 
```
ros2 topic echo --once /joint_states
```
![image](https://github.com/user-attachments/assets/e66ea0a9-e976-4ab1-a9e0-907e6d0a0709)

### 2.3 双臂协同机械臂Sim控制流程实现
具体输入数值控制，在点击运行后即可控制实现，运行过程中亦可控制。
![image](https://github.com/user-attachments/assets/5464e878-9ea7-475a-b31b-8696234fcdd2)
![image](https://github.com/user-attachments/assets/b972c8a5-1a9f-45c2-82bb-0b18e948a91e)

### 2.4 双臂协同机械臂ROS控制
![image](https://github.com/user-attachments/assets/2f50afc5-462f-4b62-a7a1-c71d33756197)

话题：
```
/mic_joint_command
/mic_joint_states
```
ros2 查看
```
ros2 topic echo /mic_joint_command
ros2 topic echo /mic_joint_states
```

```
header:
  stamp:
    sec: 990
    nanosec: 800051674
  frame_id: ''
name:
- fl_castor_wheel
- fr_castor_wheel
- left_wheel_joint
- right_wheel_joint
- rl_castor_wheel
- rr_castor_wheel
- fr_joint1
- fl_wheel
- fr_wheel
- rl_wheel
- rr_wheel
- fl_joint1
- fr_joint2
- fl_joint2
- fr_joint3
- fl_joint3
- fr_joint4
- fl_joint4
- fr_joint5
- fl_joint5
- fr_joint6
- fl_joint6
- fr_joint7
- fr_joint8
- fl_joint7
- fl_joint8
```
### 2.5 摄像头ROS发布实现
话题(亦可提供点云信息) ：
```
/rgb
/depth
/depth_pcl
```

```
ros2 topic info -v /rgb                        
Type: sensor_msgs/msg/Image

Publisher count: 1

Node name: _Render_PostProcess_SDGPipeline_Replicator_NodeWriterWriter_01
Node namespace: /
Topic type: sensor_msgs/msg/Image
Endpoint type: PUBLISHER
GID: 01.0f.1a.53.bc.45.80.e4.01.00.08.00.00.00.05.03.00.00.00.00.00.00.00.00
QoS profile:
  Reliability: RELIABLE
  History (Depth): UNKNOWN
  Durability: VOLATILE
  Lifespan: Infinite
  Deadline: Infinite
  Liveliness: AUTOMATIC
  Liveliness lease duration: Infinite

Subscription count: 0
```

```
ros2 topic info -v /depth
Type: sensor_msgs/msg/Image

Publisher count: 1

Node name: _Render_PostProcess_SDGPipeline_Replicator_NodeWriterWriter
Node namespace: /
Topic type: sensor_msgs/msg/Image
Endpoint type: PUBLISHER
GID: 01.0f.1a.53.bc.45.80.e4.01.00.08.00.00.00.04.03.00.00.00.00.00.00.00.00
QoS profile:
  Reliability: RELIABLE
  History (Depth): UNKNOWN
  Durability: VOLATILE
  Lifespan: Infinite
  Deadline: Infinite
  Liveliness: AUTOMATIC
  Liveliness lease duration: Infinite

Subscription count: 0
```
## 3. 二期展望
### 3.1 数字孪生
![image](https://github.com/user-attachments/assets/c4024102-b8d7-47e3-b0da-4e75b3e98692)
### 3.2 具身智能
#### 3.2.1 具身智能数据采集
  目前具身智能领域主要竞争点在于上肢桌面级操作，其中核心竞争点在于数据采集上，普遍的训练行业实现方式有以下几种，我们目前使用的同构的方案来实现。但是无论哪种方案，目前都需要仿真数据来做支撑。
![image](https://github.com/user-attachments/assets/9ded2ed4-3fcc-4483-bb66-b2298c0aa180)
我目前主业是基于同构方式实现仿真数据采集，在数字孪生场景搭建、动作映射、数据采集链路上都有知识储备，以下展示的仿真数据采集平台的工作是我目前实现的效果，目前整体链路已经打通。


https://github.com/user-attachments/assets/4478dd28-cc60-4c07-9d3c-c27c4109a92b

