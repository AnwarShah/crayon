# Crayon

A dark 16 color colorscheme for Vim, Gvim, and Nvim

NOTE: This is still a heavy WIP and everything is subject to change. Once I'm happy with the colors I'll add support for more terminal emulators. Until then crayon only officially supports terminals that use the .Xresources/.Xdefaults file(s).

![](https://raw.githubusercontent.com/dylanaraps/crayon-theme/master/screenshots/vimrc.png)

## Screenshots

#### Xresources
![](https://raw.githubusercontent.com/dylanaraps/crayon-theme/master/screenshots/xresources.png)

#### Markdown with Goyo.vim
![](https://raw.githubusercontent.com/dylanaraps/crayon-theme/master/screenshots/markdown.png)

## Features

* Supports Vim, Gvim and Neovim
* Supports Neovim with true color enabled
* Supports Neovim's built in terminal mode

* Plugin Support
* Supports Vim-Airline


## Installation

### *Vim

#### 1.1: Preferred Method
Use a plugin manager like [Plug](https://github.com/junegunn/vim-plug).

```VimL
Plug 'dylanaraps/crayon-theme'
```

Using plug you can easily update the plugin with

```VimL
:PlugUpdate
```

#### 1.2: Manual Install
Place 'crayon.vim' file into 'colors' folder within your Vim directory, e.g. '~/.*vim/colors/'

#### 2: Now What?
Once you've installed the theme, put this in your '~/.*vimrc' and you should be all set.

```VimL
set background=dark
colorscheme crayon
```

### Plugin Support
Crayon currently supports these vim plugins:

* Vim-Airline

Feel free to request support for your favourite plugins and I'll happily add them to the list!


#### Vim-Airline
Add this line to your .*vimrc:

```VimL
let g:airline_theme = 'crayon'
```

### Customization
You can customize all of the theme's colors by adding some lines to your .*vimrc. Here's an example that changes the color of the line numbers:

```VimL
" Changes the Line Number colors
autocmd ColorScheme * highlight LineNr guibg=#FFFFFF guifg=#191919 ctermbg=7 ctermfg=8
```

guibg/guifg change the background and foreground in neovim with true colors enabled and gvim. These values must be a hex code. e.g #FFFFFF

ctermbg/ctermfg change the background and foreground in vim/neovim They must be a number between 0 and 255. [More Info](http://vim.wikia.com/wiki/Xterm256_color_names_for_console_Vim).

"LineNR" is the highlight group for vim's linenumbers. If you'd like to change the colors of anything else you need to figure out the highlight group.

I've found that the easiest way to do that is a vim mapping I found which tells you the highlight group of whatever's under your cursor. Just add these 2 lines to your .*vimrc and reopen. Then  press f10.

```VimL
" Shows the highlight group of whatever's under the cursor
map <F10> :echo "hi<" . synIDattr(synID(line("."),col("."),1),"name") . '> trans<'
\ . synIDattr(synID(line("."),col("."),0),"name") . "> lo<"
\ . synIDattr(synIDtrans(synID(line("."),col("."),1)),"name") . ">"<CR>
```

The autocommands must be added before the colorscheme line in your vimrc otherwise they won't work. Here's an example.

```VimL
" This autocmd changes the background to #000000
autocmd ColorScheme * highlight Normal guibg=#000000 ctermbg=0

colorscheme = crayon
```

### Changing the Background Color
If you don't like the default background color you can easily change it without having to edit the theme! You just need to add a single line to your .*vimrc before the colorscheme line above.

This currently only works with dark background colors as the theme doesn't have a light varient yet.

```VimL
" This line changes the background color
au ColorScheme * hi Normal guibg=#181818 ctermbg=8

colorscheme = crayon
```

#### Protip
If you have multiple autocmds it's good to group them, you can do so like this:

```VimL
augroup ColorOverride
au!
autocmd ColorScheme * highlight Normal guibg=#000000 ctermbg=0
autocmd ColorScheme * highlight LineNr guibg=#FFFFFF guifg=#191919 ctermbg=7 ctermfg=8
augroup END
```

### Terminal Installation

#### xterm, Urxvt and terminals that use the .Xresources/.Xdefaults file.
Add the contents of the .Xresources file to your own .Xresources.

Support for other terminals is coming once I've finalized the schemes colors. In the meantime you can go to [Terminal.sexy](http://terminal.sexy/), import the contents of the .Xresources file from the repo and then export it to the terminal format of your choice.

#### Hex Colors

[1] are the color codes for terminal vim that are used for highlight groups.

| Color       | Hex     | [1] |
|-------------|---------|-----|
| black		  | #101112 |  0  |
| darkred	  | #4d2525 |  1  |
| darkgreen	  | #3b4a35 |  2  |
| darkyellow  | #784231 |  3  |
| darkblue	  | #2d4963 |  4  |
| darkmagenta | #3d2e4f |  5  |
| darkcyan	  | #263a40 |  6  |
| gray		  | #6a6f7a |  7  |
| darkgray	  | #282c33 |  8  |
| red		  | #b27b78 |  9  |
| green		  | #9dae71 | 10  |
| yellow	  | #d8c27a | 11  |
| blue		  | #7495b6 | 12  |
| magenta	  | #b59cd8 | 13  |
| cyan		  | #81c9c2 | 14  |
| white		  | #c9d4d8 | 15  |

#### Credits

* [RNB, a Vim colorscheme template](https://gist.github.com/romainl/5cd2f4ec222805f49eca)
* Used to create the colorscheme
