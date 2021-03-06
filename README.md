# hellogit
hello git

## I. Create:
    1. Clone an existing repository
        git clone ssh://user@domain.com/repo.git
        (ex: git clone git@github.com:DengpanFu/hellogit.git)
    2 Create a new local repository:
        git init
    3. Reset remote:
        git remote rm origin
        git remote add origin git@github.com:DengpanFu/hellogit.git
        git branch -M main
        git push -u origin main
## II. Local Changes:
    1. Check changed files in working directory
        git status
    2. check changes to tracked files
        git diff
        2.1 compare difference between local file and remote file
            git fetch origin master
            git diff origin/master -- [file]
    3. add changes to the next commit
        git add <file> <...> (some changes) OR
        git add ./-A (all changes)
    4. commit changes
        git commit -m "message"
## III. Commit history
    1. show commits
        git log (show all commits, starting with newest)
        git log -l (show the latest l changes)
        git log -p <file> (show changes over time for a specific file)
        git reflog (check history cmds)
        git blame <file> (who changed what and when in <file>)\
## IV. Branches & Tags
    1. list all existing branches
        git branch -av
    2. switch HEAD branch
        git checkout <branch>
    3. create a new branch based on your current HEAD
        git branch <branch-name>
    4. create and switch to a new branch
        git checkout -b <branch-name> (based on HEAD)
        git checkout -b <branch-name> <remote/branch-name> (create local branch for remote branch)
    5. create connection between local branch and remote branch
        git branch --set-upstream <branch-name> <remote/branch-name>
    6. create a new tracking branch based on a remote branch
        git checkout --track <remote/branch>
    7. delete a local branch
        git branch -d <branch>
    8. mark commit with a tag
        git tag <tag-name> (mark current commit)
        git tag <tag-name> <commit-id> (mark a specific commit id)
        git tag -a <tag-name> -m "message" <commit-id> (specify tag message)
    9. show tag
        git tag (show all tags)
        git tag <tag-name> (show a specific tag)
## V. Update & Publish
    1. list all current configured remotes
        git remote -v
    2. show info about a remote
        git remote show <remote>
    3. add new remote repository, named <remote>
        git remote add <short-name> <url>
        (git remote add origin git@github.com:DengpanFu/hellogit.git
        git push -u origin master)
    4. download all changes from <remote>, but don't integrate into HEAD
        git fetch <remote>
    5. download changes and directly merge/integrate into HEAD
        git pull <remote> <branch>
    6. publish local changes on a remote
        git push <remote> <branch>
        git push -u <remote> <branch> (-u combine remote `master` with local `master`)
    7. delete a branch on a remote
        git branch -dr <remote/branch>
    8. publish your tag
        git push --tags
## VI. Merge & Rebase
    1. merge <branch> into current HEAD
        git merge <branch>
    2. rebase current HEAD onto branch(don't rebase published commits)
        git rebase <branch>
    3. abort a rebase
        git rebase --abort
    4. contibue a rebase after resolving conflicts
        git rebase --continue
## VII. Undo
    1. discard changes in working direcoty
        git reset --hard HEAD (current head)
        git reset --hard HEAD^ (the last head, and HEAD^^ by analogy)
        git reset --hard HEAD~100 (the last 100th head)
        git reset --hard commit-id (first few letters is enough for commit-id)
    2. discard local changes in a specific file
        git checkout HEAD <file>
        git checkout -- <file>
    3. discard local changes after pull from remote
        git reset --hard origin/master
## VIII. Remove remote directory
    git rm --cache -r useless-directory
    git commit -m "remove directory from remote repository"
    git push
