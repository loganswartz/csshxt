# csshxt
Cluster SSH script/program for tmux based on the behavior of csshX.

## Usage
`csshxt <host> <host2> <host3> ...`

In a tmux session, use the above syntax to open a new window and create individual panes for each host specified. By default, your keystrokes will be broadcast to every pane simultaneously.

## Hotkeys
Hotkey | Function
------ | --------
`<prefix> C-x` | Jump to specified pane by number and disable pane-synchronization
`<prefix> C-s` | Jump to command pane and toggle pane-synchronization
`<prefix> C-d` | Disable input to a pane
`<prefix> C-e` | Enable input to a pane

## Notes
By default, the actual command executed in each pane upon initialization is simply `ssh <host>`, but you can specify a custom one by changing the `SSH_COMMAND` constant to fit your needs. Specifying usernames with the regular `user@host` format will thus work as expected, and further configurations in your `~/.ssh/config` will also be respected.

Hotkeys can also be modified by changing the `KEY` constants at the top of the script with a text editor.

For easier use, consider using shell expansion to cut down on the amount of typing you have to by using the `{#..#}` syntax, where the `#` are numbers. For example, `csshxt test-vm{01..04}` would expand to `csshxt test-vm01 test-vm02 test-vm03 test-vm04`.
