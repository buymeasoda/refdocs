# Compress files and folders

## Zip

Collect and compress files and directories into a zip file

    zip -r <output-file> <source-files>

Unzip a standard zip file archive

    unzip <file>

List files contained inside zip file without extracting

    unzip -l <file>

## Zip Info

Show files contained in zip file (`-m` show compression rate)

    zipinfo <file>
    zipinfo -m <file>

List directory and file names only

    zipinfo -1 <file>

## Gzip

Gzip file and keep (`-k`) original source file

    gzip <file> -k

Gzip file contents and write to stdout (useful for piping / directing results)

    gzip <file> -c
    gzip <input-file> -c > <output-file>

## Tar

Tar (collect) and Gzip the specified directory to file.tgz

    tar -czvf <file.tgz> <directory>

Uncompress file.tgz

    tar -xzvf <file.tgz>

## Brotli

Install brotli command line processor

    brew install brotli

Compress file with brotli (defaults to keep source and maximum compression)

    brotli <file>
