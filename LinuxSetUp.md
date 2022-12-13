# This is mine setup for hacking machine 

## TODO
Make repository from this

```bash
#!/bin/bash

# vim gnome is cool because it can copy whole file to system clipboard :D
sudo apt install vim-gtk3

# vim template
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh

# vim custom config
curl -s https://gist.githubusercontent.com/sekkabak/814aa5620561097cd16ed266fcd892d4/raw/17bb0101eef0637480746ad59fa3b76fca97a3d3/.vimrc > ~/.vimrc

# tmux template
git clone https://github.com/samoshkin/tmux-config.git /tmp/tmux-conf
/tmp/tmux-conf/install.sh
rm -rf /tmp/tmux-conf

# custom tmux config
curl -s https://gist.githubusercontent.com/sekkabak/a1b8c6b00b3314658beb86c111370d37/raw/ec9e820e4c219be01dd8551a9a22819ab6d88be4/.tmux.conf > ~/.tmux.conf

# custom zsh config
curl -s https://gist.githubusercontent.com/sekkabak/908a9a9710e99ad697156316474e4238/raw/62ffbcbbe3cc61e824c332dddd5f222f07055131/.zshrc > ~/.zshrc

```

## VI
First install:
https://github.com/amix/vimrc
Second, my custom changes:
https://gist.githubusercontent.com/sekkabak/814aa5620561097cd16ed266fcd892d4/raw/17bb0101eef0637480746ad59fa3b76fca97a3d3/.vimrc

## TMUX
First install:
https://github.com/samoshkin/tmux-config
Second, my custom changes:
https://gist.githubusercontent.com/sekkabak/a1b8c6b00b3314658beb86c111370d37/raw/ec9e820e4c219be01dd8551a9a22819ab6d88be4/.tmux.conf

### Set variable that is global to all tmux panes
```bash
export ABC=123 && tmux setenv ABC $ABC
```

## ZSH
Custom configuration:
https://gist.githubusercontent.com/sekkabak/908a9a9710e99ad697156316474e4238/raw/62ffbcbbe3cc61e824c332dddd5f222f07055131/.zshrc