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

# This repo `vim8config` Usage

Go ahead and git clone this repo to local temp space
```
git clone vim8config
cd vim8config
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


# Resources
+ https://github.com/w0rp/ale
+ http://liuchengxu.org/posts/use-vim-as-a-python-ide/
+ https://github.com/rodjek/vim-puppet
+ https://dmerej.info/blog/post/lets-have-a-pint-of-vim-ale/
+ https://github.com/pearofducks/ansible-vim
+ https://github.com/Kuniwak/vint
+ https://github.com/Valloric/YouCompleteMe
+ https://github.com/airblade/vim-gitgutter.git
+ https://github.com/junegunn/fzf.vim
+ https://github.com/junegunn/fzf


submodules installed via the following commands
```
git submodule add https://github.com/vim-airline/vim-airline.git vim/pack/jjpryor/start/vim-airline
git submodule add https://github.com/vim-airline/vim-airline-themes.git vim/pack/jjpryor/start/vim-airline-themes
git submodule add https://github.com/w0rp/ale.git vim/pack/jjpryor/start/ale
git submodule add https://github.com/python-mode/python-mode.git vim/pack/jjpryor/start/python-mode
git submodule add https://github.com/rodjek/vim-puppet vim/pack/jjpryor/start/vim-puppet
git submodule add https://github.com/pearofducks/ansible-vim vim/pack/jjpryor/start/ansible-vim
git submodule add https://github.com/Valloric/YouCompleteMe vim/pack/jjpryor/start/YouCompleteMe
git submodule add https://github.com/junegunn/fzf.vim vim/pack/jjpryor/start/fzf.vim
git submodule add https://github.com/airblade/vim-gitgutter.git vim/pack/jjpryor/start/vim-gitgutter
```

## FZF fuzzy finder
fzf is available in Fedora 26 and above, and can be installed using the usual method:
```
sudo dnf install fzf
```
## YouCompleteMe
Use the leader key `\` and then `g` to match calls and defintions

### YouCompleteMe Installation
from https://github.com/Valloric/YouCompleteMe#user-guide
Install development tools and CMake:
```
sudo dnf install automake gcc gcc-c++ kernel-devel cmake
```
Make sure you have Python headers installed:
```
sudo dnf install python-devel python3-devel
```
Compiling YCM with semantic support for C-family languages:
```
cd ~/.vim/bundle/YouCompleteMe
./install.py --clang-completer
```

### YouCompleteMe Python Semantic Completion

Completion and GoTo commands work out of the box with no additional configuration. Those features are provided by the jedi library which supports a variety of Python versions (2.6, 2.7, 3.2+) as long as it runs in the corresponding Python interpreter. By default YCM runs jedi with the same Python interpreter used by the ycmd server, so if you would like to use a different interpreter, use the following option specifying the Python binary to use. For example, to provide Python 3 completion in your project, set:
```
let g:ycm_python_binary_path = '/usr/bin/python3'
```
If the value of g:ycm_python_binary_path is an absolute path like above it will be used as-is, but if it's an executable name it will be searched through the PATH. So for example if you set:
```
let g:ycm_python_binary_path = 'python'
```
YCM will use the first `python` executable it finds in the PATH to run jedi. This means that if you are in a virtual environment and you start vim in that directory, the first python that YCM will find will be the one in the virtual environment, so jedi will be able to provide completions for every package you have in the virtual environment.

