# PaperRig QuickStart Guide

---

## 1. What is PaperRig?

**PaperRig** is a system specifically designed for 2D animation, allowing you to control a character’s **expressions, actions, and layers (e.g., outfits, accessories)** at **runtime** via Blueprints or animations.

It is built on Unreal Engine’s Skeletal Mesh system, with extended editor support for 2D animation. Key features include:

- ✅ Vertex editing (based on LOD0 deformation)
- ✅ Layer switching system driven by animation curves / Morph Targets
- ✅ Visual editing of bone weights and binding
- ✅ Layer group management and preview controller support

---

## 2. Prerequisites

Before you begin, make sure the following requirements are met:

- ✅ PaperRig plugin is correctly installed and enabled in your project
- ✅ Mesh vertices are laid out in 2D, suitable for flat surface animation
- ✅ Unreal Engine 5.6 or above
- ✅ A properly structured PSD file is ready

---

## 3. Import PSD and Create PaperRigMesh

### PSD File Guidelines:

1. **No duplicate layer names** (even if in different groups)
2. Recommended naming conventions: e.g., `hat_01`, `hat_02`, `body_01`
3. Layer groups are supported, but deep nesting is discouraged

### Import Steps:

1. Drag your PSD file into the Content Browser
2. Right-click the PSD and select **Create Paper Rig Mesh**
3. The system will automatically parse layers and generate a corresponding Skeletal Mesh

---

## 4. Edit PaperRig Mesh (Bone Binding & Layer Settings)

### Add Bones and Bind Vertices:

1. Open the generated Skeletal Mesh
2. Switch to edit mode
3. Select the **PaperRig** toolset
4. Use **Edit Vertex** to assign vertex data for each layer
5. Use **Edit Layer Control** to configure layer group controllers

### Grouping Layers & Visibility Control:

1. Use **Edit Layer Control** to create a Layer Group Controller
2. Add keyframes (Keys)
3. Set layer visibility state for each key

> For more detailed editor usage, see: [📘 EditorUsage Documentation](./EditorUsage.md)

---

## 5. Layer Control (via Animation Curve / Morph Target)

Layer group controllers support multiple control methods:

- Drive Morph Targets via animation curves in AnimSequence
- Modify controller values at runtime via Blueprint API (see next section)
- Use any Unreal-native Morph Target control method

Controller values determine which layer is shown. For example:

- Value `0` shows `hat_01`
- Value `1` shows `hat_02`

You are free to define the behavior and mapping logic for each layer group.

---

## 6. Use Animation Sequences & Curves to Control Layers

You can use animation sequences (AnimSequence) with custom curves to drive PaperRig controllers—great for outfit switching, expression changes, etc.

### Steps:

1. Open the character’s AnimSequence (or create a new one)
2. Click **Add Curve (+)** and enter the controller name (must match PaperRig controller)
3. Add keyframes on the timeline to define value changes:
   - Time 0.0: Value = 0 (show `hat_01`)
   - Time 1.0: Value = 1 (switch to `hat_02`)
4. Play the AnimSequence to preview layer switching in real time

---

## 7. Blueprint API Control (Quick Overview)

You can control layers or controllers via Blueprint using this function:

```cpp
SetPaperRigControlValue(Actor, ControlName, Value)
```

- **Actor**: Target character instance
- **ControlName**: Controller name
- **Value**: Controller value

> For details, see: 📘 Runtime Usage Documentation
> For more Blueprint functions, see: 📘 Blueprint API Documentation

## 8. Preview & Runtime Behavior
Whether in editor viewport, during runtime, or in asset preview, layers will deform with skeletal animation and respond to controller values in real time.

You can also use **Sequencer** or **Blueprint** to dynamically control them and create:

- Outfit systems
- Expression switching
- Story-driven animation

## 🎉 Congratulations!
You’ve completed the basic PaperRig setup!
Next, try adding animations, control logic, or import more PSD assets to expand your 2D animation character system.