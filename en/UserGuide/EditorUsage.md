# 🛠️ Editor Panel Usage Guide

---

## 1. Overview

PaperRig provides a set of editor panels tailored for 2D skeletal animation, covering layer binding, vertex editing, and layer group controllers.  
These tools allow efficient creation of layered control systems with real-time animation preview, enhancing workflow visualization and interactivity.

---

## 2. How to Open

Steps to open the editor panel:

1. Double-click any generated **PaperRig Skeletal Mesh** asset;  
2. Click the `Editing Tools` button in the top toolbar to enter the skeletal mesh editor;  
3. Select **PaperRig** from the toolset list to enable related editing features.

---

## 3. Vertex Editing (Edit Vertex)

Vertex editing is essential for defining layer shapes and bone binding. It allows manual adjustment of the layer geometry.

### 3.1 Selecting a Layer

- Click a layer from the left panel list to select it;  
- The selected layer outline highlights in the viewport;  
- Vertex editing is disabled if no layer is selected.

### 3.2 Editing Vertex Shape

- **Move Vertices**: Click and drag vertices to reposition;  
- **Add Vertices**: Double-click on edges to insert new vertices;  
- **Delete Vertices**: Select vertices and press `Delete` key.

Changes update the layer shape in real time, affecting binding and animation.

### 💡 Tips

- Use `Ctrl + Z` to undo;  
- Mouse wheel zooms the viewport for fine adjustments;  
- The four corner vertices of layer boundaries are not editable; vertices can only be added or removed within the bounds.

---

## 4. Layer Controller (Edit Layer Control)

Layer controllers manage layer visibility and animation keyframes. They serve as a bridge between the animation system and Blueprint logic, enabling dynamic layer switching and bone-driven behavior to enhance character expressiveness.

### 4.1 Panel Overview

- **Controller Name**: Name of the controller;  
- **Operation**: Edit mode (New or Edit);  
- **Add Key / Remove Key**: Add or delete keyframes;  
- **Slider & Range**: Controller value range and live adjustment;  
- **Layer List**: Shows all controllable layers, toggle visibility by clicking 👁️ icon.

### 4.2 Adding a New Controller

1. Set `Operation` to New;  
2. Enter the controller name in the `Controller Name` field.

### 4.3 Adding and Editing Keyframes

- Move timeline to target frame;  
- Click `Add Key` to add a keyframe;  
- Adjust controller value via slider or input;  
- Toggle layer visibility by clicking 👁️;  
- Remove keyframes by clicking `Remove Key`;  
- Right-click layer to add/remove it from keyframes.

### 4.4 Parameters

- **Range**: Defines controller value range (e.g., 0 to 1);  
- **Operation**: Determines current edit mode (add or modify).

### 4.5 Usage

- **Animation Driven**: Use curves in animation sequences to control layers for dynamic expression;  
- **Blueprint Integration**: Modify controller values at runtime in Blueprints for interactive logic (outfit changes, expressions, etc.);  
- **Visual Debugging**: Preview controller effects live in the editor for debugging and fine-tuning.

### 💡 Recommendations

- Use unique controller names for easy Blueprint referencing;  
- Combine multiple controllers for complex layered animations.

---

## 5. FAQ

### • Layers Not Applying

Try reimporting the PSD file and rebuilding the skeletal mesh:

1. Right-click the PSD file → Select “Reimport”;  
2. After processing, recreate the skeletal mesh.

The system will sync added or removed layers while keeping unchanged ones.

**Note**: Changes in pixel content require rebuilding vertices; deleted layers are removed from the mesh.

### • Unable to Edit Vertices

Make sure a layer is selected and you are in `Edit Vertex` mode.

### • Controller Not Responding to Animation Curves

Verify the controller name exactly matches the curve name and that keyframes are set for the controller.
