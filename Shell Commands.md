---
aliases: Terminal Shortcuts
---
#todo #Shell 

* [[awk 1]] - text manipulation
* [[alias 1]]
* [[Manual search 1|apropros]] \<keyword\> - man pages and descriptions with keyword
* [[ar 1]] - Archive
* [[bash]] - run
* [[bat 1]] - like [[Cat]] (concatenate) but on steroids
* [[bc 1]] - basic calculator
* [[Change permissions 1|chmod]] - change mode (permissions)
* [[cmp]] - compares two files byte by byte
* [[cp]] - copy
* [[curl]] - client for URLs
* [[du 1|df]] - disk free
* [[diff]] - displays differences between files
* [[du 1]] - disk usage
* [[echo 1]] - echoes text/strings
* [[env]] - set environment and execute command or print environment
* [[find 1]] - find
* [[free 1]] - displays free and used memory
* [[fzf]] - fuzzy find
* [[grep 1]] - search and match text patterns (global regular expression print)
* [[head]] - Cats first ten lines of files. See [[Tail]].
* [[ifconfig 1]] - displays network configuration (interface config)
* [[less]] - Displays results one page at a time
* [[Symbolic link 1|ln]] - Link (symbolic)
* [[ls 1]] - list
* [[ps 1|lsof]] - list open files
* [[Manual search 1|man]] - manuals
* [[mkdir]] - make directory
* [[mv]] - move / rename (`mv ..` - move to parent directory)
* [[ncdu]] - NCurse's disk utility
* [[nm 1]] - Name mangler. Dumps symbol table from binary file
* [[open]] - open -a application
* [[patch 1]] - For patching diff files
* [[pwd]] - print working directory
* [[ps 1]] - process status
* [[rg]] - ripgrep
* [[rm]] - remove ([[rmdir]] - remove directory)
* [[sed]] - Stream editor. Text manipulation tool.
* [[shutdown]] - `shutdown -h now` - `-h` stops hard disks
* [[sort]] - sorts alphabetically (or other)
* [[stat 1]] - statistics
* [[su]] - switch user
* [[sudo]] - super user do
* [[tar 1]] - tarball (compressed files)
* [[tail]] - Cats last ten lines of a file. See [[Head]].
* [[time 1]] - times
* [[touch 1]] - creates and modifies timestamps of files
* [[type]] - shows what would be executed if typed (aliases etc.)
* [[ulimit 1]] - User limits
* [[uname 1]] - Unix name - prints details about machine and O/S
* [[uniq]] - unique elements only (must be [[sort]]ed)
* [[wall]] - write all. sends message to all users logged in
* [[who]] - shows who is logged on
* [[wc 1]] - word count
* [[xev]] - display keycode info etc.

`.` - current directory
`..` - parent directory
`~` - root/home directory
`cd -` - go to previous directory

`Ctrl + C` - user interrupt (cancel)
`Ctrl + D` - end of file
`Ctrl + R` - open command history
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