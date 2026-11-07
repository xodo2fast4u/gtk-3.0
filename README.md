<h1 align="center">GTK 3.0 Custom Theme & Configuration</h1>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-2E8B57?style=for-the-badge" alt="License: MIT" /></a>
  <a href="https://www.gtk.org/"><img src="https://img.shields.io/badge/toolkit-GTK%203.0-4A90E2?logo=gnome&style=for-the-badge" alt="GTK 3.0" /></a>
  <a href="https://github.com/EliverLara/Nordic"><img src="https://img.shields.io/badge/base%20theme-Nordic-2E3440?style=for-the-badge" alt="Base Theme: Nordic" /></a>
  <a href="https://github.com/PapirusDevelopmentTeam/papirus-icon-theme"><img src="https://img.shields.io/badge/icons-Papirus--Dark-5294E2?style=for-the-badge" alt="Icon Theme: Papirus Dark" /></a>
  <a href="https://github.com/xodo2fast4u"><img src="https://img.shields.io/badge/status-active-2ECC71?style=for-the-badge" alt="Status: active" /></a>
</p>

<p align="center">A custom dark-mode styling layer, user settings configuration and quick bookmarks profile for GTK 3 desktop applications on Linux, featuring subtle gradients, modern typography, rounded geometry and zero-border aesthetics.</p>

## Disclaimer

**IMPORTANT:** These configuration files directly override user-level GTK 3 styles and application settings.

- **Desktop compatibility:** Designed for Linux desktop environments (GNOME, XFCE, Cinnamon, MATE, i3/sway, etc.) running GTK 3 applications.
- **Backup existing files:** Always create backups of your existing `~/.config/gtk-3.0/` configuration before applying changes.
- **Application variations:** Some custom or sandboxed applications (e.g. Flatpak/Snap) may require granting permission to access user configuration or theme directories.

## Why This Configuration?

Default GTK 3 themes can feel flat or inconsistent across varied desktop setups. This configuration delivers a polished, cohesive aesthetic:

- **Sleek dark gradient palette:** Subtle, modern charcoal-to-black depth (`#141414` to `#0d0d0d`) without harsh flat contrasts.
- **Custom typography & font rendering:** Configured with `JetBrainsMono NF` and `Roboto` with slight antialiasing and subpixel RGB hinting.
- **Rounded modern geometry:** Clean 10px rounded window borders, 8px buttons, 7px sidebar rows and borderless headerbars.
- **Responsive interaction feedback:** Smooth cubic-bezier micro-transitions (0.18s) across buttons, menu items and sidebar lists.
- **Light theme fallback:** Includes a high-contrast `gtk.light.css` definition for daytime usage or light-mode toggle workflows.

## Features

### UI & Styling Components

- **Headerbars & Titlebars:** Borderless dark gradient headerbars with rounded top corners, integrated search entry bars and custom title styling.
- **Sidebar & Places Navigation:** Dedicated styles for `.sidebar`, `placessidebar` and `.sidebar-pane` with refined item padding and hover states.
- **Menus & Popovers:** Floating dark popovers with rounded 9px containers, subtle item hover fills and customized tooltips.
- **Buttons & Pathbars:** Tactile gradient buttons with distinct `:hover` and `:active` / `:checked` states.
- **Progress & Sliders:** Clean rounded progress troughs and compact scrollbar sliders with accent hover states.

### Settings & System Integration

- **Theme & Icon binding:** Automatically configures `Nordic` as the base theme and `Papirus-Dark` for icons.
- **Font rendering configuration:** Subpixel RGB antialiasing with `hintslight` hinting for crisp text on high-DPI and standard monitors.
- **File manager bookmarks:** Pre-configured GTK file-chooser sidebar bookmarks pointing directly to standard user directories.

## Prerequisites

