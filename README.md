# helpful-command-lines

## git

* remove all branchs not on remote 
```bash
git fetch -p && git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -D
```
