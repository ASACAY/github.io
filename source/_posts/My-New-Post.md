---
title: Godot开发指南_吸血鬼幸存者篇
date: 2025-06-13 12:35:55
tags: notes
---

# Godot开发指南

## 关于幸存者框架

### 一.预先准备

> 资产(源)管理assets,利用资源管理所需的素材
>
> 资源器简化,关闭资产库和3d场景构建(限制引擎的使用场景)
>
> 网络上所需的相关游戏素材(前期建议可以使用公开免费游戏素材)



### 二.人物设计

> 节点:CharacterBody2D(Player) // Sprite2D/CollisionShape2D
>
> 1. 像素人物的模糊原因(项目>项目设置>渲染>纹理>Nearest)
> 2. 参数折叠取消(编辑>编辑器设置>Disable Folding)

- #### 脚本设计

1.在CharacterBody2D(Player)下选择创建脚本,选择Node模板

```GDS
extends Node2D


# Called when the node enters the scene tree for the first time.
# 当节点第一次进入场景树时，会调用_ready()函数!
func _ready() -> void:
	pass # Replace with function body.


# Called every frame. 'delta' is the elapsed time since the previous frame.
# 称为每一帧。'delta'是自上一帧以来经过的时间。
func _process(delta: float) -> void:
	pass

# 称为物理帧,在主循环的物理处理步骤中调用。物理处理的帧率与物理同步，即 delta 参数通常不变（例外见下文）。delta 的单位为秒。启用物理处理后才会调用该方法
func _physics_process(delta: float) -> void:
    pass
```

> 项目>项目设置>按键映射(单例) 在其中自定义按键的映射属性(项目中有其本身的项目映射)
>
> 创建关于人物移动的映射属性(上/下/左/右)

2.创建人物的位置矢量

```GDS
extends CharacterBody2D

const MAX_SPEED=200
# Called when the node enters the scene tree for the first time.
func _ready() -> void:
	pass # Replace with function body.


# Called every frame. 'delta' is the elapsed time since the previous frame.
func _process(delta: float) -> void:
	var movement=palyer_movement().normalized() #矢量单位化

	
func palyer_movement():
	var x_movement=Input.get_action_strength("ui_right") - Input.get_action_strength("ui_left")
	var y_movement=Input.get_action_strength("ui_down") - Input.get_action_strength("ui_up")
    #根据刚才的映射找到人物运动的每个方向上的速度
	return Vector2(x_movement , y_movement)

```

3.修改窗口的长宽高

{% gallery %}

![]([window_setting.png (1204×747)](https://raw.githubusercontent.com/ASACAY/asacay.github.io/refs/heads/main/photos/window_setting.png)

{% endgallery %}
