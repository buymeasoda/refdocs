
# Working with files and directories

## Open and edit files

Open a file

	open <file>
	
Open the current directory in finder

	open .
	
Open a file with the specified application (Mac OSX)

	open -a /Applications/<app> <file>

Open file in the nano text editor

	nano <file>


## Work with remote mounts and external hard drives

Access remote mounts (such as Samba shares and external hard drives)

	cd /Volumes


## Copy, move and delete files

Copy a file

	cp <source> <destination>

Move or rename a file

	mv <source> <destination>

Remove a file

	rm <file>

Remove files and folders recursively without confirmation

	rm -rf <dirname>

Symbolic link from source file to destination file

	ln -s <destination> <source>


## Create and delete directories

Create a directory

	mkdir <dirname>

Create multiple directories in one step

	mkdir -p dir1 dir2/subdir1 dir2/subdir2 dir3
	
Create multiple directories in one step, alternative syntax using array of items via {}

	mkdir -p dir1/{subdir1,subdir2} dir2

Can also nest this syntax

	mkdir -p tmp/{d1/{sd1,sd2},d2,d3/{sd3,sd4}}

Remove a directory

	rmdir <dirname>


## Create, read and output files

Output the contents of the file

	cat <file>
	
Create a new file, and add content via the command line, end with CTRL + d (on a fresh line)

	cat > <file>
	
Append text via the command line to the file (end with CTRL + s)

	cat >> <file>

Overwrite the contents of the file with text

	echo "<text>" > <file>
	
Append the contents of file with the text

	echo "<text>" >> <file>

Create a file called filename

	touch <filename>
	
Paginate through a text file output directly in the terminal

	more <filename>

Paginate through a text files output directly in the terminal (includes ability to go backwards)

	less <filename>
