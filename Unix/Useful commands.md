
# Useful commands

## System commands

Output current terminal settings

	stty -a

Change Unix shell (enter path to new shell when prompted)

	chsh

Exit the current terminal session

	exit

Restart the system

	reboot

Clear the current screen of text

	clear


## Clipboard commands

Copy content to the clipboard (eg. cat file.txt | pbcopy, copies contents of file.txt to the clipboard)

	pbcopy
 
Outputs the current contents of the clipboard

	pbpaste


## History commands

Output a list of earlier commands with a unique ID for each command

	history

Delete bash history from memory (delete or edit ~/.bash_history to modify saved bash history commands)

	history -c
 
Execute the command from the history specified by the history id (eg. !25, execute command 25)

	!<history id>
 
Execute the last command (useful for something like forgetting sudo, eg. sudo !!)

	!!


## Generate MD5 and SHA1 hashes

Generate MD5 hash from file

    md5 <file>

Generate SHA1 hash from file

    shasum <file>


## Other useful commands

Word, line, character and byte count for file or piped input

	wc

	mail

	curl

General maths interpreter (allows general equations entered into command line)

	bc

### Show files with non-ascii characters

	grep -P "[\x80-\xFF]" <files>

### Show line endings for files

Unix: ASCII text
DOS: ASCII text, with CRLF line terminators

	file <file>

## Utilities and tools

Sort lines of text

	sort

Report or filter out repeated lines

	uniq
