# git

make an alias for a nicer log tree:

    git config --global alias.tree "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
    git tree
    
to update cached files after modifying `.gitignore`:

    git rm -r --cached .
    git add .

or, specifically for the files in `.gitignore`:

    for file in `cat .gitignore`  ; do git rm -r --cached $file; done

rename a branch (e.g. `master` to `new_branch`)

    git branch -m master new_branch

if after pulling from a remote repository the HEAD detaches

    git checkout origin/master
    git branch -D master
    git branch master
    
or

    git checkout master
    # Reset master back to origin/master
    git reset --hard origin/master

## Adding an external module

    git submodule add git://github.com/someuser/repo.git lib/repo

This will create a directory named `lib/repo` and link it to the github `repo` repository. Now, initialize the submodule and clone the code to it:

    git submodule update --init --recursive

