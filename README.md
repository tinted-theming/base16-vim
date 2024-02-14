# Tinted Vim

[![Matrix Chat](https://img.shields.io/matrix/tinted-theming:matrix.org)](https://matrix.to/#/#tinted-theming:matrix.org)

Supports console [Vim], graphical Vim and [Neovim].

Over [250 themes] plus light/dark variations are available. Here are
some of our favorites:

The `classic-dark` theme:

![tinted-vim classic-dark]

The `horizon-dark` theme:

![tinted-vim horizon-dark]

The `onedark` theme:

![tinted-vim onedark]

## Terminal Themes

For terminal Vim (non-gui) please ensure you are using a terminal theme.
Have a look at the list of [official] and [unofficial] themes for your
terminal of choice.

## Installation

### Lazy.nvim
```lua
{
    "tinted-theming/tinted-vim",
}
```

### Packer

```lua
use {
  "tinted-theming/tinted-vim",
  config = function()
    vim.cmd.colorscheme 'base16-ayu-dark'
  end,
}
```

### Pathogen

```sh
cd ~/.vim/bundle
git clone https://github.com/tinted-theming/tinted-vim.git
```

```vim
Plugin 'tinted-theming/tinted-vim'
```

### vim-plug

Add the following to your `~/.vimrc` file and run `PlugInstall` in Vim.

```vim
Plug 'tinted-theming/tinted-vim'
```

### Vundle

Add the following to your `~/.vimrc` file and run `PluginInstall` in Vim.

```sh
git clone https://github.com/tinted-theming/tinted-vim.git ~/.vim/bundle/tinted-vim
```

```vim
Plugin 'tinted-theming/tinted-vim'
```

#### Symlink

You can use a symlink to easily keep things updated. Update your vim
colors every time you do a `git pull` on the `tinted-vim` repo.

1. Clone `tinted-vim` somewhere:

  ```sh
  git clone git://github.com/tinted-theming/tinted-vim.git ~/projects/tinted-vim
  ```

2. Remove your old vim/nvim `colors/` directory if it exists:

  ```sh
  rm -r ~/.vim/colors # Or ~/.config/nvim/colors for Neovim
  ```

3. Symlink the colors directory:

  ```sh 
  ln -s ~/projects/tinted-vim/colors ~/.vim/colors
  # Or for Neovim
  # ln -s ~/projects/tinted-vim/colors ~/.config/nvim/colors
  ```

### Manual

#### Vim

```sh
cd ~/.vim/colors
git clone git://github.com/tinted-theming/tinted-vim.git tinted-vim
cp tinted-vim/colors/*.vim .
```

#### Neovim

```sh
cd ~/.config/nvim/colors
git clone git://github.com/tinted-theming/tinted-vim.git tinted-vim
cp tinted-vim/colors/*.vim .
```

## 256 colorspace

If using a tinted terminal theme designed to keep the 16 ANSI colors
intact (a "256" variation) **and** have sucessfully modified your 256
colorspace with [tinted-shell].This will cause vim to access the colors
in the modified 256 colorspace. Please **do not** enable this simply
because you have a 256 color terminal as this will cause colors to be
displayed incorrectly.

you'll need to add the following to your `~/.vimrc` **before** the
colorsheme declaration.

### Vim

```vim
let tinted_colorspace=256 " Access colors present in 256 colorspace
```

### Neovim (lua)

```lua
-- Access colors present in 256 colorspace
vim.g.tinted_colorspace = 256
```

## Background transparency

If you're using a terminal with an opacity of `< 1`, you'll notice that
tinted-vim doesn't respect this transparency by default. You can enable
transparent backgrounds with tinted-vim by adding the following settings
to your vim/neovim setup.

### Vim

Add the following variable to your `~/.vimrc` before your colorscheme
declaration.

```vim
let tinted_background_transparent=1 " Make vim background transparent to work alongside transparent terminal backgrounds
```

### Neovim (lua)

Add the following to your lua setup before your colorscheme declaration.

```lua
-- Make vim background transparent to work alongside transparent terminal backgrounds
vim.g.tinted_background_transparent = 1
```

## Troubleshooting

There is a script to help troubleshoot colour issues called `colortest`
available in the [tinted-shell] repository.

If you are using a ISO-8613-3 compatible terminal ([vim docs],
[neovim docs]), and you see a green or blue line, try to enable
`termguicolors`:

```vim
set termguicolors
```

### Green line numbers

![green line numbers screenshot]

If your Vim looks like the above image you are using a 256 terminal
theme without setting `let tinted_colorspace=256` in your `~/.vimrc`.
Either set `let tinted_colorspace=256` in your `~/.vimrc` or use a non
256 terminal theme.

### Blue line numbers

![blue line numbers screenshot]

If your Vim looks like the above image you are setting `let
tinted_colorspace=256` in your `~/.vimrc` but either not running
[tinted-shell] or [tinted-shell] is not working for your terminal. Either
ensure [tinted-shell] is working by running the `colortest` available
in the [tinted-shell] repository or not setting `let
tinted_colorspace=256` in your `~/.vimrc`.

## Customization

If you want to do some local customization, you can add something like
this to your `~/.vimrc`:

```vim
function! s:tinted_customize() abort
  call Base16hi("MatchParen", g:base16_gui05, g:base16_gui03, g:base16_cterm05, g:base16_cterm03, "bold,italic", "")
  " Or Base24hi for base24 themes
endfunction

augroup on_change_colorschema
  autocmd!
  autocmd ColorScheme * call s:tinted_customize()
augroup END
```

## Contributing

See [CONTRIBUTING.md], which contains building and contributing
instructions.

[Vim]: https://github.com/vim/vim
[Neovim]: https://github.com/neovim/neovim
[250 themes]: https://github.com/tinted-theming/schemes
[official]: https://github.com/tinted-theming/home#official-templates
[unofficial]: https://github.com/tinted-theming/home#unofficial-templates
[tinted-shell]: https://github.com/tinted-theming/tinted-shell
[vim docs]: https://github.com/vim/vim/blob/23c1b2b018c8121ca5fcc247e37966428bf8ca66/runtime/doc/options.txt#L7876
[neovim docs]: https://neovim.io/doc/user/options.html#'termguicolors'
[CONTRIBUTING.md]: CONTRIBUTING.md
[tinted-vim classic-dark]: screenshots/tinted-vim-screenshot-classic-dark.png
[tinted-vim horizon-dark]: screenshots/tinted-vim-screenshot-horizon-dark.png
[tinted-vim onedark]: screenshots/tinted-vim-screenshot-onedark.png
[green line numbers screenshot]: screenshots/without-tintedcolorspace-256-with-256-terminal-theme.png
[blue line numbers screenshot]: screenshots/with-tintedcolorspace-256-without-tinted-shell.png
