https://www.youtube.com/watch?v=jaI3Hcw-ZaA&t=65s
https://www.youtube.com/watch?v=DzNmUNvnB04
https://www.youtube.com/watch?v=GH3kpsbbERo&t=51s


https://hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/
https://github.com/hamvocke/dotfiles
https://rootloops.sh/?sugar=5&colors=6&sogginess=3&flavor=2&fruit=2&milk=1
https://builtin.com/articles/tmux-config
https://github.com/tmux-plugins
https://github.com/tmux-plugins/tpm
https://github.com/tmux-plugins/list
https://github.com/catppuccin/tmux


Dot files for Jai:
https://github.com/techisteps/dotfiles.git

In **Alpine**  make sure `git`, `neovim`, `stow`, `tmux` and `bash` are installed.

```bash
doas apk update
doas apk update
doas apk add bash
doas apk add git
doas apk add stow
doas apk add tmux
doas apk add neovim
```

```bash
cd ~
git clone https://github.com/techisteps/dotfiles.git
cd dotfiles
stow -S tmux
```

Leader Key: default is`CTRL-B` but we have over written to `CTRL-A` in configuration.

Run `tmux` and press `Leader Key` + `SHIFT i` (Caps I) , this will start installation of TPM plugins.


Helpful commands:
`CTRL-A`: Leader Key
`CTRL-A`+ ? : Show key bindings
`CTRL-A`+ `:` will open command  prompt, type and enter `list-keys` this will show all key bindings
`CTRL-A`+ `:` will open command  prompt, type and enter `customize-mode` this will put you in a mode where you can customize all aspects of Tmux

In TMUX command prompt 
	`set-option mouse on` to enable mouse support and 
	`set-option mouse off` to disable mouse support.