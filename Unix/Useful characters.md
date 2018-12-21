# Useful characters

Pipe to chain commands together

    |

Direct output to a file

    >

Append content to existing file

    >>

Read content from a file

    <

Shortcut for the home directory (eg. cd ~)

    ~

Represents the current directory

    .

Traverse up one directory level (eg. cd ..)

    ..

Execute the script with the name script_name

    ./script_name

Alternative way to executure script

    source script_name

Separate long commands with a `\` at the end of each line

    \

Example:

    cd dir/name && \
    somecommand && \
    someothercommand

Join multiple commands together, but only run the second command if the first succeeds

    &&

Example:

    cd dir && touch file && echo "contents" > file

Join multiple commands together, but only run the second command if the first one fails

    ||

Example:

    cd dir/name || mkdir dir/name
