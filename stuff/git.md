```
git init
git config --global user.name ""
git config --global user.email xx@.com
git remote add origin https://github.com/xx/xx.git
git pull origin master
git add xx
git commit -m ""
git push origin master
git checkout -b develop // 원격저장소, local 모두 존재하지 않는 
git checkout -b feature/subject
git branch -d branch_name // delete a local git branch
git push <remote name> --delete <branch name> // delete a remote git branch
git push origin --delete branch_name
git fetch // update branch
git checkout -t origin/develop // 원격저장소/branch 이름으로 branch를 생성하면서 해당 branch trac, 원격저장소에는 존재하고 local에는 아직 존재하지 않는 경우
git commit -m ""
git checkout develop
git merge feature/topic
git fetch origin
git reset // git add 취소
git log --graph --all --decorate --oneline // git history
```

https://gist.github.com/heiswayi/350e2afda8cece810c0f6116dadbe651
