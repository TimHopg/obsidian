#Shell #Programming 

`file -d - | head -c 42 | tail -c 2 | grep -q '42' && echo "String '42' found at the 42nd byte" || echo "String '42' not found at the 42nd byte"

`file -C -m filename
compiles magic file

`0 string 42\0 42 file

`0` starts at byte 0
`string` - looks for a string
`42\0` - the string 42 followed by null character
`42` - counts 42 bytes in
`file` 