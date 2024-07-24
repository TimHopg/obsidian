#todo 

`ifconfig | grep ether | cut -d " " -f 2`

To print just MAC addresses:
`ifconfig | awk '/ether/{print $2}'
* takes the output of ifconfig pipes it to awk (a text processing tool)
* AWK prints the 2nd field wherever ether appears. ether = mac address and the second field is where the mac address resides
#### References
[[awk 1]]