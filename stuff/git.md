# git command

## general process
```
git init
git config --global user.name "***"
git config --global user.email ***@.com
git remote add origin https://github.com/***.git
git fetch origin
git pull origin master (develop, feature/topic)
git add ***
// to all files
git add --
git commit -m "***"
git push origin master (develop, feature/topic)
```
## make branch and checkout
```
// first 2~6 digits are ok
git checkout {commit_id}
// in the case that there is no branch in remote and local repository
git checkout -b develop
git checkout -b feature/subject
// update branch
git fetch 
// in the case of making the new branch of "develop" in a local repository
// and tracking it that exsits in a remote repository
git checkout -t origin/develop 
```
## add remote repository
```
// add remote origin
git remote add origin <https://github.com/***.git>
// add remote upstream (usually original repository before fork)
git remote add upstream <https://github.com/***.git>
// check remote
git remote -v
```

## manage branch
```
// delete a local git branch
git branch -d branch_name 
// delete a remote git branch
git push <remote name> --delete <branch name> 
git push origin --delete branch_name
```

## merge branch
```
// merge feature/topic => develop
git checkout develop
git merge feature/topic
```

## request pull
```
git fetch origin

// request pull
// ...

// update upstream repository's info.
git fetch upstream
// merge upstream/master to local
git merge upstream develop
// update origin/develop with upstream data
git push origin develop
```

# etc
```
// cancel git add
git reset 
// git history
git log --graph --all --decorate --oneline 
```

https://gist.github.com/heiswayi/350e2afda8cece810c0f6116dadbe651
