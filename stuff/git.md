# git command

## general process
```
git init
git config --global user.name "***"
git config --global user.email ***@.com
git remote add origin https://github.com/***.git
git pull origin master
git add ***
// to all files
git add --
git commit -m "***"
git push origin master
```
## checkout
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

# manage branch
```
// delete a local git branch
git branch -d branch_name 
// delete a remote git branch
git push <remote name> --delete <branch name> 
git push origin --delete branch_name
```

# merge branch and request pull
```
// merge feature/topic => develop
git checkout develop
git merge feature/topic

git fetch origin

// check remote
git remote -v
// add remote origin
git remote add orogin <https://github.com/***.git>
// add remote upstream (usually original repository before fork)
git remote add upstream <https://github.com/***.git>
```

# etc
```
git reset // git add 취소
git log --graph --all --decorate --oneline // git history
```

https://gist.github.com/heiswayi/350e2afda8cece810c0f6116dadbe651
