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

  1. 在CharacterBody2D(Player)下选择创建脚本,选择Node模板

     ```python
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

     