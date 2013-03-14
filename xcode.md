### File Templates

Copy this:

    /Applications/Xcode.app/Contents/Developer/Library/Xcode/Templates/File Templates/*

To here:

    ~/Library/Developer/Xcode/Templates/File Templates

It is recommended to only move the templates you want to avoid duplicates. And edit, e.g:

    ~/Library/Developer/Xcode/Templates/File Templates/C and C++/Header File.xctemplate/___FILEBASENAME___.h

This will result in duplicate entries in Xcode, is recommended to rename each file type:

    mv "Header File.xctemplate" "Custom Header File.xctemplate"
