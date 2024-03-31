# GNOME Widgets with Dash to Panel and Argos

This guide covers the setup of Dash to Panel and Argos extensions for GNOME Shell, enabling users to integrate system controls and scripts directly into the taskbar. Specifically, it will detail how to create and use Argos scripts for toggling audio outputs and VPN connections.

## Prerequisites

- A Linux distribution with GNOME Shell. (tested with Ubuntu 22.04)
- Dash to Panel and Argos extensions installed.


## Installing Necessary Components (assuming Ubuntu 22.04 with Firefox)

### Step 1: Install GNOME Shell Extensions

```bash
sudo apt update
sudo apt install gnome-shell-extensions
```

## Installing Necessary Components on Ubuntu 22.04

To set up Dash to Panel and Argos on Ubuntu 22.04 with GNOME Shell, and manage these using Firefox, follow the steps below:

### Step 1: Install GNOME Shell Extensions

Install the GNOME Shell extensions package:

```
sudo apt update
sudo apt install gnome-shell-extensions
```

### Step 2: Install GNOME Shell Integration for Firefox

Add the GNOME Shell integration extension to Firefox to manage GNOME extensions via the web interface. You can find it in the Firefox Add-ons store or visit [GNOME Shell integration](https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration/) directly.

### Step 3: Enable Extensions from the GNOME Extensions Website

With the GNOME Shell integration extension for Firefox installed, you can now easily manage your GNOME extensions through the web interface.

