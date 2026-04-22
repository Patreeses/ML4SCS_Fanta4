# Suggested Git Workflow
To prevent too many merges from git pull, I (Felix) would suggest the following Git Workflow:

```
git pull --rebase
# Arbeiten
git add file.py # ggf.
git commit -am "this is the commit message" # possible more than once per session
git pull --rebase
git push
```

In case, the second git pull doesn't work, I would suggest the following:

```
git rebase --abort
git pull # This time I would accept the pull merge, because it is annoying to deal with a rebase conflict.
git push 
```