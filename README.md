# zk

Bash script that I use to manage my notes. Heavily inspired on
[sirupsen's zk](https://github.com/sirupsen/zk), I highly recommend using his solution.

## Setup

* Clone the repository.

* Add run permission to script: `chmod u+x zk`

* Define your Zettelkasten directory: `echo "export ZK_PATH=path/to/your/zk" >> ~/.bashrc`

* Define your editor. It defaults to Neovim: `echo "export ZK_EDITOR=your_editor" >> ~/.bashrc`

* Put `zk` somewhere in `$PATH` if you want to call it directly.

## Search inside vim

`vimgrep /pattern/ ./**` search recursively
`vimgrep /pattern/ ./**/*.md` search recursively on markdown files