- A Linux distribution running GTK 3 (`libgtk-3-0` or equivalent)
- **Base Theme (Optional but recommended):** [Nordic](https://github.com/EliverLara/Nordic)
- **Icon Theme:** [Papirus-Dark](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)
- **Fonts:** [JetBrains Mono Nerd Font](https://www.jetbrains.com/lp/mono/) and [Roboto](https://fonts.google.com/specimen/Roboto) or [Adwaita Sans](https://gitlab.gnome.org/GNOME/adwaita-fonts)

Verify your GTK version before applying:

```bash
gtk-launch --version 2>/dev/null || dpkg -l libgtk-3-0 | grep -i gtk
```

## Quick Start

### 1. Clone or Copy Files

Place the repository files into your user config directory:

```bash
mkdir -p ~/.config/gtk-3.0
cp gtk.css settings.ini bookmarks ~/.config/gtk-3.0/
```

### 2. Verify settings.ini

Ensure your `~/.config/gtk-3.0/settings.ini` specifies your desired font and themes:

```ini
[Settings]
gtk-theme-name=Nordic
gtk-icon-theme-name=Papirus-Dark
gtk-font-name=Adwaita Sans 11
gtk-cursor-theme-name=default
gtk-cursor-theme-size=24
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size=GTK_ICON_SIZE_LARGE_TOOLBAR
gtk-button-images=0
gtk-menu-images=0
gtk-enable-event-sounds=1
gtk-enable-input-feedback-sounds=0
gtk-xft-antialias=1
gtk-xft-hinting=1
gtk-xft-hintstyle=hintslight
gtk-xft-rgba=rgb
gtk-application-prefer-dark-theme=1
```

### 3. Apply Changes

Reload or restart your running GTK applications or restart your desktop session:

```bash
# To test in an isolated GTK 3 app
GTK_DEBUG=interactive gtk3-demo
```

## Configuration & Theming

### Switching between Dark and Light Mode

The repository provides both dark (`gtk.dark.css`) and high-contrast light (`gtk.light.css`) definitions:

- **Switch to Dark Mode (Default):**
  ```bash
  cp ~/.config/gtk-3.0/gtk.dark.css ~/.config/gtk-3.0/gtk.css
  ```
- **Switch to Light Mode:**
  ```bash
  cp ~/.config/gtk-3.0/gtk.light.css ~/.config/gtk-3.0/gtk.css
  ```

### File Manager Bookmarks

`bookmarks` configures the left sidebar shortcuts in the GTK file chooser dialog and file managers (such as Thunar, Nautilus or Nemo):

| URI                             | Display Shortcut |
| ------------------------------- | ---------------- |
| `file:///home/<user>/Pictures`  | Pictures         |
| `file:///home/<user>/Documents` | Documents        |
| `file:///home/<user>/Music`     | Music            |
| `file:///home/<user>/Downloads` | Downloads        |
| `file:///home/<user>/Programs`  | Programs         |
| `file:///home/<user>/Videos`    | Videos           |

> **Note:** Update the username path in `bookmarks` to match your active user account.

## Project Structure

| File                           | Purpose                                                                |
| ------------------------------ | ---------------------------------------------------------------------- |
| [gtk.css](gtk.css)             | Active GTK 3 custom stylesheet overriding widgets, headers and buttons |
| [gtk.dark.css](gtk.dark.css)   | Dark theme stylesheet template with gradient styling                   |
| [gtk.light.css](gtk.light.css) | Clean, high-contrast light mode alternative stylesheet                 |
| [settings.ini](settings.ini)   | GTK 3 system properties, font choices, cursor size and theme selection |
| [bookmarks](bookmarks)         | File chooser sidebar quick-access directory bookmarks                  |

## Troubleshooting

### Changes do not reflect in running applications

GTK 3 caches styles per process. Close and reopen the target application or log out and log back into your desktop environment.

### Fonts appear distorted or jagged

Check that `gtk-xft-antialias=1` and `gtk-xft-rgba=rgb` are set in [settings.ini](settings.ini). Verify that `JetBrainsMono NF` and `Roboto` are installed in `~/.local/share/fonts` or `/usr/share/fonts`.

### Flatpak apps do not pick up the theme

Flatpak applications run in sandboxed environments. Expose user configurations to Flatpak:

```bash
flatpak override --user --filesystem=xdg-config/gtk-3.0:ro
```

## Contributing

Contributions, palette variations and widget fixes are welcome. Feel free to open issues or submit pull requests with screenshots demonstrating UI improvements across GTK 3 components.

## License

This configuration is available under the [MIT License](LICENSE).
