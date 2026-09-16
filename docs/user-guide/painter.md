# Substance 3D Painter

Select Blender meshes and click **Create Painter Project**. REVO
Bridge sends USD to Painter and returns exported textures to Blender materials.

Install the Painter helper from **Integrations**, restart Painter, and enable
`revo_bridge_painter` from Painter's **Python** menu.

![REVO Bridge plugin location in Painter](../assets/img/Substancepainter_PluginLocation.png){ .doc-shot }

Use **File > REVO Bridge: Export Textures to Blender** when the project is ready.
Blender auto-imports by default. **Import Textures from Painter** reapplies the
latest Painter export.

![REVO Bridge command in Painter's File menu](../assets/img/Substancepainter_FileMenu.png){ .doc-shot }

The export uses the channels in the open Painter project. Normals return as
OpenGL for Blender. Blender's USD export turns Principled BSDF materials into
Painter Texture Sets, one per material.

REVO Bridge updates matching materials. For renamed Texture Sets, it creates
and assigns a Blender material with the Painter name.

## Settings (Utilities)

![Substance 3D Painter settings](../assets/img/Substancepainter_settings.png){ .doc-shot }

- Painter executable path
- Launch Painter on export
- Existing `.spp` project
- Texture export folder
- Split by UDIM (Legacy)
- Use UV Tiles
- Normal Map Format
- Compute Tangent Space Per Fragment
- Auto-import textures from Painter
- Enable remote scripting at launch
- UE5 ACES 2.0 Color Setup

Leave **Existing Project** empty for a new project. Select an `.spp` to reuse
its setup, such as a specific shader. REVO Bridge opens a working copy in the
**Texture Export Folder** (default: `Textures/Substance` beside the `.blend`).

## Use a custom Painter project

Save the project, select it as **Existing Project**, then click **Create /
Update Painter Project**.

## UE5 ACES 2.0 Color Setup

Enabled by default for new projects. Requires Painter **11.0.3** or newer.
Existing projects keep their own color-management settings.
