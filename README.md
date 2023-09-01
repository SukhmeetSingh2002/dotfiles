## Intializing

```
git init --bare $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.bashrc
```
### Zash
```
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.zshrc
```

Now we can directly add and commit files

## Installing on new machine

- Set the alias
```
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.bashrc
```
### Zash
```
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.zshrc
```

- Ignore
```
echo ".dotfiles >> .gitignore"
```


- Clone
```
git clone --bare https://github.com/SukhmeetSingh2002/dotfiles-wsl.git $HOME/.dotfiles
```

- Now you can checkout. This will *overwrite* contents


- For this you can backup your old files
```
mkdir -p .dotfiles-backup && \
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
xargs -I{} mv {} .config-backup/{}
```

- Set show untracked to no

```
config config --local status.showUntrackedFiles no
```


