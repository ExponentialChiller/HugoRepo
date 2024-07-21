---
layout: post
title : 'Light in UE'
date : '2024-07-20T13:22:46+08:00'
published: true
---

## 1. Mobility  类型

|static|stationary|movable|
|---|---|---|
| 运行时无法改变或移动 | 除位置外其他属性可改变 | 属性均可改变|

注意：__设置光源为movable时，需要设置场景内禁止灯光贴图 `force No Precomputed lighting`__

## 2. 天光源类型
SLS捕获场景（SLS Captured Scene）：从捕获的场景构造天空光照。任何与天光位置的距离超过天空距离阈值（Sky Distance Threshold ）的部分都将被包括在内。

SLS指定立方体贴图场景（SLS Specified Cubemap）从指定的立方体贴图构造天空光照。

## 3. 通过 post process volume 剔除不需要的eye adaption效果
首先选中volume，并拖放到场景中，设置其bound 为 infinite extent
![get volume](../../img/postProcessVolume.png)

对场景中的volue进行设置，调整模式，并调整最大与最小亮度一直
![set volume](../../img/PostProcessVolumeSettings.png)

## 4. collision

[collision官方說明文檔](https://docs.unrealengine.com/4.27/en-US/InteractiveExperiences/Physics/Collision/Overview/)

|ignore|overlap|block|
|-----|-----|-----|
|可以穿透过的，没有碰撞属性 |可以有重叠|完全的两个刚体|

`collision presets`属性解释</br>
`object type`：当前被设置的物体，其物理属性</br>
`object response:当前物体与其他某种类型物体产生碰撞时所产生的物理效果

<font color='red'>注意，如果两个object的物理属性产生了冲突，则优先级顺序:block\<overlap\<ignore </font>

### 4.1 collision 新增类型
假如某个 object 的 collision 设置不符合当前设置，可以通过新增 collision channel 来解决，路径 `project setting` -> `coliision` -> `object channels`， 然后在想要修改 collision 类型的物体或者材质上勾选 collision 设置下的 object type，设置为刚刚新增的类型。</br>
同理，也可以在`project setting`里新增 collision preset，来保存一套collison 的配置