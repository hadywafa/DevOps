# Questions

## Networking Fundamentals Questions

### Advanced Questions

#### 1. For each step for example Router to Internet when router modify the packet and Removed for internet transmission. Ethernet Header and then it comes back to router again how the router knows the removed data ? is he store it or what ?

- When the router modifies a packet and removes the Ethernet header for internet transmission, it does not need to store the removed data (like the Ethernet header) because the necessary information to reconstruct the packet when it returns is already contained within the IP and NAT tables.

#### 2. i need to go deep dive in NAT Table to understand how router public ip can know the data is for ip of pc1 not for ip of pc2 ?

- The NAT table is used to map the private IP addresses of devices on the local network to the public IP address of the router. When a packet is received by the router, it checks the NAT table to determine which device on the local network the packet is intended for. The router then forwards the packet to the appropriate device based on the NAT table entry.
