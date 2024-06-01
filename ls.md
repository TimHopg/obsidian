#Shell 
### List
`-l` - long format
`-g` - omit owner information
`-o` - long format without group information
`-a` - all
`-1` - 1 file per line
`-h` - human readable
`-t` - sort by last modified
`-r` - reverse list order

`*` - executable

`ls -laghor` or `ls -lagho`
### `-l` Columns
1. *File Permissions* Contains 10 characters. The first character denotes the file type and the remaining 9 character represents the file permissions.
2. *Number of links* shows the number of hard links the content file or directory has
3. *Owner* The owner of the file or directory
4. *Group* Group owner of file or directory
5. *Size* Content size, by default in bytes
6. *Date* The last modification date of the file or directory.
7. *Time* The modification time of the file or directory.
8. *Filename/Directory name* The actual name of the file or directory.

Also see:
`colorls`