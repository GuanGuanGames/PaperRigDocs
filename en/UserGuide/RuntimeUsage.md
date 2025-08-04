# 🕹️ PaperRig Runtime Usage Guide

This guide explains how to use the **PaperRig** plugin via **Blueprint** during **game runtime** to control character expressions, motions, or layers.

To use PaperRig at runtime, you only need:

✅ **An Actor with a Skeletal Mesh**  
✅ **A PaperRigControlComponent attached to it**

Once set up, you can directly use the runtime Blueprint nodes.

---

## 🎯 Runtime Control Logic

At runtime, PaperRig applies the following **priority logic** for each controller:

1. **Controller values set via Blueprint/code take precedence**
2. **If the controller value is `0`, it automatically falls back to the animation blueprint or curve**

> ✅ **As a designer, just remember:**  
> - To override the animation → **Set a non-zero controller value**  
> - To restore animation curve → **Set the controller value back to `0`**

Examples:

- `Set Control Value("MouthSmile", 0.8)` → Overrides animation immediately  
- `Set Control Value("MouthSmile", 0.0)` → Reverts to animation curve

---

## 1️⃣ Setup Steps

1. **Ensure the character has a Skeletal Mesh**
   - For example: `SK_Character`

2. **Add PaperRigControlComponent**
   - Open the character Blueprint → Click `Add Component` → Search for **PaperRigControlComponent**
   - Add and compile the Blueprint

Once set up, the Actor is ready to use all PaperRig runtime Blueprint nodes.  
For Blueprint interface details, see: [📘 Blueprint API Reference](../API/BlueprintAPI.md)
