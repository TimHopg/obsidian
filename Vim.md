#Vim #Programming #todo 

`:help term` - for help
`vimtutor` - on the command line for tutorial

`V/v` - visual line/character mode
`i` - insert mode (`esc` to exit)
`:` - command line mode

`:vs` split screen vertically
`vim -Xp` - Compare two files side by side

`:term` - open terminal
`:bel term` - terminal below
`:bel vert term` - terminal below vertical

`u` - undo
`Ctrl + r` - redo

` =` - autoindents
`ggVG=` - autoindent all
	`gg` - first line
	`V` - visual line mode
	`G` - go to last line
	` =` - indent

`Ctrl + N` - autocomplete
#### Search and Replace
`:%s/existing_term/replacement_term/options`
`:s` - first instance
`:%s` - all instances
`/c` - with confirmation
`:noh` - un-highlight

`CTRL + W` - windows 'leader' key
	`+ W` - switch window
	`+ C` - close window
#
#### System Clipboard
`"*y` - yank
`"*p` - paste
#### Prefs
`:edit ~/.vimrc` - edit vim prefs
`\\t` - terminal into bottom right window
	`noremap <Leader>\t :botright vertical terminal<CR>`
#### Navigation
`h` <=> `l` - left <=> right
`j / k` - down and up
`w` - beginning of next word
`e` - end of current word
`b` - back one word
`SHIFT + left/right` - skip through words in insert mode

`:x` - `:wq`

```bash
  1 " syntax highlighting
  2 syntax on
  3
  4 " indent to four spaces and autoindent
  5 set tabstop=4
  6 set shiftwidth=4
  7 filetype indent on
  8 set smartindent
  9 set autoindent
 10 set smarttab
 11
 12 " Auto wraps left and right cursor keys to next/previous line & insert mode
 13 set whichwrap+=<,>
 14 set ww+=[,]
 15
 16 " display line number
 17 set number
 18
 19 " Highlight cursor line underneath the cursor horizontally.
 20 set cursorline
 21
 22 " Ignore caps during search. Unless searching for caps
 23 set ignorecase
 24 set smartcase
 25
 26 " keystroke \\t for terminal window vertical
 27 noremap <Leader>\t :botright vertical terminal<CR>
 28
 29 " Show partial command you type in the last line of the screen.
 30 set showcmd
 31
 32 " Use highlighting when doing a search.
 33 set hlsearch
 34
 35 syntax enable
 36 " set background=dark
 37 " colorscheme solarized
```
#### Customisation
Neovim (lunar)
Tmux