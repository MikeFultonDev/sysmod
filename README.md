# Setup work tree separate from git dir

See [example](https://stackoverflow.com/questions/16792737/git-change-working-directory)

## Steps

- On z/OS, make the directory where you want your repo, e.g. `mkdir sysmod`
- Initialize your git repo, specifying your work tree directory:
```
git --git-dir sysmod --work-tree /dsfs/txt/SYS1 init
```
- On z/OS, set up your .gitattributes to mark files as EBCDIC

*.gitattributes*
```
text zos-working-tree-encoding=IBM-1047
```

- If you want to only check in _some_ files under git control, use `info/exclude` instead of `.gitignore`, e.g.


*info/exclude*
```
*
!README.md
!f1.txt
!f2.txt
!f3.txt
```

will indicate that only the 4 files `README.md`, `f1.txt`, `f2.txt`, `f3.txt` should be git managed.

- On z/OS, specify where to push your code to:
```
git remote add origin git@github.com:MikeFultonDev/sysmod.git
git branch -M main
git push -u origin main
```
