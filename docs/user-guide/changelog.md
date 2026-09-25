# Changelog

## 1.1.1

### Fixed

- Export to Toolbag, Create Bake Project and sends to ZBrush, Maya or Painter
  could stop working with no error. Windows Storage Sense or a temp cleaner
  deleted the bridge's private token from `%TEMP%\REVO_Bridge`. The bridge now
  restores the token itself, and Toolbag exports are never dropped silently.
- **Restart** in **Integrations** could not stop a bridge server in that state.
  It now replaces it, and Blender does the same when it starts.

## 1.1.0

### New

- Substance 3D Painter bake projects: **Create Low/Low Bake** and **Create
  Low/High Bake**. Name meshes `_low` / `_high` and REVO Bridge sets up a new
  Painter project with the high mesh loaded in the baker, your chosen mesh maps
  enabled and By Mesh Name matching for multiple groups. You bake in Painter.
  See [Bake Project](painter.md#bake-project).
- Painter bake settings under **Utilities**: Bake Resolution, Match By Mesh Name
  and all ten mesh maps.
- **Help** tab with links to this documentation, Discord and ArtStation.

### Improved

- Redesigned sidebar: icon tabs on the left, and each app (ZBrush, Toolbag,
  Painter, Maya) in its own collapsible section, collapsed by default. Click
  anywhere on a header to open it. See [User Interface](user-interface.md).
- Color-coded sections make the panel easy to scan, so you can quickly find the
  tools you need. Each app keeps the same color and order on every tab.
- Taller, grouped Install / Update and Uninstall buttons on the
  **Integrations** tab.

### Fixed

- Marmoset Toolbag showed the REVO Bridge plugin twice under **Edit > Plugins**.
  Install / Update now installs a single copy and removes the extra one.
- Substance 3D Painter now shows the real error when project creation fails.

## 1.0.0

Initial public release.

- Exchange meshes, rigs, scenes, textures and materials between Blender, ZBrush,
  Maya, Marmoset Toolbag 5 and Substance 3D Painter.
- Windows 10 / 11, x64 and ARM64.
- Supports Blender 4.2 and newer.
- Automatic import from Maya, ZBrush, Toolbag and Painter.
- Maya rig exchange through FBX or USD, including joints, skinning, blend shapes
  and animation.
- Substance 3D Painter projects with texture round-trips back to Blender
  materials, UDIMs and UE5 ACES 2.0 color setup.
- Toolbag Baker project setup with presets, maps and material workflows.
- One-click install, update and uninstall of every DCC plugin.
