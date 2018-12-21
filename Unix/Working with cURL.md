# Using cURL

## Downloading files

Download single file

    curl <url>
    curl http://www.google.com

Output downloaded result to a file

    curl <url> > <file>
    curl http://www.google.com > google.txt

    curl -o <file> <url>
    curl -o google.txt http://www.google.com

Output downloaded file based on destination file name (eg. about.html)

    curl -O <url>
    curl -O https://www.google.com/intl/en/about.html

Fetch and output multiple files

    curl -O <url1> <url2> <url3>

Follow location headers

    curl -L <url>
    curl -L http://google.com

Verbose activity information

    curl -v <url>
    curl -v http://www.google.com

Resume partially downloaded file

    curl -C - -O <url>
