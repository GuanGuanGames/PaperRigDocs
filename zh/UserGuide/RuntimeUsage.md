# PaperRig 运行时使用指南  

本指南介绍如何在 **游戏运行时** 通过 **蓝图** 使用 PaperRig 插件来控制角色的表情、动作或 Layer。  

PaperRig 在运行时只需要：  

✅ **一个挂载 Skeletal Mesh 的 Actor**  
✅ **PaperRigControlComponent 组件**  

即可直接使用蓝图节点控制。  

---

## 🎯 PaperRig 控制策略  

PaperRig 在运行时对每个控制器采用以下 **优先级策略**：  

1. **优先使用蓝图/代码设置的控制器值**  
2. **如果控制器值为 `0`，则自动回退到动画蓝图/动画曲线的值**  

> ✅ **设计师只需记住**：  
> - 想要完全覆盖动画 → **直接给控制器设置非 0 的值**  
> - 想恢复动画曲线 → **把控制器值重置为 0**  

示例：  
- `Set Control Value("MouthSmile", 0.8)` → 立即覆盖动画  
- `Set Control Value("MouthSmile", 0.0)` → 自动使用动画曲线  

---


## 1. 前置准备  

1. **确保角色有 Skeletal Mesh**  
   - 例如 `SK_Character`  

2. **为角色添加 PaperRigControlComponent**  
   - 打开角色蓝图 → `Add Component` → 搜索 **PaperRigControlComponent**  
   - 保存并编译  

完成后，该 Actor 就能在运行时使用所有 PaperRig 蓝图节点。  
蓝图接口请参考：[📘 Blueprint API 文档](../API/BlueprintAPI.md)

