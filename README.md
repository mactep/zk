# zk

Bash script that I use to manage my notes. Heavily inspired on
[sirupsen's zk](https://github.com/sirupsen/zk), I highly recommend using his solution.

## Dependencies
* [Neovim 0.5+](https://neovim.io/)
* [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim)
* [ripgrep](https://github.com/BurntSushi/ripgrep)
* `git` (optional)

## Setup
* Clone the repository.
* Add run permission to script: `chmod u+x zk`
* Define your Zettelkasten directory: `echo "export ZK_PATH=path/to/your/zk" >> ~/.bashrc`
* Put `zk` somewhere in `$PATH` if you want to call it directly.
* Install Neovim, `telescope.nvim` and `ripgrep`.
* Put `zk.vim` in your vim configuration (either source it inside `init.vim` or
  some directory of the `runtimepath`).

## Usage
* `zk new`: create a new note inside `$ZK_PATH`.
* `zk search`: open Neovim and telescope to search for notes inside `$ZK_PATH`.
* `zk grep`: open Neovim and telescope to search for notes contents inside `$ZK_PATH`.
* `zk push`: commit all the changes inside the `$ZK_PATH` and pushes to the
  remote repository, if in a git repository.
* `zk diff`: uses `git diff` to show the changes in the `$ZK_PATH`.

## Neovim functionalities
* `<leader>zf`: Search for a note using telescope inside `$ZK_PATH`.
* `<leader>zg`: grep the content of the notes inside `$ZK_PATH`.
* `<leader>zb`: Browse the files inside `$ZK_PATH`. Inserting a filename and
  typing `<C-e>` will create a new note with the appropriate prefix, equivalent
  to running `zk new filename`.
* `<leader>zl`: find for a note and insert it as a link at the current cursor
  position.
* `<C-l>`: the same as above, but in insert mode.
* `Zk`: Used to create a new note, with or without a filename.
* `Backlinks`: List all notes that link to the current one.
