# Base16 Vim

Supports console [Vim][1], graphical Vim and [Neovim][2].

Over [200 themes][3] plus light/dark variations are available. Here are
some of our favorites:

The `classic-dark` theme:

![base16-vim classic-dark][10]

The `horizon-dark` theme:

![base16-vim horizon-dark][11]

The `onedark` theme:

![base16-vim onedark][12]

## Terminal Themes

For terminal Vim (non-gui) please ensure you are using a base16 terminal
theme. Have a look at the list of [official][4] and [unofficial][5]
themes for your terminal of choice.

## Installation

Add `colorscheme base16-default-dark` to your `~/.vimrc`.

### Vundle

Add the following to your `~/.vimrc` file and run `PluginInstall` in Vim.

```vim
Plugin 'tinted-theming/base16-vim'
```

### vim-plug

Add the following to your `~/.vimrc` file and run `PlugInstall` in Vim.

```vim
Plug 'tinted-theming/base16-vim'
```

### Pathogen

```bash
cd ~/.vim/bundle
git clone https://github.com/tinted-theming/base16-vim.git
```

### Manual

```bash
cd ~/.vim/colors
git clone git://github.com/tinted-theming/base16-vim.git base16
cp base16/colors/*.vim .
```

### Manual neovim

```bash
cd ~/.config/nvim/colors
git clone git://github.com/tinted-theming/base16-vim.git base16
cp base16/colors/*.vim .
```

## 256 colorspace

If using a Base16 terminal theme designed to keep the 16 ANSI colors
intact (a "256" variation) **and** have sucessfully modified your 256
colorspace with [base16-shell][6].This will cause vim to access the
colours in the modified 256 colorspace. Please **do not** enable this
simply because you have a 256 color terminal as this will cause colors
to be displayed incorrectly.

you'll need to add the following to your `~/.vimrc` **before** the
colorsheme declaration.

### Vim

```vim
let base16_colorspace=256 " Access colors present in 256 colorspace
```

### Neovim (lua)

```lua
-- Access colors present in 256 colorspace
vim.g.base16_colorspace = 256
```


## Background transparency

If you're using a terminal with an opacity of `< 1`, you'll notice that
base16-vim doesn't respect this transparency by default. You can enable
transparent backgrounds with base16-vim by adding the following settings
to your vim/neovim setup.

### Vim

Add the following variable to your `~/.vimrc` before your colorscheme
declaration.

```vim
let base16_background_transparent=1 " Make vim background transparent to work alongside transparent terminal backgrounds
```

### Neovim (lua)

Add the following to your lua setup before your colorscheme declaration.

```lua
-- Make vim background transparent to work alongside transparent terminal backgrounds
vim.g.base16_background_transparent = 1
```

## Troubleshooting

There is a script to help troubleshoot colour issues called `colortest`
available in the [Base16 Shell][6] repository.

If you are using a ISO-8613-3 compatible terminal ([vim docs][7],
[neovim docs][8]), and you see a green or blue line, try to enable
`termguicolors`:

```vim
set termguicolors
```

### Green line numbers

![green line numbers screenshot][13]

If your Vim looks like the above image you are using a 256 terminal
theme without setting `let base16_colorspace=256` in your `~/.vimrc`.
Either set `let base16_colorspace=256` in your `~/.vimrc` or use a non
256 terminal theme.

### Blue line numbers

![blue line numbers screenshot][14]

If your Vim looks like the above image you are setting `let
base16_colorspace=256` in your `~/.vimrc` but either not running [Base16
Shell][6] or [Base16 Shell][6] is not working for your terminal. Either
ensure [Base16 Shell][6] is working by running the `colortest` available
in the [Base16 Shell][6] repository or not setting `let
base16_colorspace=256` in your `~/.vimrc`.

## Customization

If you want to do some local customization, you can add something like
this to your `~/.vimrc`:

```vim
function! s:base16_customize() abort
  call Base16hi("MatchParen", g:base16_gui05, g:base16_gui03, g:base16_cterm05, g:base16_cterm03, "bold,italic", "")
endfunction

augroup on_change_colorschema
  autocmd!
  autocmd ColorScheme * call s:base16_customize()
augroup END
```

## Contributing

See [`CONTRIBUTING.md`][9], which contains building and contributing
instructions.

[1]: https://github.com/vim/vim
[2]: https://github.com/neovim/neovim
[3]: https://github.com/tinted-theming/base16-schemes
[4]: https://github.com/tinted-theming/home#official-templates
[5]: https://github.com/tinted-theming/home#unofficial-templates
[6]: https://github.com/tinted-theming/base16-shell
[7]: https://github.com/vim/vim/blob/23c1b2b018c8121ca5fcc247e37966428bf8ca66/runtime/doc/options.txt#L7876
[8]: https://neovim.io/doc/user/options.html#'termguicolors'
[9]: CONTRIBUTING.md
[10]: screenshots/base16-vim-screenshot-classic-dark.png
[11]: screenshots/base16-vim-screenshot-horizon-dark.png
[12]: screenshots/base16-vim-screenshot-onedark.png
[13]: screenshots/without-base16colorspace-256-with-256-terminal-theme.png
[14]: screenshots/with-base16colorspace-256-without-base16-shell.png
