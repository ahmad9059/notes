# KeyBindings

## User KeyBindings

| Keybinding                   | Action / Command                                         | Description                               |
| ---------------------------- | -------------------------------------------------------- | ----------------------------------------- |
| **SUPER + D**                | `pkill rofi                                              | Open Rofi                                 |
| **SUPER + Return**           | `foot`                                                   | Open default terminal (foot)              |
| **SUPER + F**                | `thunar`                                                 | Open file manager (Thunar)                |
| **SUPER + K**                | `kitty`                                                  | Launch Kitty terminal                     |
| **SUPER + B**                | `firefox`                                                | Launch Firefox browser                    |
| **SUPER + R**                | `foliate`                                                | Launch Foliate eBook reader               |
| **SUPER + V**                | `$scriptsDir/ClipManager.sh`                             | Clipboard manager                         |
| **SUPER + C**                | `code --ozone-platform=x11`                              | Launch Visual Studio Code                 |
| **SUPER + O**                | `obsidian --ozone-platform=x11`                          | Launch Obsidian                           |
| **SUPER + S**                | `spotify-launcher`                                       | Launch Spotify                            |
| **SUPER + I**                | `vesktop`                                                | Launch Vesktop (Discord)                  |
| **SUPER + T**                | `(64gram-desktop\|telegram-desktop)`                     | Launch Telegram client                    |
| **SUPER + M**                | `fdm`                                                    | Launch Free Download Manager              |
| **SUPER + Shift + H**        | `$scriptsDir/KeyHints.sh`                                | Show help / cheat sheet                   |
| **SUPER + Shift + R**        | `$scriptsDir/Refresh.sh`                                 | Refresh Waybar, swaync, rofi              |
| **SUPER + Shift + E**        | `$scriptsDir/RofiEmoji.sh`                               | Open emoji picker                         |
| **SUPER + Shift + O**        | `$scriptsDir/ChangeBlur.sh`                              | Toggle blur settings                      |
| **SUPER + Shift + G**        | `$scriptsDir/GameMode.sh`                                | Toggle animations ON/OFF                  |
| **SUPER + Shift + L**        | `$scriptsDir/ChangeLayout.sh`                            | Toggle between Master and Dwindle layouts |
| **SUPER + Shift + P**        | `hyprpicker -a / –autocopy`                              | Color picker                              |
| **SUPER + Shift + V**        | `systemd-run --user --scope $scriptsDir/parrotOS-KVM.sh` | Start yazi in foot                        |
| **SUPER + Shift + B**        | `/home/ahmad/Documents/blog/quickScript.sh`              | Hugo file sync                            |
| **SUPER + Shift + F**        | `fullscreen`                                             | Toggle fullscreen                         |
| **SUPER + Shift + Return**   | `[float; move 15% 20% size 70% 60%] foot`                | Dropdown floating terminal                |
| **SUPER + Ctrl + F**         | `fullscreen, 1`                                          | Fake fullscreen                           |
| **SUPER + Space**            | `togglefloating`                                         | Toggle floating mode for window           |
| **SUPER + Alt + Space**      | `hyprctl dispatch workspaceopt allfloat`                 | Set all windows to floating               |
| **SUPER + Alt + Mouse Down** | Adjust `cursor:zoom_factor` ×2                           | Zoom in (magnifier)                       |
| **SUPER + Alt + Mouse Up**   | Adjust `cursor:zoom_factor` ÷2                           | Zoom out (magnifier)                      |
| **SUPER + Ctrl + Alt + B**   | `pkill -SIGUSR1 waybar`                                  | Toggle show/hide Waybar                   |
| **SUPER + Ctrl + B**         | `$scriptsDir/WaybarStyles.sh`                            | Waybar styles menu                        |
| **SUPER + Alt + B**          | `$scriptsDir/WaybarLayout.sh`                            | Waybar layout menu                        |
| **SUPER + Shift + M**        | `$UserScripts/RofiBeats.sh`                              | Play online music using Rofi              |
| **SUPER + Shift + W**        | `$UserScripts/WallpaperSelect.sh`                        | Wallpaper selection menu                  |
| **Ctrl + Alt + W**           | `$UserScripts/WallpaperRandom.sh`                        | Set random wallpaper                      |
| **SUPER + Ctrl + O**         | `hyprctl setprop active opaque toggle`                   | Toggle window opacity                     |
| **SUPER + Shift + K**        | `$scriptsDir/KeyBinds.sh`                                | Search keybinds via Rofi                  |
| **SUPER + Shift + A**        | `$scriptsDir/Animations.sh`                              | Hyprland animations menu                  |
| **SUPER + Alt + C**          | `$UserScripts/RofiCalc.sh`                               | Open calculator via Rofi                  |


## System KeyBindings


| Keybinding                     | Action                                 | Description                                     |
| ------------------------------ | -------------------------------------- | ----------------------------------------------- |
| `CTRL ALT + Delete`            | `exec hyprctl dispatch exit 0`         | Exit Hyprland                                   |
| `SUPER + Q`                    | `killactive`                           | Close active window (not kill)                  |
| `SUPER + SHIFT + Q`            | `exec KillActiveProcess.sh`            | Kill active process                             |
| `CTRL ALT + L`                 | `exec LockScreen.sh`                   | Screen lock                                     |
| `CTRL ALT + P`                 | `exec Wlogout.sh`                      | Power menu                                      |
| `SUPER + N`                    | `exec swaync-client -t -sw`            | Open swayNC notification panel                  |
| `SUPER + SHIFT + E`            | `exec Kool_Quick_Settings.sh`          | Open KooL Hyprland Settings menu                |
| `SUPER + CTRL + D`             | `layoutmsg removemaster`               | Remove master                                   |
| `SUPER + I`                    | `layoutmsg addmaster`                  | Add master                                      |
| `SUPER + J`                    | `layoutmsg cyclenext`                  | Cycle to next window                            |
| `SUPER + K`                    | `layoutmsg cycleprev`                  | Cycle to previous window                        |
| `SUPER + CTRL + Return`        | `layoutmsg swapwithmaster`             | Swap with master                                |
| `SUPER + SHIFT + I`            | `togglesplit`                          | Toggle split (only on dwindle layout)           |
| `SUPER + P`                    | `pseudo`                               | Toggle pseudo mode                              |
| `SUPER + M`                    | `exec hyprctl dispatch splitratio 0.3` | Set split ratio to 0.3                          |
| `SUPER + G`                    | `togglegroup`                          | Toggle group                                    |
| `SUPER + CTRL + Tab`           | `changegroupactive`                    | Change focus within group                       |
| `SUPER + J`                    | `cyclenext`                            | Cycle to next window                            |
| `SUPER + J`                    | `bringactivetotop`                     | Bring active window to top                      |
| `SUPER + Print`                | `exec ScreenShot.sh --now`             | Screenshot now                                  |
| `SUPER + SHIFT + Print`        | `exec ScreenShot.sh --area`            | Screenshot selected area                        |
| `SUPER + CTRL + Print`         | `exec ScreenShot.sh --in5`             | Screenshot after 5 seconds                      |
| `SUPER + CTRL + SHIFT + Print` | `exec ScreenShot.sh --in10`            | Screenshot after 10 seconds                     |
| `ALT + Print`                  | `exec ScreenShot.sh --active`          | Screenshot active window                        |
| `SUPER + SHIFT + S`            | `exec ScreenShot.sh --swappy`          | Screenshot with swappy                          |
| `SUPER + SHIFT + Left`         | `resizeactive -50 0`                   | Resize window left                              |
| `SUPER + SHIFT + Right`        | `resizeactive 50 0`                    | Resize window right                             |
| `SUPER + SHIFT + Up`           | `resizeactive 0 -50`                   | Resize window up                                |
| `SUPER + SHIFT + Down`         | `resizeactive 0 50`                    | Resize window down                              |
| `SUPER + CTRL + Left`          | `movewindow l`                         | Move window left                                |
| `SUPER + CTRL + Right`         | `movewindow r`                         | Move window right                               |
| `SUPER + CTRL + Up`            | `movewindow u`                         | Move window up                                  |
| `SUPER + CTRL + Down`          | `movewindow d`                         | Move window down                                |
| `SUPER + ALT + Left`           | `swapwindow l`                         | Swap window left                                |
| `SUPER + ALT + Right`          | `swapwindow r`                         | Swap window right                               |
| `SUPER + ALT + Up`             | `swapwindow u`                         | Swap window up                                  |
| `SUPER + ALT + Down`           | `swapwindow d`                         | Swap window down                                |
| `SUPER + Left`                 | `movefocus l`                          | Move focus left                                 |
| `SUPER + Right`                | `movefocus r`                          | Move focus right                                |
| `SUPER + Up`                   | `movefocus u`                          | Move focus up                                   |
| `SUPER + Down`                 | `movefocus d`                          | Move focus down                                 |
| `SUPER + Tab`                  | `workspace m+1`                        | Switch to next workspace                        |
| `SUPER + SHIFT + Tab`          | `workspace m-1`                        | Switch to previous workspace                    |
| `SUPER + U`                    | `togglespecialworkspace nyx`           | Toggle special workspace 'nyx'                  |
| `SUPER + SHIFT + U`            | `movetoworkspace special:nyx`          | Move window to special workspace 'nyx'          |
| `SUPER + 1-10`                 | `workspace 1-10`                       | Switch to workspace 1-10                        |
| `SUPER + SHIFT + 1-10`         | `movetoworkspace 1-10`                 | Move window to workspace 1-10                   |
| `SUPER + SHIFT + [ / ]`        | `movetoworkspace -1 / +1`              | Move window to previous/next workspace          |
| `SUPER + CTRL + 1-10`          | `movetoworkspacesilent 1-10`           | Move window to workspace silently 1-10          |
| `SUPER + CTRL + [ / ]`         | `movetoworkspacesilent -1 / +1`        | Move window to previous/next workspace silently |
| `SUPER + Mouse Scroll Down`    | `workspace e+1`                        | Scroll to next workspace                        |
| `SUPER + Mouse Scroll Up`      | `workspace e-1`                        | Scroll to previous workspace                    |
| `SUPER + .`                    | `workspace e+1`                        | Next workspace                                  |
| `SUPER + ,`                    | `workspace e-1`                        | Previous workspace                              |
| `SUPER + Left Mouse`           | `movewindow`                           | Move window with mouse                          |
| `SUPER + Right Mouse`          | `resizewindow`                         | Resize window with mouse                        |


## Neovim KeyBindings (NvChad + These Custom One's)


| Mode(s)                | Key(s)                  | Action / Command                                                     | Description               |
| ---------------------- | ----------------------- | -------------------------------------------------------------------- | ------------------------- |
| Normal                 | `;`                     | `:`                                                                  | Enter command mode        |
| Insert                 | `jk`                    | `<ESC>`                                                              | Exit insert mode          |
| Normal, Insert, Visual | `Ctrl + S`              | `<cmd> w <cr>`                                                       | Save file                 |
| Insert                 | `Alt + h`               | `<Left>`                                                             | Move left in insert mode  |
| Insert                 | `Alt + j`               | `<Down>`                                                             | Move down in insert mode  |
| Insert                 | `Alt + k`               | `<Up>`                                                               | Move up in insert mode    |
| Insert                 | `Alt + l`               | `<Right>`                                                            | Move right in insert mode |
| Normal                 | `Ctrl + A`              | `ggVG`                                                               | Select all                |
| Insert                 | `Ctrl + A`              | `<ESC>ggVG`                                                          | Select all in insert mode |
| Visual                 | `Ctrl + A`              | `<ESC>ggVG`                                                          | Select all in visual mode |
| Normal                 | `<leader>lg`            | `<cmd>LazyGit<CR>`                                                   | Open LazyGit              |
| Visual                 | `<leader>i{`            | `vi{`                                                                | Select inside `{}`        |
| Visual                 | `<leader>a{`            | `va{`                                                                | Select around `{}`        |
| Visual                 | `<leader>i(`            | `vi(`                                                                | Select inside `()`        |
| Visual                 | `<leader>a(`            | `va(`                                                                | Select around `()`        |
| Visual                 | `<leader>i[`            | `vi[`                                                                | Select inside `[]`        |
| Visual                 | `<leader>a[`            | `va[`                                                                | Select around `[]`        |
| Visual                 | `<leader>i"`            | `vi"`                                                                | Select inside `""`        |
| Visual                 | `<leader>a"`            | `va"`                                                                | Select around `""`        |
| Visual                 | `<leader>i'`            | `vi'`                                                                | Select inside `''`        |
| Visual                 | `<leader>a'`            | `va'`                                                                | Select around `''`        |
| Visual                 | `i``                    | `vi``                                                                | Select inside ` `` `      |
| Visual                 | `a``                    | `va``                                                                | Select around ` `` `      |
| Normal                 | `<leader>1`…`<leader>9` | Switch to buffer `1-9`                                               | Buffer navigation         |
| Normal, Terminal       | `Alt + i`               | `require("nvchad.term").toggle { pos="float", id="floatTerm", ... }` | Toggle floating terminal  |
| Normal                 | `Ctrl + h`              | `<cmd>TmuxNavigateLeft<CR>`                                          | Tmux navigate left        |
| Normal                 | `Ctrl + j`              | `<cmd>TmuxNavigateDown<CR>`                                          | Tmux navigate down        |
| Normal                 | `Ctrl + k`              | `<cmd>TmuxNavigateUp<CR>`                                            | Tmux navigate up          |
| Normal                 | `Ctrl + l`              | `<cmd>TmuxNavigateRight<CR>`                                         | Tmux navigate right       |
| Normal                 | `Ctrl + \`              | `<cmd>TmuxNavigatePrevious<CR>`                                      | Tmux navigate previous    |


## TMUX

|Keys / Combo|Mode / Context|Action|
|---|---|---|
|**r**|Prefix required|Reload `~/.tmux.conf`|
|**M-o**|Global|Tmux prefix key|
|**Mouse**|Global|Mouse support enabled|
|*****|Prefix required|Split window horizontally|
|**l**|Prefix required|Select left pane|
|**j**|Prefix required|Select pane below|
|**k**|Prefix required|Select pane above|
|**h**|Prefix required|Select right pane|
|**C-h**|Global (normal)|If in Vim → send `C-h`, else select left pane|
|**C-j**|Global (normal)|If in Vim → send `C-j`, else select pane below|
|**C-k**|Global (normal)|If in Vim → send `C-k`, else select pane above|
|**C-l**|Global (normal)|If in Vim → send `C-l`, else select right pane|
|**C-\**|Global (normal)|If in Vim → send `C-\\`, else select last active pane|
|**C-h**|Copy-mode (vi)|Select left pane|
|**C-j**|Copy-mode (vi)|Select pane below|
|**C-k**|Copy-mode (vi)|Select pane above|
|**C-l**|Copy-mode (vi)|Select right pane|
|**C-\**|Copy-mode (vi)|Select last active pane|
|**M-1** to **M-9**, **M-0**|Global|Select window 1–10|
