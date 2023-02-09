[VSCodeVim](https://github.com/VSCodeVim/Vim#-vscodevim-tricks)
Vim emulation in vscode. Not _exactly_ the real thing, but pretty close, and also emulates a lot of essential plugins. Can get pretty slow, especially when working with multiple cursors. 

`gd` - jump to definition.
`gq` - on a visual selection reflow and wordwrap blocks of text, preserving commenting style. Great for formatting documentation comments.
`gb` - adds another cursor on the next word it finds which is the same as the word under the cursor.
`af` - visual mode command which selects increasingly large blocks of text. For example, if you had "blah (foo [bar 'ba|z'])" then it would select 'baz' first. If you pressed af again, it'd then select [bar 'baz'], and if you did it a third time it would select "(foo [bar 'baz'])".
`gh` - equivalent to hovering your mouse over wherever the cursor is. Handy for seeing types and error messages without reaching for the mouse!
 `gr` for [vim-scripts/ReplaceWithRegister: Replace text with the contents of a register.](https://github.com/vim-scripts/ReplaceWithRegister)

