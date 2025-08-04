# PaperRig 使用手册（QuickStart）

---

## 1. PaperRig 是什么？

**PaperRig** 是一个专为 2D 动画设计的系统，允许你在 **运行时** 通过蓝图或动画控制角色的 **表情、动作和图层（如服装、配件）**。

它基于 Unreal Engine 的 Skeletal Mesh 系统，并对编辑器进行了 2D 动画的适配扩展，支持以下功能：

- ✅ 顶点编辑（基于 LOD0 的变形）
- ✅ 基于动画曲线 / Morph Target 的图层切换系统
- ✅ 骨骼权重与绑定操作的可视化编辑
- ✅ 图层分组管理、预览控制器支持

---

## 2. 准备工作

在开始之前，请确保以下条件已经满足：

- ✅ 项目中已正确安装并启用 PaperRig 插件
- ✅ Mesh 顶点为 2D 排布，适合面片动画
- ✅ 使用 Unreal Engine 5.6 或更高版本
- ✅ 已准备好符合规范的 PSD 文件

---

## 3. 导入 PSD 并创建 PaperRigMesh

### PSD 文件规范：

1. **禁止同名图层**（即使在不同组内也不允许）
2. 推荐使用规则命名，例如：`hat_01`, `hat_02`, `body_01`
3. 支持图层组嵌套，但层级不宜过深

### 导入步骤：

1. 将 PSD 文件拖入 Content Browser
2. 右键点击 PSD，选择 **Create Paper Rig Mesh**
3. 系统将自动解析图层并生成对应骨骼模型（Skeletal Mesh）

---

## 4. 编辑 PaperRig Mesh（骨骼绑定与图层设置）

### 添加骨骼与绑定顶点：

1. 打开生成的 Skeletal Mesh
2. 切换到编辑模式
3. 选择 **PaperRig** 工具集
4. 使用 **Edit Vertex** 编辑图层顶点信息
5. 使用 **Edit Layer Control** 设置图层组控制器

### 图层分组与可见性控制：

1. 使用 **Edit Layer Control** 创建图层组控制器（Layer Group Control）
2. 添加关键帧（Key）
3. 为每个关键帧设置图层的可见性状态

> 更详细的编辑器操作请参考：[📘 EditorUsage 文档](./EditorUsage.md)

---

## 5. 图层控制（基于动画曲线 / Morph Target）

创建好的图层组控制器支持以下控制方式：

- 在动画序列中通过 **动画曲线驱动 Morph Target**
- 在蓝图中调用 API 实时修改控制器值（详见下节）
- 使用任何支持 Morph Target 的原生 Unreal 功能

控制器的数值决定图层的显示状态，例如：

- 值为 `0` 显示 `hat_01`
- 值为 `1` 显示 `hat_02`

你可以在编辑器中自由定义图层组行为与映射逻辑。

---

---

## 6. 使用动画序列与曲线控制图层

你可以在动画序列（AnimSequence）中添加自定义曲线，通过曲线数值驱动 PaperRig 的控制器，实现动态换装、表情切换等效果。

### 步骤如下：

1. 打开角色的 AnimSequence（或创建一个新的）
2. 点击 **添加曲线（+）**，输入控制器名称（必须与 PaperRig 控制器名称一致）
3. 在时间轴上设置关键帧，定义控制器值的变化，例如：
   - 时间 0.0：值为 0（显示 hat_01）
   - 时间 1.0：值为 1（切换到 hat_02）
4. 播放该 AnimSequence 即可驱动控制器数值，并实时预览图层切换效果。
---



## 7. 蓝图 API 控制（简要）

你可以在蓝图中通过如下函数控制图层或控制器：

```cpp
SetPaperRigControlValue(Actor, ControlName, Value)
```

- **Actor**：目标角色实例
- **ControlName**：控制器名称
- **Value**：控制器数值

> 详细请参考：[📘 运行时 文档](./RuntimeUsage.md)     
> 更多蓝图接口请参考：[📘 Blueprint API 文档](../API/BlueprintAPI.md)

---

## 8. 预览与运行时效果

无论在编辑器视口、运行时，还是资产预览窗口中，图层都将随骨骼动画实时变形，并根据控制器数值做出响应。

你还可以结合 **Sequencer** 或 **Blueprint** 进行动态控制，实现：

- 换装系统
- 表情切换
- 剧情动画等效果

---

## 🎉 恭喜！

你已经完成了 PaperRig 的基本搭建流程！  
接下来你可以尝试加入动画、控制逻辑，或导入更多 PSD 资源来扩展你的 2D 动画角色系统。
