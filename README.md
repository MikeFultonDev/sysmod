# Setup work tree separate from git dir

See [example](https://stackoverflow.com/questions/16792737/git-change-working-directory)

## Steps

- On z/OS, make the directory where you want your repo, e.g. `mkdir sysmod`
- Initialize your git repo, specifying your work tree directory:
```
git --git-dir sysmod --work-tree /dsfs/txt/SYS1
```

