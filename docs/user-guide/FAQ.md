# FAQ

## General

### Q: Is this a live-link?
No. Each send writes files to the transfer folder. You export, work in the other DCC, then send back.

### Q: Does it work on macOS?
No. REVO Bridge is Windows only.

### Q: Where are the transfer files?
Default: `%TEMP%\REVO_Bridge`. Open it from **Utilities > Open Transfer Folder**. A custom parent folder in Preferences still uses a `REVO_Bridge` subfolder.

### Q: Does the server talk to the internet?
No. It listens on `127.0.0.1` only (default port `58772`). Commands need a private token in the transfer folder. Browser-origin requests are rejected.

### Q: Who is responsible if a file is overwritten?
Use copies and keep backups of projects you care about. In Painter, **Save**
overwrites the open project.

---

## Installation

### Q: I see REVO Bridge in ZBrush's plugin folder as a `.txt`, but nothing in ZPlugin
ZBrush 2026 loads compiled `.zsc` files, not `.txt`. Install from Blender **Integrations** so `REVO_Bridge.zsc` is copied, then restart ZBrush.

### Q: Maya has no shelf after install
Restart Maya. Confirm Plugin Manager has `REVO_Bridge.py` loaded. The installer follows the Maya version in the executable path you set.

### Q: Maya shows Color Management Initialization failed
Maya does not use Blender's color config. Close Maya, **Restart** the bridge server in Integrations, then launch Maya from Blender again. Blender 5.2 was passing its OCIO 2.5 file into Maya, which only understands OCIO 2.4.

### Q: I updated the Blender ZIP but Toolbag still behaves like the old plugin
Run **Install / Update Toolbag Plugin**, then **fully quit** Toolbag (not just the scene) and Create Bake Project again.

### Q: Where is the Painter plugin?
Install it from Blender's **Integrations**, restart Painter, then enable
`revo_bridge_painter` in Painter's **Python** menu.

---

## Toolbag Baker

### Q: High and Low are in the baker but the maps are blank
Turn on **Use Hidden Meshes**. Toolbag Quick Loader hides the High group after import. With that option off, the high poly is ignored and the bake writes empty maps. It is enabled by default in the plugin.

### Q: Export Format says USD but Bake Project imports an FBX
That is expected. **Export Format** is for **Export to Toolbag** only. **Create Bake Project** always uses FBX so Quick Loader can group `_low` / `_high` meshes.

### Q: Create Bake Project only opens Toolbag and does nothing
Quit Toolbag completely, install this ZIP, then Create Bake Project again. Toolbag has to boot with the REVO Bridge Python script so it can read the bake request.

### Q: WinError 5 / access denied on the bake folder
`//Bakes/` is blend-relative. Save the Blender file, or set an absolute bake output folder. Unsaved files fall back to the transfer folder.

### Q: Validate fails
Names must look like `asset_low` / `asset_high`. Each group needs both roles. Low meshes need geometry and a UV map. Only the selected meshes are exported.

### Q: Cage looks huge or tiny
Cage offsets are authored in Blender units and converted to Toolbag centimetres on export. Start with the default max offset (`0.02`) and **Estimate Cage Offset**.

---

## Send and receive

### Q: Why does Export to Toolbag open the REVO Bridge plugin, but Import from Toolbag does not?
Blender starts the plugin when it launches Toolbag. For an existing Toolbag
session, open **Edit > Plugins > Revo_Bridge**, then use **Export Scene to
Blender**. See [Send and receive](toolbag.md#send-and-receive).

### Q: Does ZBrush auto-import from Blender?
No. ZScript has no idle timer that is safe for this. Always click **Receive from Blender**. Send the other way with **Send to Blender**; Blender can auto-import.

### Q: Does Maya auto-import both ways?
Yes, after the Maya plugin is installed and Maya has been restarted.

### Q: ZBrush overwrote the wrong SubTool
Receive always replaces the **active** SubTool. Select the correct one before you click **Receive from Blender**. ZBrush does not auto-import.

### Q: Why did Maya export the whole child hierarchy?
That is intentional: Maya export now preserves selected characters and rigs. Select
only a mesh if you want only that branch, or select the character group / rig root
and meshes for a complete character transfer. Use FBX by clicking the shelf button,
or right-click it and choose USD.

### Q: Painter textures did not come back to Blender
Install the Painter plugin from Blender's **Integrations**, restart Painter, and
enable `revo_bridge_painter` from Painter's **Python** menu. Then use
**File > REVO Bridge: Export Textures to Blender**. Blender auto-imports by
default. **Import Textures from Painter** reapplies the latest successful export
and reloads image files; it has nothing to import until Painter has sent one.
Texture Set names may be changed: Blender creates and assigns a corresponding
material when no existing material matches.

### Q: Painter overwrote my starter file or an old painting
REVO Bridge opens a working copy of the `.spp` selected in **Existing Project**.
It is stored in the **Texture Export Folder** (default: `Textures/Substance`
beside the Blender file) and named after the Blender file. **Save** in Painter
overwrites that working copy. See [Use a custom Painter project](painter.md#use-a-custom-painter-project).

### Q: Why did duplicating the Painter project take so much disk space?
On the first launch, REVO Bridge makes a full working copy of the `.spp` set in
**Existing Project**. It is not a shortcut, so it needs about the same disk
space as the source project. Later launches reuse that copy.

---

## If send or receive stops

1. Confirm the local server shows as running in the sidebar.
2. Open **Integrations**, choose **Check Status**, then **Restart** if needed.
3. Confirm the DCC executable path in **Utilities**.
4. Confirm that DCC's plugin was installed and the application was restarted.
5. Use **Clear Pending Data** or the per-DCC clear button if a stale import is blocking a new send.
6. Use **Open Transfer Folder** to inspect `%TEMP%\REVO_Bridge`.
