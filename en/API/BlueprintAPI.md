# PaperRig Blueprint API

This page lists the **Blueprint interfaces provided by PaperRig**, allowing you to control PaperRig parameters and layers within Blueprints.

PaperRig offers two approaches:

- ✅ **Global Static Functions** → `PaperRigFunctionBlueprintLibrary` (function names are fully visible in Blueprint)
- ✅ **Component Functions** → `PaperRigControlComponent` (function names do not show the BP_ prefix in Blueprint)

---

## ✅ Method 1: Global Functions (`UPaperRigFunctionBlueprintLibrary`)

These are **global functions that do not require direct access to the component**. Simply pass in the target Actor. Blueprint node names match those listed here.

---

### 📌 Get PaperRig Control Component

**Purpose**  
Retrieve the `PaperRigControlComponent` from the target Actor.

**Parameters**  
- `InActor`: The Actor to retrieve the component from

**Return Value**  
- `PaperRigControlComponent`, returns the component if present, otherwise null

---

### 📌 Set PaperRig Control Value

**Purpose**  
Set the value of a specified Control.

**Parameters**  
- `InActor`: Target Actor  
- `ControlName`: Name of the controller  
- `NewValue`: New value to set

---

### 📌 Set PaperRig Control Values

**Purpose**  
Set multiple Control values at once.

**Parameters**  
- `InActor`: Target Actor  
- `ControlValues`: A map of `ControlName → Value`

---

### 📌 Get PaperRig Control Value

**Purpose**  
Get the current value of a specified Control.

**Parameters**  
- `InActor`: Target Actor  
- `ControlName`: Name of the controller

**Return Value**  
- `float`: Current value

---

### 📌 Get PaperRig All Control Values

**Purpose**  
Retrieve all current Control values from the target Actor.

**Parameters**  
- `InActor`: Target Actor

**Return Value**  
- A map of `ControlName → Value`

---

### 📌 Get PaperRig All Control Names

**Purpose**  
Get a list of all Control names from the target Actor.

**Return Value**  
- List of all controller names

---

### 📌 Reset PaperRig Control Value

**Purpose**  
Reset a specified Control to its default value.

**Parameters**  
- `InActor`: Target Actor  
- `ControlName`: Name of the controller

---

### 📌 Reset PaperRig All Controls

**Purpose**  
Reset all Controls to their default values.

**Parameters**  
- `InActor`: Target Actor

---

### 📌 Get PaperRig All Layer Names

**Purpose**  
Get all Layer names from the target Actor.

**Parameters**  
- `InActor`: Target Actor

**Return Value**  
- List of all Layer names

---

## ✅ Method 2: Component Functions (`PaperRigControlComponent`)

If the Actor already has a `PaperRigControlComponent` attached, you can directly call the following functions in Blueprint.

(Blueprint nodes do not show the `BP_` prefix, so names listed here match what appears)

---

### 📌 Set Control Value

**Purpose**  
Set the value of a specified Control.

**Parameters**  
- `Name`: Control name  
- `NewValue`: New value to set

---

### 📌 Get Control Value

**Purpose**  
Get the current value of a specified Control.

**Parameters**  
- `Name`: Control name

**Return Value**  
- Current value

---

### 📌 Get All Control Values

**Purpose**  
Retrieve all Control values from this component.

**Return Value**  
- A map of `ControlName → Value`

---

### 📌 Get All Control Names

**Purpose**  
Get all Control names from this component.

**Return Value**  
- List of all Control names

---

### 📌 Reset Control Value

**Purpose**  
Reset a specified Control to its default value.

**Parameters**  
- `Name`: Control name

---

### 📌 Reset All Controls

**Purpose**  
Reset all Controls to their default values.

---

### 📌 Get All Layer Names

**Purpose**  
Get all Layer names from this component.

**Return Value**  
- List of all Layer names

---

## ✅ Usage Examples

- **Modify a single control value (global function)**  
  - `Set PaperRig Control Value (Actor, "EyeBlink_L", 1.0)`

- **Set multiple control values at once (global function)**  
  - `Set PaperRig Control Values (Actor, {"EyeBlink_L": 1.0, "MouthSmile": 0.5})`

- **Directly modify control value using component function**  
  - `Set Control Value("EyeBlink_L", 1.0)`

- **Reset all controls**  
  - `Reset All Controls()`

- **Get all controller names and iterate**  
  - `ForEach Get All Control Names → Do Something`

- **Get all Layer names**  
  - `LayerNames = Get All Layer Names()`

---

## ✅ When to Use Global vs Component Functions?

- **Global Functions**  
  - Ideal when you're **not sure if the Actor has the component**; it will auto-detect internally  
  - Blueprint node names are in full form like `Set PaperRig Control Value`

- **Component Functions**  
  - Ideal when you **already have a reference to the component**; node names are more concise  
  - Blueprint node names are like `Set Control Value`

Both approaches offer the same functionality—choose based on your workflow needs.

---

## Notes

- Make sure the **Actor has a `PaperRigControlComponent` attached**, or functions will not work  
- `ControlName` is case-sensitive  
- Can be used alongside the **C++ API**