# Checksum and hash utilities

## Checksum tools

MD5 (Message digest algorithm)

    md5

SHA 1/256/512 (Secure hash Algorithm)

    shasum
    shasum -a 256
    shasum -a 512

File usage

    md5 <file>
    shasum <file>
    cat <file> | md5
    cat <file> | shasum

String input usage

    echo <string> | md5
    echo <string> | shasum

## Cyclic redundancy tools

CRC (Cyclic redundancy check)

    crc32 <file>

## Securely generate a hash locally from text input

- Allows using command line to generate hash without logging input to shell history
- Replace `shasum` with any of the checksum variants to generate the required hash

Bash version

    read -sp 'Input: ' input; echo; echo -n 'Output: '; echo -n "$input" | shasum; unset input

Fish version

    read -sP 'Input: ' input; echo -n 'Output: '; echo -n "$input" | shasum; set -e input
