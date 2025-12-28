# AutoTuner — Dynamic authority balancing for smoother flight

AutoTuner dynamically balances **engine gimbal**, **control surface authority**, and **reaction wheel torque** based on your craft and changing flight conditions—so rockets feel **less twitchy** and **more stable** without constant manual tweaking.

It’s designed as a **quality-of-life flight handling tool**. It does **not** replace SAS or autopilots; it tunes control authority so manual flight and SAS are smoother.

---

## Features

- **Dynamic authority tuning** for:
  - Engine gimbals
  - Reaction wheels
  - Control surfaces (when present)
- **Fine Mode** for delicate control (e.g., circularization tweaks, rendezvous, docking without RCS)
  - Throttle limiting + adaptive wheel authority behavior
- **High‑TWR handling reduction** to prevent oversteer on light, high-powered craft
- **Smart reaction wheel behavior**
  - Avoids “distributed torque” bending (e.g., multiple probe cores fighting a dedicated wheel)
- **Pause Tuning** (QoL)
  - When a vessel is not controllable / no EC / on rails / switching, AutoTuner pauses instead of fighting
  - Smooth ramp back in when conditions return

---

## Install

1. Download the release `.zip`.
2. Copy the `gameData` folder into Kerbal Space Program's Main directory.
3. Confirm you have (typical layout):

```
GameData/
  AutoTuner/
    Plugins/
      AutoTuner.dll
    PluginData/
      AutoTuner.cfg
    Icons/
      Icon_On.png
      Icon_Paused.png
      Icon_Off.png
```

4. **Restart KSP** (textures and config are loaded on startup).

### Updating
- Replace the old `AutoTuner.dll` with the new one.
- Keep your `PluginData/AutoTuner.cfg` unless you want to reset settings.

---

## Toolbar icon states

AutoTuner swaps the toolbar icon depending on state:

- **Green** = Enabled + Active (applying tuning) → `Icon_On.png`
- **Yellow** = Enabled + Paused (not applying) → `Icon_Paused.png`
- **Grayscale** = Disabled → `Icon_Off.png`

> Icon filenames must match exactly and live in `GameData/AutoTuner/Icons/`.

---

## Using AutoTuner

1. Click the **AutoTuner toolbar icon** to open the window.
2. Toggle **Enable AutoTuner**.
3. Use **More/Less** to show advanced values.
4. Optional: enable **Fine Mode** for delicate maneuvers.

### Fine Mode notes
Fine Mode is intended for *precision*, not brute-force steering. If you want full authority at all times, disable Fine Mode (or disable adaptive wheel behavior depending on your setup).

---

## Configuration (for “nerds”)

The live config file is saved/loaded from:

- `GameData/AutoTuner/PluginData/AutoTuner.cfg`

AutoTuner will overwrite this file as settings change.

### Config reference file
KSP may strip comments from files it rewrites. If you want descriptions, keep a separate reference file (shipped in the release next to this README) such as:

- `AutoTuner_ConfigReference.cfg`

Edit the **PluginData** cfg for actual behavior changes.

---

## Compatibility notes

AutoTuner plays well with most common mods because it adjusts **authority limits** rather than directly steering the vessel.

### Autopilots (MechJeb, etc.)
- Autopilots may adjust throttle and steering while AutoTuner adjusts authority.
- If you ever feel “fighting,” disable AutoTuner for that craft or reduce authority via config.

### UI/toolbars
AutoTuner uses the **stock AppLauncher**. Toolbar “manager” mods should still work normally, since the button is a standard AppLauncher button.

---

## Troubleshooting

### The toolbar icon looks wrong (blue/purple/tinted)
- Confirm the icon files exist in `GameData/AutoTuner/Icons/`.
- Restart KSP.
- Ensure you did not rename the folder (the load path depends on `AutoTuner/...`).

### UI window appears but looks empty or broken
- This usually indicates a UI/layout exception. Check `KSP.log` for an `[AutoTuner]` UI error line.
- As a quick reset: disable AutoTuner, restart KSP, and test again.

### Settings “don’t stick”
- Ensure you’re editing:
  - `GameData/AutoTuner/PluginData/AutoTuner.cfg`
- KSP can overwrite configs on exit; change settings in-game (or edit the file while KSP is closed).

---

## Feedback / testing
If you report a bug, include:
- KSP version
- A short description of the craft and what you expected
- Your `KSP.log` (or at least relevant lines)
- Your `PluginData/AutoTuner.cfg`

---

## License
Add your preferred license here (MIT / GPL / etc.) before wide release.

## Credits
Created by the AutoTuner project team. (AI-assisted development.)
