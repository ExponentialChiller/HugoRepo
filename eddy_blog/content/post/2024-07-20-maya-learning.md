---
layout:     post
title:      "Maya Learning"
subtitle:   "Some basic operations about maya"
date:       2024-07-20
author:     "Eddy"
---

## 关于maya的一些操作

### 1. 导入fbx后尺寸不对，调整当前显示的默认单位 window->preference->settings

### 2. 动画播放的速度不对，可能是默认的播放选项不一样，window->preference->时间滑块

### 3. 创建骨骼：选中模式为绑定，然后创建骨骼，按住x点鼠标左键可以吸附到网格点上
![create skeleton](../../img/createSkeleton.png)

### 4. 插入root骨骼，先选中原来的根节点，然后再ctrl 选中新增根节点，按下P，即可自动完成


## 关于动画的一些操作
1. 动画有只包括skeleton的和有蒙皮的，如果项目里这两种动画都要使用，则需要先导入有骨骼的动画
2. 导入动画时可以选择导入的范围，如全部导入`exported time`，只导入有动画的部分`Animated time`，以及指定帧数的导入`Set Range`

动画重定向
1. 两套骨骼需要先调整到同一个姿势，可以借助摆放到同一视图来实现，具体操作步骤：
   1.1 需要修改姿势的人物，对照需要修改的姿势进行修改
   1.2 选择 RetargetManager，选择  Modify Pose
   1.3 在修改姿势的人物，选择RetargetManager -> Select Rig -> Select Humanoid Rig，对照着参考的骨骼，将新的骨骼绑定到标准名称
   ![change skeleton name](../../img/changeSkeletonName.png)

2. 选中某个动画，Retarget Anim Blueprint, 如果出现了source或target为空白，需要确保目标 skeleton 拥有不为空的preview mesh
3. 如果发现转换后的动画在高度或者比-例上不一致，可以回到原来的骨骼设置，对节点进行retarget的模式设置
   ![adjust the retarget mode](../../img/adjustSkeletonMode.png)

## Blend Space 参数说明
1. interpolation time:Interpolation Time for input, when it gets input, it will use this time to interpolate to target. Used for smoother interpolation.简单说就是让动画的过渡更流畅。
2. 动画的播放速率是可以调整的，在Blend Space里可以调整动画的rate scale

state machine
1. state 里还可以添加 state machine
