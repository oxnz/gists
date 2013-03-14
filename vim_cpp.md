Vi for C Development
====================

Getting Library Source Code
---------------------------

### MacOS X

* Open source for [10.7.4 release](http://www.opensource.apple.com/release/mac-os-x-1074/).

Download the stdlib and kernel (xnu). For 10.7.4 these were:

* [xnu-1699.26.8](http://www.opensource.apple.com/tarballs/xnu/xnu-1699.26.8.tar.gz)
* [Libc-763.13](http://www.opensource.apple.com/tarballs/Libc/Libc-763.13.tar.gz)

Un-archive each under /usr/src

### Linux

Get Libc Source and Tag it. From directory /usr/src:

    sudo apt-get source libc6

OR

    sudo apt-get install apt-src
    sudo apt-src install libc6

Either of the above choices will create directory:

    /usr/src/eglibc-2.15

This can be tagged:

    cd eglibc-2.15
    sudo ctags -R  --fields=+S .

Get the Kernel Source:

    sudo apt-get install kernel-source

This will install source as an archive:

    /usr/src/linux-source-3.2.0/linux-source-3.2.0.tar.bz2

Unzip the archive, and this can be tagged (assuming you unzipped the archive to give root at /usr/src/linux-source-3.2.0/linux-source-3.2.0):

    /usr/src/linux-source-3.2.0
    ctags -R  --fields=+S linux-source-3.2.0


Generate C-Tags
---------------

In /usr/src directory:

    ctags -R  --fields=+S .

Common Tag Directory
--------------------

This helps to be consistent across Mac/Linux or when versions change. Link as appropriate based on above:

   mkdir ~/.tags
   ln -s /usr/src/eglibc-2.15/tags libc_tags
   ln -s /usr/src/linux-source-3.2.0/tags kernel_tags

Setup VimRc
-----------

The following line in .vimrc points to tags. Important to include current directory, possibly needs a better solution for more complex project stuctures:

    set tags=~/.tags/libc_tags,~/.tags/kernel_tags,./tags

The following line in .vimrc will cause ctags to run on save updating project tags

    au BufWritePost *.c,*.cpp,*.h silent! !ctags -R &