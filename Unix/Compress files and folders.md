# Compress files and folders

## Zip

Collect and compress files and directories into a zip file

    zip -r <output-file> <source-files>

Unzip a standard zip file archive

    unzip <file>

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
