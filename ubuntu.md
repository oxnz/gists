### Find package containing file

    apt-get install apt-file
    apt-file update
    apt-file search stdlib.c

### Get Source

(Note this unpacks to the current working directory)

    apt-get source coreutils

### Search packages/show descriptions

    apt-cache search perl
    apt-cache show eclipse-cdt

### What is currently installed/what files does a package provide?

    dpkg --get-selections | grep mesa
    dpkg -L libgl1-mesa-dri

### Grub Customizer

    sudo add-apt-repository ppa:danielrichter2007/grub-customizer
    sudo apt-get update
    sudo apt-get install grub-customizer
    Applications -> Grub Customizer
