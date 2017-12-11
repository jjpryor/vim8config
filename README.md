# vim8config is a set of configs for Vim 8+

# Pre-Usage primer on packaging
Per vim8 has native package handling, se just git clone and use git submodules.
See also
https://jjpryor.com/vim-packages/

## Native packaging
### Adding a package

Here is an example of how to add a package using Vim’s native approach to packages and git submodules.
```
git submodule init
git submodule add https://github.com/vim-airline/vim-airline.git vim/pack/jjpryor/start/vim-airline
git add .gitmodules vim/pack/jjpryor/start/vim-airline
git commit
```

### Updating packages

To update packages is also just a case of updating git submodules.

```
git submodule update --remote --merge
git commit
```

### Removing a package

Removing a package is just a case of removing the git submodule.

```
git submodule deinit vim/pack/jjpryor/start/vim-airline
git rm vim/pack/jjpryor/start/vim-airline
rm -Rf .git/modules/vim/pack/jjpryor/start/vim-airline
git commit
```

# Usage

Go ahead and git clone this repo to local temp space
```
git clone repo
cd repo
```

then update the modules
```
git submodule update --init --recursive
```

then put the `.vim` and `.vimrc. in place
```
cp -pr vim ~/.vim
cp -pr dot-vimrc  ~/.vimrc
```

