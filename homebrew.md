Homebrew
--------

### How to install an older version of a brew

    cd /usr/local
    brew versions sbt
    git checkout -b sbt-0.11.2 1557bc7
    brew uninstall sbt
    brew install sbt
    git checkout master
    git branch -d sbt-0.11.2

### Launch Agents

    ~/Library/LaunchAgents

### Dupes

Software on MacOS that is more recent. This will give Vim with clipboard support:

    brew install homebrew/dupes/vim

