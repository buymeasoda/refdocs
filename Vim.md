# VIM

## Help

Show help instructions and commands

    :help

Open user manual index

    :help user-manual

Navigate to topic (see navigation below), position cursor inside `|...|` for topic filename and open

    CTRL + ]

Exit help manual

    :q

## General

Commands and actions are extended with modifiers and repeated using counts

    <action><modifier>
    <count><modifier>

Modifiers can be combined with counts to duplicate the modified action

    <action><count><modifier>

Example: Delete three words (`d` delete action, `3` count, `w` word modifier)

    d3w

Example: Move forward three words (`3` count, `w` word modifier)

    3w

## Navigation

Move cursor Up / Down, Left / Right

    j = Up
    k = Down
    h = Left
    l = Right

    h (Left) j (Up) k (Down) l (Right)

Move by a number of lines or characters (eg. up 4 lines)

    <count>j
    4j

Move cursor to top / middle / bottom (High / Middle / Bottom) of page

    H
    M
    L

Go to start of file

    gg

Go to end of file

    G

Page down / up (f = forward, b = back) and half page (d = down, u = up)

    CTRL + f
    CTRL + b

    CTRL + d
    CTRL + u

Go to line number

    <line> SHIFT + G
    <line> gg
    :<line> ENTER

Move to start, start (whitespace) and end of line

    ^
    0
    $

Move by word boundary to start of word forward / backward (delimiter / whole word)

    w
    W
    b
    B

Move by word boundary to end of word (delimiter / whole word)

    e
    E

## Edit

Insert text under / after the cursor

    i
    a

Insert text at the beginning / end of the current line

    I
    A

Insert a line above / below and insert text

    o
    O

Insert text at the end of the word

    ea

Repeat the last action or edit

    .

Join line below to the current one

    J

Transpose two letters (performs forward delete/cut then paste)

    xp

Complete current partial word based on existing word list (cycle through next / previous entries)

    CTRL + N
    CTRL + P

## Delete

Delete text in front / behind cursor

    x
    X

Delete current line (also cuts text to clipboard)

    dd

Delete to beginning / end of current word or start of next word

    db
    de
    dw

Delete to start / end of line

    d^
    d$

Apply modifier to delete command (eg. Delete three words)

    d<modifier><command>
    d3w

## Change

Change entire line (combines delete and insert)

    cc

Change a word to beginning / end or start of next work

    cb
    ce
    cw

Delete to start / end of line

    c^
    c$

Change from the cursor to the end of the line

    C

Delete character / line at cursor and substitute text

    s
    S

Replace a single character (without triggering insert mode)

    r<character>

Replace multiple characters in replace mode

    R<type>

## Search

Search forward / backwards for text

    /<search-string>
    ?<search-string>

Next / previous search result

    n
    N

Next / previous word under cursor

    *
    #

## Replace

Replace all instances of string `old` with string `new` in current file

    :%s/old/new/g

Replace all instances with per item confirmation

    :%s/old/new/gc

## Cut, Copy, Paste

Cut current line

    dd

Copy the current line

    yy

Copy to beginning / end of current word or start of next word

    ye
    yw
    yb

Copy to start / end of line

    y^
    y$

Paste buffer after / before cursor

    p
    P

Paste multiple instances of the copied text

    <num>p
    5p

## Visual Mode

Visual selection mode by character / line (to apply commands to)

    v
    V

Exit visual selection mode

    ESC

Move visual marker to opposite end of selection

    o

Visual section with block select

    CTRL + v

Cut text visually marked

    d

Copy text visually marked (yank)

    y

Replace selected text

    c

## Undo / Redo

Undo edits and changes

    u

Redo edits and changes

    CTRL+R

Revert last change to original state

    U

## Save / Quit

Save file

    :w

Quit vim (normal, without saving / no prompt)

    :q
    :q!

Write and quit

    :wq

## Configuration

Enable / disable line numbers

    :set number
    :set nu
    :set nonumber
    :set number!
    :set nonu
    :set nu!

Set editor to paste mode (to retain pasted formatting)

    :set paste

Set highlight search results or disable highligh

    :set hlsearch
    :set nohlsearch

## Split Windows

Split window horizontally

    ctrl + ws

Split window vertically

    ctrl + wv

Switch between windows

    ctrl + ww

Quit active window

    ctrl + wq
