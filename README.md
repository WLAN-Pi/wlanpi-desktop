# wlanpi-desktop

A minimal desktop environment for WLAN Pi bookworm images.

## Features

- Lightweight Openbox window manager with LXPanel for resource-constrained computers.
- Disabled by default to minimize overhead when not in use.
- Simple command-line management via the `wlanpi-gui` utility.
- Firefox ESR pre-configured for WLAN Pi WebUI integration.
- Optional autologin support.
- Configurable screen blanking with 10-minute default.

## Installation

Currently only tested on Bookworm. No support for older releases.

Install from the WLAN Pi package repository:

```bash
sudo apt update
sudo apt install wlanpi-desktop
```

## Usage

### Enable desktop environment

```bash
sudo wlanpi-gui enable
```

This sets the system to boot into graphical mode and starts LightDM immediately.

### Disable desktop environment

```bash
sudo wlanpi-gui disable
```

Returns the system to headless console mode.

### Check status

```bash
wlanpi-gui status
```

Shows current desktop state, autologin status, and screen blanking configuration.

### Autologin management

Enable automatic login to desktop (no password prompt):

```bash
sudo wlanpi-gui autologin-enable
sudo systemctl restart lightdm
```

Disable autologin (require manual login):

```bash
sudo wlanpi-gui autologin-disable
sudo systemctl restart lightdm
```

### Screen blanking control

Disable screen blanking for always-on displays:

```bash
sudo wlanpi-gui blanking-disable
```

Re-enable screen blanking with 10-minute timeout:

```bash
sudo wlanpi-gui blanking-enable
```

## Components

The package installs and configures the following desktop components:

- **Window manager:** Openbox
- **Panel:** LXPanel (customized for WLAN Pi)
- **Display manager:** LightDM with GTK greeter
- **Terminal:** xfce4-terminal
- **File manager:** PCManFM with desktop integration
- **Web browser:** Firefox ESR
- **Network management:** NetworkManager with nm-applet

## Default configuration

- Desktop is disabled on installation (multi-user.target).
- Screen blanking is enabled with a 10-minute timeout.
- Autologin is disabled (requires manual login).
- LightDM service is disabled until explicitly enabled.

## Notes

- SSH access remains available regardless of desktop state.
- When desktop is active, console is accessible via Ctrl+Alt+F1-F6.
- Firefox is pre-configured to trust the WLAN Pi self-signed certificate.
- HDMI display connection is required for graphical operation.

## License

BSD 3-Clause License. See LICENSE file for details.
