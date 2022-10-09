---
title: tmux
---

tmux can split your terminal into multiple terminals, either locally or remotely. It can split a single terminal into multiple panes (windows?), and it keep a remote session going even when you go offline.

`tmux` is an alternative to `screen`

[Tmux vs. Screen tool comparison – Linux Hint](https://linuxhint.com/tmux_vs_screen/)

[Getting Started · tmux/tmux Wiki · GitHub](https://github.com/tmux/tmux/wiki/Getting-Started)

# tmux default status bar


    Bottom left:

    - `[0]` current session name
    - `0:bash*` window list?
        - index:name*current
        - For example `1:bash- 2:bash 3:bash*`
    - `"asia"` title of the active pane?

# tmux basic workflow 

- New session: `tmux new -s session_name`
- Prefix key: `C-b`
- Detach session: `C-b d`
- Reattach session: `tmux attach-session -t session_name`
- Panes
    - Split vertically (left-right): `C-b %`
    - Split horizontally (up-down): `C-b "`
        - (is that `ctrl+b shift+'`?)
            - (yes)
    - Move focus: `C-b (arrows)`
    - Quick move: `C-b q` `C-b q 1`
    - Next pane: `C-b o`
    - Swap panes: `C-b C-o`
- Windows
    - Next window `C-b n`
- Sessions
    - Tree view: `C-b s`
    - In tree view:
        - Kill selected item: `x`
        - Toggle preview: `v`
        - Exit tree mode: `q`
- Clients
    - Client list: `C-b S-d`
