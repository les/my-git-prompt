# my git prompt

```console
# without my patch
[me@computer:~/my-repo](main)$ ls -a
./  ../  .bare/  .git  main/  my-branch/
[me@computer:~/my-repo/main](main)$ ls -a
./  ../  .git  README.md

# with with patch
[me@computer:~/my-repo](worktrees)$ ls -a
./  ../  .bare/  .git  main/  my-branch/
[me@computer:~/my-repo/main](main)$ ls -a
./  ../  .git  README.md
```

## usage

```console
mkdir -p ~/.local/share/git/completion/
cp /usr/share/git/completion/git-prompt.sh ~/.local/share/git/completion/
patch -u ~/.local/share/git/completion/git-prompt.sh git-prompt.patch
cat << EOF >> ~/.bashrc
. ~/.local/share/git/completion/git-prompt.sh
GIT_PS1_SHOWDIRTYSTATE="yes"
GIT_PS1_SHOWSTASHSTATE="yes"
GIT_PS1_SHOWUNTRACKEDFILES="yes"
GIT_PS1_SHOWUPSTREAM="auto"
GIT_PS1_STATESEPARATOR=""
GIT_PS1_SHOWCONFLICTSTATE="yes"
GIT_PS1_DESCRIBE_STYLE="branch"
GIT_PS1_SHOWCOLORHINTS="yes"
PS1='[\# \t \w]$(__git_ps1 "(%s)")\$ '
EOF
. ~/.bashrc
```
