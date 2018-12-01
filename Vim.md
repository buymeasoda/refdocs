# VIM

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

Move by word boundary to start of word foward / backward (delimiter / whole word)

	w
	W
	b
	B

Move by word boundary to end of word (delimeter / whole word)

	e
	E

Move by a count for any action (eg. move forward 3 words)

	<count><action>
	3w

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

Delete to start of next word, end of current word, start / end of line

	dw
	de
	d^
	d$
	d<motion>

Repace a single character (without triggering insert mode)

	r

## Search

Search for text

	/<search-string>

Next / previous search result

	n
	N

Next / previous word under cursor

	*
	#

## Cut, Copy, Paste

Cut current line

	dd

Copy the current line

	yy

Paste buffer after / before cursor

	p
	P

Paste multiple instances of the copied text

	<num>p
	5p

Visual selection character / line (to apply commands to)

	v
	V

Visual section with block select

	CTRL + v

Cut text visually marked

	d

Copy text visually marked (yank)

	y

Replace selected text

	c

## Undo / Redo

Undo
	
	u

Redo

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
