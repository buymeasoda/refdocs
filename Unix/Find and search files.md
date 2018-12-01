
# Find and search files

Find allows searching file names and directories under the current location

	find <location> <settings>

Show files that match the search critera. The criteria can be a literal name or use wildcards *
Wrap non-alphanumeric search criteria with quotes ""

	find . -name "<file name>"

Find files that match the file pattern and pass results to grep for searching file contents

	find <location> -name <file pattern> | xargs grep <search string>

## Example

	find . -name "*.jsp" | xargs grep <search string>

Search the files recursively in location for the search string
To search only the location and not the sub dirs drop the -R flag

	grep -R '<search string>' <location>

Find folders that are at a certain depth with the specified name

	find . -mindepth 1 -maxdepth 1 -type d -name '<search-string>'
