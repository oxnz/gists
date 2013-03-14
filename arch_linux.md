### Full system update

    pacman -Syu

### X11

Basic Xorg:

    pacman -S xorg-server
    pacman -S xorg-xauth

Also need a window manager:

    pacman -S slim

To configure sshd for X11, follow this [link](https://wiki.archlinux.org/index.php/Secure_Shell#X11_forwarding).