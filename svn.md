SVN
---

### Check out only the 'trunk' directories from entire repository

    repo=myrepo
    url=https://svn.arunhorne.co.uk/svn/$repo
    svn list $url > projects.txt
    mkdir $repo
    cd $repo
    for p in $(cat ../projects.txt); do svn co "$url/$p/trunk" $p/trunk; done

### Create branch

    svn copy https://svn.arunhorne.co.uk/svn/project1/trunk https://svn.arunhorne.co.uk/svn/project1/branches/mybranch -m "A comment"

### Rollback a changeset

More info in the [SVN Book](http://svnbook.red-bean.com/en/1.5/svn-book.html#svn.branchmerge.basicmerging.undo).

    svn merge -c -43662 https://svn.arunhorne.co.uk/svn/project1/trunk

### See all changes since a revision / between two revisions

    svn diff -r 44550
    svn diff -r 44550:44670

#### Find Revision Branch was From

    svn log --stop-on-copy

#### Merging

Find branch rev (e.g. command above), then from a clean trunk execute: 

    svn merge -r <branch_rev>:HEAD https://svn.arunhorne.co.uk/svn/project1/branch/foo
