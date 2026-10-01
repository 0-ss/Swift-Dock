SwiftDock

A macOS-style dock for Hyprland, written in QML for Quickshell. It's a single file with no external dependencies beyond the compositor tools, and it includes a preferences window styled after macOS System Settings.

Features

Dock

Frosted-glass dock at the bottom of the screen with a gradient and highlight border.
Icon magnification that follows the pointer, with a smooth cosine falloff like the real macOS dock.
Pinned apps are read from your .desktop entries. Running apps that aren't pinned appear after a separator.
Running indicator dots under open apps, and a bounce animation while an app is launching.
Hover tooltips with the app name.
A Trash item that opens trash:///.
Works on every monitor, or on one you choose.

Interaction

Left click focuses the app, cycling through its windows if it has several, or launches it if it isn't running.
Middle click opens a new window.
Right click opens a glass context menu with the app's open windows, Keep in Dock / Remove from Dock, New Window, Quit and Dock Preferences…
Drag pinned icons to reorder them. The other icons slide out of the way as you drag.

Smart auto-hide

Smart: hides while a non-floating window occupies that monitor's active workspace, and slides back when you touch the screen edge. It queries hyprctl and reacts to Hyprland events.
Always: always auto-hides.
Never: always visible, and reserves screen space.

Preferences window
Open it from the right-click menu. It has five panes:

Dock: icon size, magnification amount, spacing and distance from the edge, with a live preview.
Appearance: light/dark mode, accent color, translucency, corner radius and font.
Behavior: hide mode and delay, which display the dock appears on, labels, indicators, launch bounce and Trash.
Applications: manage pinned apps and reset them to the defaults.
About: open the config folder and reset all settings.
Requirements
Hyprland
Quickshell (Qt 6)
hyprctl, which ships with Hyprland
xdg-open, used for the Trash and Open Config Folder
The Inter font (optional, falls back to the system font)
Install
bash
mkdir -p ~/.config/quickshell/macdock
cp shell.qml ~/.config/quickshell/macdock/shell.qml
qs -c macdock
Hyprland setup

The dock window uses the layer namespace macdock. Add a layer rule so the glass gets blurred:

layerrule = blur, macdock
layerrule = ignorealpha 0.2, macdock
layerrule = noanim, macdock

The preferences window has no title bar, so make it float:

windowrule = float, title:^(Dock Preferences)$
windowrule = center, title:^(Dock Preferences)$

These use hyprland.conf syntax and may differ in newer Hyprland versions or the Lua config.

Configuration
Defaults live at the top of shell.qml in the CONFIG section.
Preferences are saved to ~/.config/macdock/settings.json.
Pinned apps are saved to ~/.config/macdock/pinned.json once you use Keep in Dock.
License / Credits

Made by Lachowski — https://github.com/0-ss

Before you publish it, check the layer rule and window rule syntax against your Hyprland version. I haven't run this build myself, so a screenshot or short GIF at the top of the README would also help people see what it looks like.
