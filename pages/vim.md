---
title: Vim
---

Vim and vim-mode in other tools. Should probably be broken up into different pages.

## Tips

- `cit` Change Inside Tag. Can be used anywhere in the line and will find the nearest tag to change inside of.
- Vim Surround [#](https://github.com/tpope/vim-surround)
  - `dst` Delete Surrounding Tag.
- Replace with Register [#](https://github.com/vim-scripts/ReplaceWithRegister)
	- `gr` replace with unnamed register 
	- `grr` replace line with unnamed register
	- `"xgr` replace with register `x`


## Workflows

* Run `vim index.html` to create a new HTML file from scratch. Have good defaults like shorter tabs etc.
* Working with files in a project. Find files, create new.
* Create a new directory when creating a new file (Create file in non-existing directory)
* Easily add support for a new workflow, for e.g. editing Liquid templates with Jekyll
* Built-in terminal
    * Toggle, hide
    * Scrollback

### Working with the terminal 

When Zsh is also configured to use Vim mode, what commands get interpreted by which Vim?

`:term` to open a terminal in a new window (will split the screen)
`Ctrl-d` to close the window (will remove the split)
`Ctrl-W N` for Normal mode (special "terminal-normal" mode, `:h Terminal-mode`)
`Ctrl-W :` command mode (Ex command)

### Working with buffers and windows

## Key Concepts

### word vs WORD

> A word consists of a sequence of letters, digits and underscores, or a sequence of other non-blank characters, separated with white space (spaces, tabs, \<EOL>). This can be changed with the 'iskeyword' option. An empty line is also considered to be a word.
> A WORD consists of a sequence of non-blank characters, separated with white space. An empty line is also considered to be a WORD.

## Usage

```
operator [number] motion

operator - is what to do, such as d for delete
[number] - is an optional count to repeat the motion
motion - moves over the text to operate on, such as w, $
```

## Motions

* `h`,`j`,`k`,`l` Arrows
* `bB` To beginning of word/WORD
* `eE` To end of current word/WORD
* `wW` To start of next word/WORD
* `ge` To end of previous word
* `$` To end of the line
* `0` To start of line

## Repeating

* `3w` Move cursor 3 words forward. Equivalent to pressing `w` three time.
* `30i- Esc` Insert a dash 30 times

## Finding

* `f`, `F` Find next, previous character
* `fo` Find next "o"
* `3fq` Find third "q"
* `*`, `#` Find next, previous word under cursor
* `/` Search forward
* `?` Search backward
* `n`,`N` Find next, previous result
* `Ctrl+g` show status line

## Jumping

* `%` jump to matching parens
* `0` start of line
* `$` end of line
* `gg` beginning of file
* `G` end of file
* `20G` line 20
* `Ctrl-o` Back (history)
* `Ctrl-I` Forward (history)

## Inserting

* `i` Insert before cursor (before the character under the cursor)
* `I` Insert at beginning of line
* `a` Append After cursor (after the character under the cursor)
* `A` Append After line (at end of line)
* `o` Open line below
* `O` Open line above

## Editing

* `r` Replace character
* `rx` E.g., replace with "x"
* `R` Replace multiple characters (overwrite). This is actually a different mode, called "REPLACE (paste)"
* `c` Change (goes into Insert mode)
* `ce` Change to end of word
* `dw` Delete to next word
* `d2w` Delete two words
* `de` Delete to end of word
* `d$` Delete to end of line
* `dd` Delete current line
* `2dd` Delete two lines
* `df` Delete until find result (inclusive)
* `df.` E.g., delete until .
* `u` Undo
* `U` Undo whole line, restore line to its original state
* `.` Redo?
* `s/old/new/g` Substitute "new" for "old". `/g` means globally (for the current line)
* `#,#s/old/new/g` Substitute within lines in range #,#
* `%s/old/new/g` Replace across entire file
* `%s/old/new/gc` Replace across entire file but ask for confirmation each time

## Selection and Registers

* Things deleted with `d` get stored in a register
* `p` Put command, put from the register. Put below/after
* `v` Visual selection
* `y` Yank selection, or with operator
* `yw` E.g., yank one word

## Files

* `w` Save file
* `w` With selection - save subset of file
* `r` Read file
* `r !` Read output of command
* `r !ls` E.g., read output of `ls`

## Commands

* `:!` Run external commands
* `:!ls` E.g., run `ls`
*

## Window Management

* `Ctrl+W h,j,k,l` Move between windows in direction
* `Ctrl+ww` Switch windows

# Tips

## For learning vim

* Disable Insert mode features, don't allow backing beyond the initial insertion point, don't allow arrow keys
* Relative line numbers
* (from [Improving Vim Speed - YouTube](https://www.youtube.com/watch?v=OnUiHLYZgaA))

# Articles

[Vim: Seven habits of effective text editing](https://www.notion.so/Vim-Seven-habits-of-effective-text-editing-40b3fdf678554603bd51aa403be2b221)

[Your problem with Vim is that you don't grok vi. · GitHub](https://www.notion.so/Your-problem-with-Vim-is-that-you-don-t-grok-vi-GitHub-d5e7ddfbbafc43e8b77df0a7097b0fc8)

[vimrctips - best practices - reddit/vim](https://www.notion.so/vimrctips-best-practices-reddit-vim-5722987377ab4e3c86a4c5a148ac7d0c)

[Copy, cut and paste | Vim Tips Wiki | Fandom](https://vim.fandom.com/wiki/Copy,_cut_and_paste)

[Vim Cheat Sheets](https://www.notion.so/Vim-Cheat-Sheets-e0b3515c72dd414d93c079f8942c2300)

# Links

* [Vim Awesome](https://vimawesome.com/) \- Plugins
* [Newest - Vim Colors](http://vimcolors.com/)
* r/[Vim porn](https://www.reddit.com/r/vimporn/)
* [vim wallpaper](https://github.com/LevelbossMike/vim_shortcut_wallpaper)
