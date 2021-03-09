# zk

Bash script that I use to manage my notes. Heavily inspired on
[sirupsen's zk](https://github.com/sirupsen/zk), I highly recommend using his solution.

## Dependencies

* [Neovim](https://neovim.io/)
* [fzf](https://github.com/junegunn/fzf)
* [fzf.vim](https://github.com/junegunn/fzf.vim)
* [ripgrep](https://github.com/BurntSushi/ripgrep)

## Setup

* Clone the repository.
* Add run permission to script: `chmod u+x zk`
* Define your Zettelkasten directory: `echo "export ZK_PATH=path/to/your/zk" >> ~/.bashrc`
* Put `zk` somewhere in `$PATH` if you want to call it directly.
* Install Neovim, fzf, fzf.vim, ripgrep and add the following to `$MYVIMRC`:
``` vim
function! RipgrepFzf(query, fullscreen)
  let command_fmt = 'rg --column --line-number --no-heading --color=always --smart-case %s || true'
  let initial_command = printf(command_fmt, shellescape(a:query))
  let reload_command = printf(command_fmt, '{q}')
  let spec = {'options': ['--phony', '--query', a:query, '--bind', 'change:reload:'.reload_command]}
  call fzf#vim#grep(initial_command, 1, fzf#vim#with_preview(spec), a:fullscreen)
endfunction
command! -nargs=* -bang RG call RipgrepFzf(<q-args>, <bang>0)
```

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
