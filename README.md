![Polychromatic](.readme/logo.png)

A front-end for customising the functionality of your Razer perpherials under GNU/Linux.

## Features

### Controller
| Screenshot | Features |
| ---------- | -------- |
| ![Controller v0-3-8](https://cloud.githubusercontent.com/assets/13032135/24725693/b9766b60-1a47-11e7-926b-df5568a13e8a.png) | <ul><li>Set effects, brightness, colours, DPI and modes supported by the device.</li><li>Create application profiles.</li><li>Set up colours for quick access.</li><li>View all connected devices and configure the daemon-specific settings.</li></ul>

### Tray Applet
| Screenshot | Features |
| ---------- | -------- |
| ![Tray Effects Menu](https://cloud.githubusercontent.com/assets/13032135/24725801/0aa359b2-1a48-11e7-8c4a-638c6024cb08.png) | <ul><li>Quickly change the Chroma effects of your device from this tray applet.</li><li>Set colours and application profiles on-the-fly.</li></ul>

[View all screenshots](.readme/Screenshots.md)

------------

## Device Support

See the [daemon's device support table](https://github.com/terrycain/razer-drivers#device-support) to check whether your device is supported by the daemon. Once it works with the daemon, it's likely to work in Polychromatic too.

However, not all newly supported devices will work straight away. These devices have known issues:

| Keyboard | Mouse | Mousemat | Keypad | Headset |
|   :---:  | :---: |   :---:  | :---:  | :---:   |
| ![Keyboard](.readme/status/keyboard-ok.png) | ![Mouse](.readme/status/mouse-warn.png) | ![Mousemat](.readme/status/mousemat-warn.png) | ![Keypad](.readme/status/keypad-ok.png) | ![Headset](.readme/status/headset-ok.png)

#### Known Issues
* **Mice and mousemats**
  * Profile support will come in a future release.

With developments being made to the daemon, it will eventually be possible to:

* Manage macros for keyboards and keypads.
* Create and run "custom effects".

There are some limitations:

* Profile support is not possible for keypads as the daemon does not support matrixes.


-------------

## Driver Installation

### ![Chroma Drivers](.readme/chroma-drivers.png) Razer Drivers for Linux
If you haven't already, you will need to install the [razer-drivers](http://terrycain.github.io/razer-drivers/) driver and daemon.

Ubuntu and Linux Mint users can install this via this PPA:

    sudo add-apt-repository ppa:terrz/razerutils
    sudo apt update
    sudo apt install python3-razer razer-kernel-modules-dkms razer-daemon razer-doc

Please see the [project website](http://terrycain.github.io/razer-drivers/#download) for instructions for your distribution.


## Polychromatic Installation

#### ![Ubuntu](.readme/ubuntu.png) Ubuntu 16.04+ / Linux Mint 18+

##### Stable Builds

Polychromatic can be installed via this PPA:

    sudo add-apt-repository ppa:lah7/polychromatic
    sudo apt update
    sudo apt install polychromatic

The PPA is recommended as it keeps the application up-to-date.

##### Daily Builds

These builds deliver the newest features and improvements quicker, but are not well tested and may be buggy at times.

    sudo add-apt-repository ppa:lah7/polychromatic-daily
    sudo apt update
    sudo apt install polychromatic

If you later decide to revert back to the stable builds:

    sudo apt remove polychromatic
    sudo rm /etc/apt/sources.list.d/lah7-ubuntu-polychromatic-daily.list*
    sudo add-apt-repository ppa:lah7/polychromatic
    sudo apt update
    sudo apt install polychromatic

#### ![Debian](.readme/debian.png) Debian 8+

**WebKit2 Dependency**

 * Debian 8 "Jessie" provides an old version of `gir1.2-webkit2-4.0` which is incompatible with Polychromatic.
 * Please enable `jessie-backports` and update `gir1.2-webkit2-4.0` and its dependencies.

Packages built for Ubuntu are also compatible with Debian.

Add this line to your `/etc/apt/sources.list`:

    deb http://ppa.launchpad.net/lah7/polychromatic/ubuntu xenial main

(Or `polychromatic-daily` for development builds)

Then add the public key to verify the packages:

    gpg --keyserver hkp://keyserver.ubuntu.com:11371 --recv-keys 6CFDA3EBE08FDDE9
    gpg --armor --export 6CFDA3EBE08FDDE9 | sudo apt-key add -

Followed by updating your Apt sources:

    sudo apt-get update

Otherwise, standalone packages are available from the [releases page](https://github.com/lah7/polychromatic/releases/latest/), or
by following a manual installation below.


#### ![Arch](.readme/arch.png) Arch Linux

Packages for Arch are maintained by [z3ntu](https://github.com/z3ntu). You can install using an AUR wrapper, like as follows:

    yaourt -S polychromatic
    pacaur -S polychromatic

There are two packages:

* [`polychromatic`](https://aur.archlinux.org/packages/polychromatic/) - Latest stable version.
* [`polychromatic-git`](https://aur.archlinux.org/packages/polychromatic-git/) - Latest development version.


#### ![Fedora](.readme/fedora.png) Fedora and ![openSUSE](.readme/opensuse.png) openSUSE

You can add a repository and obtain packages for these distributions via OpenSUSE's Build System.
Thank you to [z3ntu](https://github.com/z3ntu) for setting this up.

* https://software.opensuse.org/download.html?project=hardware%3Arazer&package=polychromatic


#### ![Gentoo](.readme/gentoo.png) Gentoo

Rudimentary ebuilds for Gentoo are maintained by [vifino](https://github.com/vifino) in his personal overlay. These can be installed with these commands:

    sudo layman -a vifino-overlay
    emerge polychromatic


#### ![Other Distributions](.readme/linux.png) Other Distributions / Manual Installation

See further below for which dependencies you will require to install first.

    git clone https://github.com/lah7/polychromatic.git
    cd polychromatic
    git checkout stable
    sudo ./install/install.sh

**If you'd like to use the latest development version** (but potentially unstable), skip this line: `git checkout stable`.

You can update your installation by clicking **"Check for Updates"** in the preferences, or by running:

    ./install/update.sh


### Dependencies

Polychromatic interfaces with the daemon from the [razer-drivers project](https://terrycain.github.io). These packages are required for all distributions:

* [python3-razer](https://github.com/terrycain/razer-drivers)
* [razer-daemon](https://github.com/terrycain/razer-drivers)


| Debian/Ubuntu | Arch | openSUSE |
| ------------- | ---- | -------- |
| [gir1.2-gtk-3.0](https://packages.debian.org/sid/gir1.2-gtk-3.0) | [gtk3](https://www.archlinux.org/packages/extra/x86_64/gtk3/) | |
| [gir1.2-appindicator3-0.1](https://packages.debian.org/sid/gir1.2-appindicator3-0.1) | [libappindicator](https://aur.archlinux.org/pkgbase/libappindicator/?comments=all) | [typelib-1_0-AppIndicator3-0_1](https://software.opensuse.org/package/typelib-1_0-AppIndicator3-0_1)
| [gir1.2-webkit2-4.0](https://packages.debian.org/sid/gir1.2-webkit2-4.0) (>= 2.12.0) | [webkit2gtk](https://www.archlinux.org/packages/extra/x86_64/webkit2gtk/) | [typelib-1_0-WebKit2-4_0](https://software.opensuse.org/package/typelib-1_0-WebKit2-4_0)
| [python3-gi](https://packages.debian.org/sid/python3-gi) | [python-gobject](https://www.archlinux.org/packages/extra/x86_64/python-gobject/) | [python3-gobject](https://software.opensuse.org/package/python3-gobject)
| [python3-setproctitle](https://packages.debian.org/sid/python3-setproctitle) | [python-setproctitle](https://www.archlinux.org/packages/community/x86_64/python-setproctitle/) | [python3-setproctitle](https://software.opensuse.org/package/python3-setproctitle)
| [python3-requests](https://packages.debian.org/sid/python3-requests) | [python-requests](https://www.archlinux.org/packages/extra/any/python-requests/) | [python3-requests](https://software.opensuse.org/package/python3-requests)
| [imagemagick](https://packages.debian.org/sid/imagemagick) | [imagemagick](https://www.archlinux.org/packages/extra/x86_64/imagemagick/) | [imagemagick](https://software.opensuse.org/package/ImageMagick)


## Something not working?

* Check that the driver and daemon are [properly installed](https://github.com/terrycain/razer-drivers#installation) for your distribution.
* Check that your [device has daemon support](https://github.com/terrycain/razer-drivers#device-support).
* For DBUS, daemon or driver bugs, [see if an issue](https://github.com/terrycain/razer-drivers/issues) has been raised on the [razer-drivers repository](https://github.com/terrycain/razer-drivers), otherwise [please create a new issue there](https://github.com/terrycain/razer-drivers/issues/new).

For visual or functional problems with Polychromatic, [please raise an issue here instead](https://github.com/lah7/polychromatic/issues/new).


## Translations

The software is ready to speak multiple languages! Take a look
[at this wiki page](https://github.com/lah7/polychromatic/wiki/How-to-translate-the-application) if you'd like to contribute.


## Donations

This software is developed in my spare time without any expection of money in return,
but if you're [feeling generous](https://github.com/lah7/polychromatic/issues/75), then you are more then welcome to
[donate to the lead developer](https://www.paypal.me/LukeHorwell) of Polychromatic
and [the people who bring you the driver and daemon](https://github.com/terrycain/razer-drivers/blob/master/README.md#contributions).
Thank you for your generosity.
