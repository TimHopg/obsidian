#todo #Networks
_localhost_ on most networks is the address _127.0.0.1_ and allows a computer to communicate with itself. aka the most common IPv4 loopback address
#### NAT
Virtual machine shares the host's IP address but uses a private IP address internally.
Use _localhost_ and [[Port Forwarding]].
`ssh user@localhost -p <port>`
#### Bridged
In bridged mode the VM acts as another device on the network and gets its own IP address from the [[DHCP]] server.
Use the VM's unique IP address.
`ssh user@vm_ip_address`
#### Host Only Networking
VM can only communicate with the host and other VMs on the same host-only network.

Use tools like `ifconfig` and `hostname -I`
#### References


_2024-05-24 11:58_
