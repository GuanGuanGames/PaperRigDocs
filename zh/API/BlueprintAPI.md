# PaperRig Blueprint API  

本页列出 **PaperRig 提供的蓝图接口**，方便在 Blueprint 中控制 PaperRig 的参数和 Layer。  

PaperRig 提供两种方式：  

- ✅ **全局静态函数** → `PaperRigFunctionBlueprintLibrary`（蓝图中会完整显示函数名）  
- ✅ **组件函数** → `PaperRigControlComponent`（蓝图中不会显示 BP_ 前缀）  

---

## ✅ 方式 1：全局函数（`UPaperRigFunctionBlueprintLibrary`）  

这些是 **无需直接访问组件** 的全局函数，传入目标 Actor 即可，蓝图节点名称和这里一致。  

---

### 📌 Get PaperRig Control Component  

**作用**  
获取目标 Actor 上的 `PaperRigControlComponent`  

**参数**  
- `InActor`：要获取组件的 Actor  

**返回值**  
- `PaperRigControlComponent`，如果 Actor 有此组件则返回，否则为空  

---

### 📌 Set PaperRig Control Value  

**作用**  
设置指定 Control 的值  

**参数**  
- `InActor`：目标 Actor  
- `ControlName`：控制器名称  
- `NewValue`：新的值  

---

### 📌 Set PaperRig Control Values  

**作用**  
一次性批量设置多个 Control 的值  

**参数**  
- `InActor`：目标 Actor  
- `ControlValues`：`ControlName → Value` 的映射表  

---

### 📌 Get PaperRig Control Value  

**作用**  
获取指定 Control 当前值  

**参数**  
- `InActor`：目标 Actor  
- `ControlName`：控制器名称  

**返回值**  
- `float` 当前值  

---

### 📌 Get PaperRig All Control Values  

**作用**  
获取目标 Actor 上所有 Control 的当前值  

**参数**  
- `InActor`：目标 Actor  

**返回值**  
- `ControlName → Value` 的映射表  

---

### 📌 Get PaperRig All Control Names  

**作用**  
获取目标 Actor 所有 Control 的名称列表  

**返回值**  
- 所有控制器名称  

---

### 📌 Reset PaperRig Control Value  

**作用**  
重置指定 Control 为默认值  

**参数**  
- `InActor`：目标 Actor  
- `ControlName`：控制器名称  

---

### 📌 Reset PaperRig All Controls  

**作用**  
重置所有 Control 为默认值  

**参数**  
- `InActor`：目标 Actor  

---

### 📌 Get PaperRig All Layer Names  

**作用**  
获取目标 Actor 上所有 Layer 的名称  

**参数**  
- `InActor`：目标 Actor  

**返回值**  
- 所有 Layer 名称  

---

## ✅ 方式 2：组件函数（`PaperRigControlComponent`）  

如果 Actor 已经挂载了 `PaperRigControlComponent`，可以直接在 Blueprint 里调用下列函数。  

（蓝图中不会显示 `BP_` 前缀，所以这里直接用最终显示的名字）  

---

### 📌 Set Control Value  

**作用**  
设置指定 Control 的值  

**参数**  
- `Name`：Control 名称  
- `NewValue`：新的值  

---

### 📌 Get Control Value  

**作用**  
获取指定 Control 的当前值  

**参数**  
- `Name`：Control 名称  

**返回值**  
- 当前值  

---

### 📌 Get All Control Values  

**作用**  
获取该组件下所有 Control 的值  

**返回值**  
- `ControlName → Value` 的映射表  

---

### 📌 Get All Control Names  

**作用**  
获取该组件下所有 Control 的名称  

**返回值**  
- 所有 Control 名称  

---

### 📌 Reset Control Value  

**作用**  
重置指定 Control 为默认值  

**参数**  
- `Name`：Control 名称  

---

### 📌 Reset All Controls  

**作用**  
重置所有 Control 为默认值  

---

### 📌 Get All Layer Names  

**作用**  
获取该组件下所有 Layer 的名称  

**返回值**  
- 所有 Layer 名称  

---

## ✅ 使用示例  

- **修改单个控制值（全局函数）**  
  - `Set PaperRig Control Value (Actor, "EyeBlink_L", 1.0)`  

- **批量设置多个控制值（全局函数）**  
  - `Set PaperRig Control Values (Actor, {"EyeBlink_L": 1.0, "MouthSmile": 0.5})`  

- **直接使用组件函数修改控制值**  
  - `Set Control Value("EyeBlink_L", 1.0)`  

- **重置所有控制**  
  - `Reset All Controls()`  

- **获取所有控制器名称并遍历**  
  - `ForEach Get All Control Names → Do Something`  

- **获取所有 Layer 名称**  
  - `LayerNames = Get All Layer Names()`  

---

## ✅ 什么时候用全局函数 vs 组件函数？  

- **全局函数**  
  - 适合**不知道 Actor 是否有组件**的场景，内部会自动查找  
  - 蓝图节点名字是 `Set PaperRig Control Value` 这种完整形式  

- **组件函数**  
  - 适合**已经持有组件引用**的场景，蓝图节点名字更简洁  
  - 蓝图节点名字是 `Set Control Value`  

两种方式功能完全相同，可以根据实际需求选择  

---

## 注意事项  

- 需要确保 **Actor 已挂载 `PaperRigControlComponent`**，否则函数无效  
- `ControlName` 区分大小写  
- 可以与 **C++ API** 混用  

---
