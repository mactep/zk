# zk

Bash script that I use to manage my notes. Heavily inspired on
[sirupsen's zk](https://github.com/sirupsen/zk), I highly recommend using his solution.

## Dependencies

* [Neovim](https://neovim.io/)
* [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim)
* [ripgrep](https://github.com/BurntSushi/ripgrep)

## Setup

* Clone the repository.
* Add run permission to script: `chmod u+x zk`
* Define your Zettelkasten directory: `echo "export ZK_PATH=path/to/your/zk" >> ~/.bashrc`
* Put `zk` somewhere in `$PATH` if you want to call it directly.
* Install Neovim, telescope.nvim and ripgrep.

## Built-in functionalities
### Search

`vimgrep /pattern/ ./**` search recursively

`vimgrep /pattern/ ./**/*.md` search recursively on markdown files

### Vim commands
``` vim
command! -nargs=1 Search execute 'silent grep! -r -i <args> .' | copen
command! -nargs=1 SearchTag execute 'silent grep! -r -w -i \\#<args> .' | copen
command! Backlinks execute 'silent grep! -H -r % .' | copen
command! -nargs=* ZK execute "edit $ZK_PATH/".strftime("%Y%m%d%H%M")."_<args>.md"
```
