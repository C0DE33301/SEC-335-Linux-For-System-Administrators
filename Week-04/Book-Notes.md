- [4.1 Understanding the GUI](#41-understanding-the-gui)
- [4.2 Understanding the X11 Architecture](#42-understanding-the-x11-architecture)
- [4.3 Managing the GUI](#43-managing-the-gui)
- [4.4 Providing Accessibility](#44-providing-accessibility)
- [4.5 Using X11 for remote access](#45-using-x11-for-remote-access)
- [4.6 Using remote desktop software](#46-using-remote-desktop-software)

# 4.1 Understanding the GUI
|Serving the GUI Components|||
|---|---|---|
|**Desktop Environment**|**Windows Manager**|**Display Server**|
|...|A program that communicates with the **display server** on behalf of the GUI.<br><ul><li>Mutter</li><li>Kwin</li><li>Marco</li><li>Metacity</li><li>Muffin</li></ul>|A program that communicates with the **display server protocol** to transmit the desires of the GUI to the operating system. <br><br> A **compositor** program arranges various display elements within a window to create a screen image to be passed back to the client.|

# 4.2 Understanding the X11 Architecture
**X.Org Server**
- A Display Server
- Keeps track of display card, monitor, and input device information in a configuration file, using the original XFree86 format.
- The primary configuration file is `/etc/x11/xorg.conf`
- Individual applications or devices store their own X11 settings in separate files stored in the `/etc/x11/xorg.conf.d` directory.
- To manually create the configuration file
    1. Shutdown the X Server, `sudo telinit 3`, Works on both **SysVinit** **systemd** systems
    1. Generate the file, `sudo xorg -configure`, **File:**`xorg.conf.new` will be in your local directory.
    1. Edit the file
    1. Rename the file
    1. Move the file to its location
    1. restart the X server.
- `xorg.conf`
    |||
    |---|---|
    |**Input Device**|Configure the session's keyboard and mouse.|
    |**Monitor**|Sets the session's monitor configuration|
    |**Modes**|Defines video modes|
    |**Device**|Configures the session's video card(s)|
    |**Screen**|Sets the session's screen resolution and color depth|
    |**Module**|Denotes any modules that need to be loaded|
    |**Files**|Sets file path names, if needed, for fon't, modules, and keyboard layout files.|
    |**Server Flags**|Configures global X server options|
    |**Server Layout**|Links together all the session's input and output devices.|
- X11 configuration file's details, `man 5 xorg.conf`
- To troubleshoot X11 problems, the X.Org server generates the `~/.xsession-errors` text log file, that indicates what whent wrong with the X.Org server.
- `xdpyinfo`, Provides information about the X.Org server, including the different screen types available, the default communicate parameter values, protocol extension information.
- `xwininfo`, Provides window information, The displayed stats include location information, the window's dimensions (width and height), color map ID.
    - Will hang if you are running a Wayland session instead of an X.Org session. Press `Ctrl+C` to exit out of the hung command.
    - Reset it by pressing the `Ctrl+Alt+Backspace`

**Wayland**
- A Display Server
- Supports newer display hardware and security, and supports additional types of input devices.
- **Checking your display server**
    1. `echo $WAYLAND_DISPLAY`
    1. Note the session number, `loginctl`
    1. loginctl show-session SESSION-NUMBER -p Type
- The wayland compositor is **Weston**
- Wayland's compositor is swappable.
    - Arcan
    - Sway
    - Lipstick
    - Clayland
- **GUI issues**
    - The GUI without Wayland
    - Check your system's graphics card
    - Use a different compositor

# 4.3 Managing the GUI
- The X Display Manager configuration file, `/etc/X11/xdm/xdm-config`

# 4.4 Providing Accessibility

# 4.5 Using X11 for remote access

# 4.6 Using remote desktop software