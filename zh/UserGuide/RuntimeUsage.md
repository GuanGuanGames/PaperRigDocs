# 🕹️ PaperRig 运行时使用指南

本指南介绍如何在 **游戏运行时** 使用 **蓝图** 控制 PaperRig 插件，以驱动角色的表情、动作或 Layer（图层）。

在运行时使用 PaperRig 只需要满足以下两个条件：

✅ **一个绑定了 Skeletal Mesh 的角色 Actor**  
✅ **添加 PaperRigControlComponent 组件**

完成后即可在蓝图中使用控制节点。

---

## 🎯 控制策略说明

在运行时，PaperRig 控制器的值遵循以下 **优先级策略**：

1. **优先使用蓝图或代码显式设置的控制器值**
2. **若控制器值为 `0`，则自动回退使用动画蓝图中的动画曲线值**

> ✅ **记住一条设计原则即可：**  
> - 想要覆盖动画 → **设置非零控制器值**  
> - 想恢复动画 → **设置控制器值为 `0`**

示例用法：

- `Set Control Value("MouthSmile", 0.8)` → 立即覆盖动画中的值  
- `Set Control Value("MouthSmile", 0.0)` → 恢复动画曲线控制效果

---

## 1️⃣ 前置准备

1. **确保角色拥有 Skeletal Mesh**
   - 例如：`SK_Character`

2. **添加 PaperRigControlComponent**
   - 打开角色蓝图 → 点击 `Add Component` → 搜索 **PaperRigControlComponent**
   - 添加并编译蓝图

完成以上步骤后，角色即可在运行时使用所有 PaperRig 的蓝图控制接口。  
详细蓝图接口请参考：[📘 Blueprint API 文档](../API/BlueprintAPI.md)
