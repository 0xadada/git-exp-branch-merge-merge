# Git Experiment: Branch / Merge / Merge

Experiment tests the workflow where there is a master branch, user checks
out feature branch from master branch. User commits work to feature branch.
Work continues in parallel in master branch. User on feature branch merges
master `32836`, does a push to GitHub. Finally `32839` on master, merges
in feature branch with `--no-ff`, and commits the commit message.


```
32804  echo "#1" >> 1
32805  git add -A && git commit -m "#1"
32806  echo "#2" >> 1
32812  git commit -am "#2"
32814  git push origin master

32815  git checkout -b feature
32816  echo "#a" >> a
32817  git add -A && git commit -m "#a"
32818  echo "#b" >> a
32819  git commit -am "#b"
32820  git push origin feature

32821  git checkout master
32822  echo "#3" >> 1
32823  git commit -am "#3"
32824  echo "#4" >> 1
32825  git commit -am "#4"
32826  git push origin master

32827  git checkout feature
32828  echo "#c" >> a
32829  git commit -am "#c"
32836  git merge master
32837  git push origin feature

32838  git checkout master
32839  git merge feature --no-ff
32840  git push origin master
```

## Final History log
1. Merge 'feature' into 'master' includes: #c, #b, #a
1. Merge 'master' into 'feature' includes #4 and #3
1. #c
1. #4
1. #3
1. #b
1. #a
1. #2
1. #1
