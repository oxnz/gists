Bootloader needs to be installed on

    /dev/sda

General build and maintenance tools

    sudo apt-get install cmake
    sudo apt-get install build-essential
    sudo apt-get install apt-file
    sudo apt-file update
    sudo apt-get install vim

Install Git and basic config for box

    sudo apt-get install git
    git config --global user.name "arunh"
    git config --global user.email arun@arunhorne.co.uk
    mkdir GitHub
    cd GitHub/
    git clone https://github.com/arunh/config.git
    cd config/
    git config remote.origin.url git@github.com:arunh/config.git
    git checkout ubuntu
    ./rewire.sh <--- does most of the config work
    vi /home/arunh/.bashrc  <--- source bash_env from config

Graphics specific stuff and libraries (only need SDL if doing dev)   

    sudo apt-get install libsdl1.2-dev
    sudo apt-get install mesa-utils
    dpkg -L nvidia-current
    glxinfo <--- make sure we have direct rendering

Setup SSH server

    sudo apt-get install openssh-server
    (copy id_rsa[.pub] to ~/.ssh)
    cat id_rsa.pub >> ~/.ssh/authorized_keys

Misc tweaks

    sudo apt-get remove indicator-messages <--- annoying mail icon
