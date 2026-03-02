# iTerm

## Command Helpers

Open command history tool to list, navigate and autocomplete current command

    ALT + ;

## Marks

Allow navigating window scroll to line positions of defined markers (eg. bookmarks)

Set mark for current line (bottom line in window view)

    SHIFT + CMD + M

Move to prev / next mark

    SHIFT + CMD + UP
    SHIFT + CMD + DOWN

Jump to most recent mark

    SHIFT + CMD + J

## Window Management

Split window vertically and horizontally (adjust pane size by dragging dividers)

    CMD + D
    CMD + SHIFT + D

Close window pane (or use close X button)

    CMD + W

Navigate window panes (alternatively click into pane with mouse)

    CMD + [
    CMD + ]

Maximise current pane to full window (or reset to original size)

    CMD + SHIFT + ENTER

## iTerm Tmux (Control Mode)

Create tmux session (or new named session)

    tmux -CC
    tmux -CC new -s <name>

Attach to most recent tmux session (or target named session)

    tmux -CC attach
    tmux -CC attach -t <name>

List available sessions

    tmux ls
