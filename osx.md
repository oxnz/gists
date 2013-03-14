### Set Hostname

    scutil --set HostName name-of-host

### IntelliJ Data Locations

    ~/Library/Application Support/.IntelliJIdeaXX -- contains the catalog with plugins.
    ~/Library/Preferences/.IntelliJIdeaXX -- contains the rest of the configuration settings.
    ~/Library/Caches/.IntelliJIdeaXX -- contains data caches, logs, local history, etc.

### Create ISO

    hdiutil makehybrid -iso -joliet -o ~/Desktop/tygp21d.iso /Volumes/TYGAMES_R

### Postfix

    postfix stop|start|reload -- daemon control
    mailq -- view mail queue
    /etc/postfix/main.cf -- main config file

### SSD

Enable trim with "Chameleon SSD"

### Launch Agents

    launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.memcached.plist
    edit file --> set KeepAlive as required
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.memcached.plist
    launchctl stop|start homebrew.mxcl.memcached
