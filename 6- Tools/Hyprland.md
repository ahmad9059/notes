#tech #window-manager #linux #hyprland

## What is a Window Manager (WM)?

A **Window Manager** is software that controls the placement and appearance of windows in a graphical user interface (GUI). It works on top of the display server (like X11 or Wayland) and decides:

- How windows open, close, tile, float, or stack
- What keyboard shortcuts manage windows
- How workspaces/desktops are handled
- Visual effects (transparency, animations, etc.)

### Types of Window Managers:

1. **Stacking WMs** (e.g. Openbox): Traditional overlapping windows
2. **Tiling WMs** (e.g. i3, dwm): Automatically tile windows without overlap
3. **Dynamic WMs** (e.g. Awesome, Hyprland): Can do tiling, floating, stacking, dynamically

---

## X11 vs Wayland

- **X11**: Older display server, used in most Linux distros for decades
- **Wayland**: Modern replacement, designed for security, smooth graphics, better performance
- **Hyprland** runs **only on Wayland**, not X11.

---

## What is Hyprland?

**Hyprland** is a dynamic tiling Wayland compositor. It is similar in spirit to i3, Sway, and Awesome WM, but it is built **natively for Wayland**, with modern effects and flexibility.

### Philosophy:

- Minimal but **highly customizable**
- Modern look with **beautiful animations**
- Easy to write extensions and scripts
- Focus on **performance and aesthetics**

---

## Features of Hyprland

|Feature|Description|
|---|---|
|✅ **Wayland-native**|Uses Wayland protocol for smooth performance and modern features|
|🎯 **Dynamic Tiling**|Windows tile by default, but you can float any window|
|🎨 **Animations & Effects**|Smooth animations for moving, resizing, fading|
|🖼️ **Rounded Corners**|Aesthetically pleasing UI with blur, transparency|
|🧩 **Scriptable**|Configurable via config files and `hyprctl` command|
|🖥️ **Multiple Layouts**|Supports tiling, floating, monocle (fullscreen)|
|⌨️ **Keyboard-first**|Designed to be used entirely via keyboard|
|🛠️ **Active Development**|Fast updates, growing community|
|🧠 **Intelligent Workspace Management**|Workspaces per monitor, follow focus, auto move|

---

## How Hyprland Works

1. It reads your config file (`~/.config/hypr/hyprland.conf`)
2. You use keybinds to launch apps, move/split windows, and manage workspaces
3. You can use scripts with `hyprctl` to dynamically control behavior
4. Built-in support for themes, layouts, and monitors

---

## File Structure

```bash
~/.config/hypr/
├── hyprland.conf      # Main config
├── scripts/           # Your custom scripts
├── waybar/            # Bar configuration (if you use Waybar)
└── wallpapers/        # Background images
```

---

## Minimal Example of hyprland.conf

```ini
# Hyprland config

# Set the monitor
monitor=HDMI-A-1,1920x1080@60,0x0,1

# Set wallpaper
exec = swww img ~/wallpapers/mountain.jpg

# Keybindings
bind=SUPER,Return,exec,alacritty
bind=SUPER,Q,killactive
bind=SUPER,F,fullscreen
bind=SUPER,Space,togglefloating

# Workspaces
bind=SUPER,1,workspace,1
bind=SUPER,2,workspace,2
bind=SUPER SHIFT,1,movetoworkspace,1

# Layout
general {
  gaps_in = 5
  gaps_out = 10
  border_size = 2
  col.active_border = rgba(33ccffee) rgba(00ff99ee) 45deg
  col.inactive_border = rgba(595959aa)
  layout = dwindle
}
```

---

## Layouts in Hyprland

1. **Dwindle** - Like a binary tree. Each window splits space.
2. **Master** - One main window, others stack on side
3. **Floating** - Traditional free-move and resize
4. **Monocle** - One window maximized

You can toggle between them using config or hotkeys.

---

## Launching Apps

```ini
bind=SUPER,T,exec,thunar        # File manager
bind=SUPER,B,exec,firefox       # Browser
bind=SUPER,E,exec,code          # VS Code
```

---

## Tools You May Use with Hyprland

- **Waybar**: Custom bar for Wayland
- **swww**: For setting wallpapers
- **Hyprpaper**: Built-in wallpaper daemon for Hyprland
- **wofi**: Application launcher (like rofi but for Wayland)
- **mako**: Notification daemon
- **swaylock & swayidle**: For lock screen and idle

---

## Useful Hyprctl Commands

```bash
hyprctl monitors               # Show monitor info
hyprctl clients                # Show open windows
hyprctl dispatch exit          # Exit Hyprland
hyprctl keyword ...            # Dynamically update config
```

---

## Sample Startup Script (~/.config/hypr/start.sh)

```bash
#!/bin/bash
swww init &
waybar &
mako &
nm-applet &
```

Then add to your config:

```ini
exec-once = ~/.config/hypr/start.sh
```

---

## Tips for First Time Setup

1. Install via AUR or GitHub
2. Add Hyprland to your `.xinitrc` or greetd/wlroots session
3. Use `alacritty`, `kitty`, or any Wayland terminal
4. Keep `ttf-font-awesome`, `nerd-fonts`, etc. for icon support
5. Use a compositor-aware bar like **waybar**

---

## Resources

- GitHub: [https://github.com/hyprwm/Hyprland](https://github.com/hyprwm/Hyprland)
- Wiki: [https://wiki.hyprland.org](https://wiki.hyprland.org)
- Reddit: [r/unixporn](https://reddit.com/r/unixporn) for inspiration
- YouTube: Search “Hyprland rice” or “Hyprland setup” for walkthroughs
