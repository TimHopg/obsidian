---
aliases: Terminal Shortcuts
---
#todo #Shell 

* [[awk]] - text manipulation
* [[alias]]
* [[Manual search 1|apropos]] \<keyword\> - man pages and descriptions with keyword
* [[ar]] - Archive
* [[bash]] - run
* [[bat]] - like [[Cat]] (concatenate) but on steroids
* [[bc]] - basic calculator
* [[Change permissions 1|chmod]] - change mode (permissions)
* [[cmp]] - compares two files byte by byte
* [[cp]] - copy
* [[curl]] - client for URLs
* [[du 1|df]] - disk free
* [[diff]] - displays differences between files
* [[du]] - disk usage
* [[echo]] - echoes text/strings
* [[env]] - set environment and execute command or print environment
* [[find]] - find
* [[free]] - displays free and used memory
* [[fzf]] - fuzzy find
* [[grep]] - search and match text patterns (global regular expression print)
* [[head]] - Cats first ten lines of files. See [[Tail]].
* [[ifconfig]] - displays network configuration (interface config)
* [[less]] - Displays results one page at a time
* [[Symbolic link 1|ln]] - Link (symbolic)
* [[ls]] - list
* [[ps 1|lsof]] - list open files
* [[Manual search|man]] - manuals
* [[mkdir]] - make directory
* [[mv]] - move / rename (`mv ..` - move to parent directory)
* [[ncdu]] - NCurse's disk utility
* [[nm]] - Name mangler. Dumps symbol table from binary file
* [[open]] - open -a application
* [[patch]] - For patching diff files
* [[pwd]] - print working directory
* [[ps]] - process status
* [[rg]] - ripgrep
* [[rm]] - remove ([[rmdir]] - remove directory)
* [[sed]] - Stream editor. Text manipulation tool.
* [[shutdown]] - `shutdown -h now` - `-h` stops hard disks
* [[sort]] - sorts alphabetically (or other)
* [[stat]] - statistics
* [[Sys Calls Lib Calls|strace]] - returns system calls used by a program
* [[su]] - switch user
* [[sudo]] - super user do
* [[tar]] - tarball (compressed files)
* [[tail]] - Cats last ten lines of a file. See [[Head]].
* [[time]] - times
* [[touch]] - creates and modifies timestamps of files
* [[type]] - shows what would be executed if typed (aliases etc.)
* [[ulimit]] - User limits
* [[uname]] - Unix name - prints details about machine and O/S
* [[uniq]] - unique elements only (must be [[sort]]ed first)
* [[wall]] - write all. sends message to all users logged in
* [[who]] - shows who is logged on
* [[wc]] - word count
* [[xev]] - display keycode info etc.

`.` - current directory
`..` - parent directory
`~` - root/home directory
`cd -` - go to previous directory

`Ctrl + C` - user interrupt (cancel)
`Ctrl + D` - end of file
`Ctrl + R` - open command history (search)
`Ctrl + A` - go to start of command line
`Ctrl + E` - go to end of command line
`Ctrl + U` - delete from cursor to start of command line
`Ctrl + W` - delete from cursor to start of word
`Ctrl + X/X` - move between cursor and start of command line (and back)
`clear/Ctrl + K/Ctrl + L` - clear screen
`TAB` - autocomplete

`Ctrl + Y` - paste word that was cut
#### Updating `$PATH`
`export PATH="$PATH:/home/ubuntu/.local/bin"`
Using the `$PATH` variable appends this new path to the end of the existing `PATH` variable.

#### References


_2024-05-13 10:48_