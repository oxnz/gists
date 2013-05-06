### Stop git prompting for user

    git config remote.origin.url git@github.com:the_repository_username/your_project.git

### Enable Colour

    git config --global color.diff auto
    git config --global color.status auto
    git config --global color.branch auto

### Create new repo over existing files
    
    #Create the repo
    git init                                                                                                                                                                                                                                                              
    git commit -m "Initial commit"                                                                                                                                                                                                                                        
    git remote add origin https://github.com/arunh/<REPO>.git
    git config remote.origin.url git@github.com:arunh/<REPO>.git
    git push -u origin master

    #Resolve merge of generated artefacts by editing after pull
    git pull
    git add .gitignore                                                                                                                                                                                                                                                    
    git add README.md
    git commit -m "Resolved merge conflicts"
    git push

### Setup a local-remote rep

Create the "remote" repo

    cd ~/GitRepo
    mkdir fb-app.git
    cd fb-app.git
    git init --bare

Clone the repo or import into it

    git clone ~/GitRepo/fb-app.git

OR:

    cd ~/LocalCode/fb-app
    git init
    git add .gitignore pom.xml src/
    git remote add origin ~/GitRepo/fb-app.git
    git commit -m "Initial commit"
    git push origin master

### Branching

New branch:

    git checkout -b "newbranch"

Rebase from master:

    git checkout master
    git pull
    git checkout newbranch
    git rebase master

Push back with rebase:

    git pull origin newbranch
    git push origin newbranch

Delete a branch:

    git branch -d <branchName> //local
    git push origin --delete <branchName> //remote

Checkout a remote branch:

    git checkout -b interrupt_handling origin/interrupt_handling

### Revert

    git log (to get commit)
    git checkout 9aaf1187b9376e1ec68016d769200a94a0c276e0 eclipse_dev/BlinkingLED/main.cpp

### Keep Fork Updated

Once:

    git remote add upstream git@github.com:codahale/dropwizard.git

To update:

    git pull --ff-only upstream master
    git push origin master
    git fetch all

### Delete remote branch

    git push origin :power_save

Still need local cleanup

    git branch -d power_save

### Tagging 

    git tag -a v0.1 -m "Initial working version"
    git push --tags
    git describe --tags

### Auto Staging

Use this command to stage tracked files, including deleting previously tracked files:

For current working path:

    git add -u .

For ALL working tree:

    git add -u




