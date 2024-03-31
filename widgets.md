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
