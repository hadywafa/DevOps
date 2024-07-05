# Networking in K8s

## Firewalls and iptables in Linux: A Simple Explanation

### What is a Firewall?

A firewall is a security system that controls the incoming and outgoing network traffic based on predetermined security rules. It acts as a barrier between your computer (or network) and potential threats from the internet.

### What is iptables?

`iptables` is a command-line utility in Linux that allows a system administrator to configure the IP packet filter rules of the Linux kernel firewall, implemented as different Netfilter modules.

### Basic Concepts

1. **Packet**: A packet is a small unit of data that is transmitted over a network.
2. **Chain**: A chain is a set of rules that determine what happens to packets. There are three default chains in iptables:
   - **INPUT**: Deals with incoming packets to your system.
   - **OUTPUT**: Deals with outgoing packets from your system.
   - **FORWARD**: Deals with packets that are routed through your system (not used very often unless you're setting up a router).

3. **Rule**: A rule is a condition that is applied to packets traveling through a chain. Each rule specifies what to do with matching packets (e.g., accept, drop, log).

4. **Target**: A target is the action to take when a rule matches a packet. Common targets include:
   - **ACCEPT**: Allows the packet through.
   - **DROP**: Drops the packet without any response.
   - **REJECT**: Drops the packet but sends an error back to the sender.

### Using iptables

#### Checking Current Rules

To see the current iptables rules, you can use the following command:

```bash
sudo iptables -L
```

#### Basic Commands

- **Adding a Rule**: To add a rule, use the `-A` (append) option. For example, to allow incoming SSH connections on port 22:

  ```bash
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  ```

- **Deleting a Rule**: To delete a rule, use the `-D` option. For example, to remove the rule allowing SSH connections:

  ```bash
  sudo iptables -D INPUT -p tcp --dport 22 -j ACCEPT
  ```

- **Listing Rules with Line Numbers**: To list rules with line numbers, which can be helpful for deleting specific rules:

  ```bash
  sudo iptables -L --line-numbers
  ```

- **Flushing Rules**: To remove all rules in a chain:

  ```bash
  sudo iptables -F
  ```

### Examples

1. **Allowing HTTP and HTTPS Traffic**:

   ```bash
   sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT  # Allow HTTP
   sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT # Allow HTTPS
   ```

2. **Blocking All Incoming Traffic Except for SSH, HTTP, and HTTPS**:

   ```bash
   sudo iptables -P INPUT DROP                            # Default policy: drop all incoming traffic
   sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT     # Allow SSH
   sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT     # Allow HTTP
   sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT    # Allow HTTPS
   sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT  # Allow established connections
   ```

3. **Logging Dropped Packets**:

   ```bash
   sudo iptables -A INPUT -j LOG --log-prefix "iptables denied: " --log-level 7
   sudo iptables -A INPUT -j DROP
   ```

### Summary

- **Firewall**: A security system to control network traffic.
- **iptables**: A tool to configure Linux kernel firewalls.
- **Chains**: INPUT, OUTPUT, FORWARD.
- **Rules**: Conditions applied to packets.
- **Targets**: Actions taken on matching packets (ACCEPT, DROP, REJECT).

This overview should help you get started with basic firewall configuration using iptables in Linux. Feel free to ask if you have more specific questions!