- Visit the [GNOME Extensions](https://extensions.gnome.org/) website.
- Search for "Dash to Panel" extension
- Use the toggle switch to install and enable these extensions.

## Step 3b: Install Argos

Argos is a GNOME Shell extension that allows for the execution of scripts and displaying their output in the top panel, enhancing desktop functionality and customization.

1. **Clone the Repository**: First, clone the Argos repository to your local machine. Choose a directory for development projects, such as `~/Projects`.

```bash
    cd ~/Projects
    git clone https://github.com/p-e-w/argos.git argos/argos@pew.worldwidemann.com
```

2. **Install the Extension**: Copy or symlink the cloned Argos directory to the GNOME Shell extensions directory.

```bash
    ln -s ~/Projects/argos/argos@pew.worldwidemann.com ~/.local/share/gnome-shell/extensions/argos@pew.worldwidemann.com
```

3. **Enable the Extension**: Restart GNOME Shell to apply changes by pressing `Alt+F2`, typing `r`, and pressing `Enter`. Then, enable Argos using GNOME Extensions app or the GNOME Tweaks tool.

## Updating Argos

To ensure Argos remains up-to-date with the latest features and bug fixes, follow these steps:

1. **Navigate to the Argos Directory**: Change to the directory where Argos was cloned.

```bash
    cd ~/Projects/argos/argos@pew.worldwidemann.com
```

2. **Pull the Latest Changes**: Update the local repository with the latest changes from GitHub.

```bash
    git pull origin master
```

3. **Apply the Update**: Restart GNOME Shell to ensure the updates are applied, either by logging out and back in or by pressing `Alt+F2`, typing `r`, and pressing `Enter`.

## Removing Argos

If you wish to remove Argos from your system, follow these steps:

1. **Remove the Extension Directory**: Delete the Argos directory from the GNOME Shell extensions directory.

```bash
    rm -rf ~/.local/share/gnome-shell/extensions/argos@pew.worldwidemann.com
```

2. **Restart GNOME Shell**: Restart GNOME Shell for the changes to take effect by pressing `Alt+F2`, typing `r`, and pressing `Enter`.

3. **Optional Cleanup**: If desired, you can also remove the Argos repository from your projects directory.

```bash
    rm -rf ~/Projects/argos/argos@pew.worldwidemann.com
```

By following these instructions, you can install, update, or remove Argos, tailoring your GNOME Shell environment to your preferences.


### Step 4: Restart GNOME Shell

To ensure the changes take effect, you may need to restart GNOME Shell. Press `Alt+F2`, type `r`, then press `Enter`. If you're on Wayland, you may need to log out and log back in.

### Step 5: Customize Dash to Panel and Argos

After installation, access the settings of each extension through the Extensions application or by right-clicking on the panel (for Dash to Panel) or the Argos widget itself to begin customization.

### Note:

Ensure that the version of extensions is compatible with your GNOME Shell version. Ubuntu 22.04 typically comes with GNOME Shell 40 or newer.

# Creating a VPN Switching App with Argos

Argos for GNOME Shell allows you to execute scripts and display their output in the top panel, turning them into interactive applets. This guide details creating a VPN switching applet using a bash script.

## Understanding the Script Name: `wgvpn.1r.30s.sh`

- The naming convention `wgvpn.1r.30s.sh` for Argos scripts includes specific directives:
  - **wgvpn**: A custom prefix for identification.
  - **1r**: The script runs when the GNOME Shell starts (`r` for refresh) and then periodically based on the interval specified next.
  - **30s**: The script refreshes every 30 seconds (`30s`), keeping the display updated. The interval can be adjusted as needed.

## Script Location

Store the script in `~/.config/argos` to ensure Argos loads it. Make sure the script is executable:

```bash
chmod +x ~/.config/argos/wgvpn.1r.30s.sh
```

## Argos VPN script

```bash
#!/bin/bash

CONFIG0="/etc/wireguard/vpn0.conf"
INTERFACE0="vpn0"
SUDO="/usr/bin/sudo"
WG_QUICK="/usr/bin/wg-quick"

# icons from Google Fonts Material Symbols (https://fonts.google.com/icons) and placed and indexed in ~/.local/share/icons
# adding fill="#ffffff" for white. "material-design-hub" for VPN ON, "material-design-spoke" for VPN OFF
# "material-design-public" and "material-design-public-off" also good options
if ip link show $INTERFACE0 &> /dev/null; then
    echo "VPN: ON | iconName=material-design-hub"
    echo "---"
    echo "Disconnect | iconName=material-design-spoke-black bash='$SUDO $WG_QUICK down $CONFIG0' terminal=false refresh=true"
else
    echo "VPN: OFF | iconName=material-design-spoke"
    echo "---"
    echo "Connect to vpn0 | iconName=material-design-hub-black bash='$SUDO $WG_QUICK up $CONFIG0' terminal=false refresh=true"
fi

# Add more VPN connections below with new CONFIG1="/path/to/your/second/vpn.conf" and adding a new INTERFACE1="vpn1"
```

# Preparing Icons for the VPN Switching App

For the VPN switching app to provide clear visual feedback, it utilizes iconography to indicate the current state (VPN ON or OFF). You can source icons from GNOME's built-in icons or Google's Material Design icons. Here's how to acquire and prepare these icons:

## Acquiring Icons

- **GNOME Built-in Icons**: GNOME Shell comes with a set of standard icons that can be utilized directly without additional downloads. These icons are typically found in `/usr/share/icons` or `~/.local/share/icons`.

- **Google's Material Design Icons**: For a wider selection of icons, Google's Material Design icons offer an extensive library. You can download icons from [Google Fonts Material Icons](https://fonts.google.com/icons).

## Storing Icons

Once you've selected your icons, follow these steps to store them properly:

1. **Create a Local Share Icons Directory**: If it doesn't already exist, create a directory in your local share to store custom icons. This ensures that your script can easily find and use these icons.

    ```bash
    mkdir -p ~/.local/share/icons
    ```

2. **Placing Icons**: Move your downloaded or selected icons into the `~/.local/share/icons` directory. Ensure the icons are named clearly to reference them easily in your scripts.

3. **Referencing Icons in Your Script**: When specifying icons in your Argos script, use the path relative to `~/.local/share/icons`. For example, if you have an icon named `vpn-on.svg`, reference it as `iconName=vpn-on` within your script.

    Note: Ensure the icons are in a supported format (e.g., `.svg` or `.png`) and correctly sized for panel display.

## Updating Icon Cache (Optional)

After adding new icons to your system, you might need to update the icon cache to ensure GNOME recognizes the new icons:

```bash
gtk-update-icon-cache ~/.local/share/icons

## Make contrasting versions

## Creating White and Black Versions of Icons

To ensure your icons are visible and distinct against any background in the GNOME Shell top panel, it's useful to create both white and black versions of each icon. This can be achieved using `sed` commands to modify the SVG files directly.

1. **Adding White Fill to Icons**:

Navigate to your icons directory:

```bash
cd ~/.local/share/icons/
```

Then, use the following `sed` command to add a white fill to each SVG file. Replace `/path/to/your/icons/` with the actual directory containing your SVG icons:

```bash
for file in /path/to/your/icons/*.svg; do
    sed -i 's/\"\/>/\" fill=\"#ffffff\"\/>/g' "$file"
done
```

This command searches for the end of the SVG tag (`"/>`) and adds a white fill attribute (`fill="#ffffff"`) before it.

2. **Creating Black Versions**:

After you've prepared the white versions of your icons, create black versions by modifying the white-filled icons:

```bash
for icon in material-design-*.svg; do
    sed 's/fill="#ffffff"/fill="#000000"/g' "$icon" > "${icon%.svg}-black.svg"
done
```

This command takes each SVG file with a white fill, replaces the white fill color with black (`fill="#000000"`), and saves the result as a new file with `-black` appended to the original filename.

**Note**: These commands are powerful tools for batch processing SVG files. They allow you to quickly prepare icons in both color schemes, enhancing the versatility of your Argos scripts' visual design.

# Setting Up an Audio Toggle Feature with Argos

This guide details creating an audio toggle feature using a bash script and the Argos extension for GNOME Shell. The toggle allows switching between predefined audio sinks, such as headphones and speakers, directly from the top panel.

## Preparing an Audio Toggle Script

1. **Identify Audio Sinks**: First, identify the names of the audio sinks you want to switch between. Use `pactl list short sinks` to list available sinks and find their names.

The following command can help:

```
pactl list short sinks
```

2. **Script Creation**: Create `toggle_audio.sh` in `~/bin` to toggle between your audio sinks. This script checks the current default audio sink and switches to the other.

```bash
    #!/bin/bash

    # Define the sink names
    HEADPHONES_SINK="alsa_output.usb-Your_Headset_Name-00.analog-stereo"
    SPEAKERS_SINK="alsa_output.usb-Your_Speaker_Name-00.analog-stereo"

    # Add your toggle function here
```

    Replace `Your_Headset_Name` and `Your_Speaker_Name` with the actual sink names you identified earlier.

3. **Make Executable**: Ensure the script is executable by running:

```
    chmod +x ~/bin/toggle_audio.sh
```

## Integrating with Argos

1. **Argos Configuration**: Create a new script in `~/.config/argos` to interface with `toggle_audio.sh`. This script will display the current audio output and provide a menu to switch outputs.

```bash
    #!/bin/bash

    # Define the sink names
    HEADSET_SINK="alsa_output.usb-HEADSET_DEVICE_NAME-00.iec958-stereo"
    SPEAKERS_SINK="alsa_output.usb-SPEAKER_DEVICE_NAME-00.iec958-stereo"

    # Define the icons
    HEADSET_ICON="audio-headset-symbolic"
    SPEAKER_ICON="audio-speakers-symbolic"
    FALLBACK_ICON="audio-card"

    # Function to get the current default audio sink
    getCurrentSink() {
        pactl get-default-sink
    }

    # Function to determine the next action, icon based on the current sink, and display current output
    determineOutputAndNextAction() {
        local current_sink=$(getCurrentSink)
        if [[ "$current_sink" == *"$HEADSET_SINK"* ]]; then
            # Current output is Headset
            echo "Audio Output (Headset) | iconName=$HEADSET_ICON"
            echo "---"
            echo "Switch to SPEAKERS Speakers | iconName=$SPEAKERS_ICON bash='$HOME/bin/toggle_audio.sh toggle' terminal=false refresh=true"
        elif [[ "$current_sink" == *"$SPEAKERS_SINK"* ]]; then
            # Current output is SPEAKERS Speakers
            echo "Audio Output (SPEAKERS Speakers) | iconName=$SPEAKERS_ICON"
            echo "---"
            echo "Switch to HEADSET Headset | iconName=$HEADSET_ICON bash='$HOME/bin/toggle_audio.sh toggle' terminal=false refresh=true"
        else
            # Fallback if current output is unrecognized
            echo "Audio Output (Unrecognized) | iconName=audio-card"
            echo "---"
            echo "Switch Audio Output | iconName=audio-card bash='$HOME/bin/toggle_audio.sh toggle' terminal=false refresh=true"
        fi
    }

    # Main
    determineOutputAndNextAction
```

    Ensure you define the sink names and icons as in your `toggle_audio.sh` script.

2. **Add Icons**: For visual feedback, add appropriate icons to `~/.local/share/icons`, ensuring they are named as referenced in your Argos script

3. **Refresh Argos**: After saving your Argos script, it should automatically appear in the GNOME Shell top panel. If not, restart GNOME Shell or log out and back in.

By following these steps, you create a practical audio output switcher integrated into your GNOME Shell environment, enhancing productivity and ease of use.
