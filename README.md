# Power Chip

A fork of Omarchy's built-in **Power** panel for the Omarchy shell. The bar
button drops the battery glyph and shows the charge level as a bold number
inside a rounded outline whose color follows the level.

![Bar preview](preview.png)

## Features

- Bar shows the bare charge number (no `%`, no battery glyph) in a rounded,
  border-only frame.
- Frame color follows the level: **red below 20%**, **yellow 20–49%**,
  **green 50% and up**, and the theme accent while charging.
- Colors come from the active theme's `colors.toml` and refresh when the
  theme changes.
- Click opens the full Power panel (power profiles, battery readings, system
  stats); right-click toggles between the chip and the stock battery icon.
- Vertical bars keep the battery icon, since the chip needs horizontal room.

## Requirements

- Omarchy with the Quickshell-based shell (`omarchy-shell`)
- UPower

Built and tested against Omarchy 4.5.0.

## Install

### From git (recommended)

```bash
omarchy plugin add https://github.com/purePulsar/omarchy-power-chip.git --enable
```

Choose `right` for the bar section when prompted. If you enable it later
manually:

```bash
omarchy plugin enable purepulsar.power right
```

The plugin keeps `clonedFrom: omarchy.power` in its manifest, so Omarchy
disables the built-in Power widget when this one is enabled and routes the
`omarchy.power` IPC target here.

### Offline / manual

1. Copy this whole folder to `~/.config/omarchy/plugins/purepulsar.power`.
2. Reload the plugin list:

   ```bash
   omarchy-shell shell rescanPlugins
   ```

3. Enable it in the bar:

   ```bash
   omarchy plugin enable purepulsar.power right
   ```

If the bar still shows the old widget, restart the shell with
`omarchy restart shell`.

## Customizing

Mirror `purepulsar.power/Panel.qml` into `~/.config/omarchy/plugins/` after
enabling, or edit the installed copy directly. The level thresholds live in
`percentageFrameColor`, and the frame's size and border weight in the
`Rectangle` under `labelButton`. Frame colors use the theme keys `red`,
`yellow`, `green`, and `accent`.

## Uninstall

```bash
omarchy plugin remove purepulsar.power
omarchy plugin enable omarchy.power right
```

The second command restores the stock Power widget.

## License

MIT. This plugin is derived from Omarchy's Power plugin
(https://github.com/omacom/omarchy), which is MIT licensed. See `LICENSE`.
