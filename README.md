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
