# Secure-Network-Architecture-

# Assignment Description

You have been recently hired as a security architect by an organization with the following structure and access control policies, and your job is to design a secure network architecture from scratch.

## Organization Structure and Access Control Policies:

A) The organization has three public servers: one public Web Server, one DNS Server, and one Mail Server. They can be accessed by both internal and Internet users.

B) The organization has two departments: Engineering and Accounting.

C) The organization has an internal Web app that runs on port 8080 of an internal Web server. Both departments can access this internal Web server.

D) Both public and internal Web servers access a Database server that stores data. This DB server is only accessible by these two Web servers, and no other source is allowed to connect to it.

E) Users in both departments are allowed to browse the Internet (access web services on port 80 or 443), but no source can establish a connection with the client machines in both departments.

F) Servers are not allowed to make connections to any destination. The only exceptions are the Web servers, which are allowed to connect to the DB server.

G) The accounting department has an application server that runs on port 3030 of a server machine. Only users in the accounting department are allowed to connect to this machine.

H) Machines in our network can ping machines on the Internet, but no machine on the Internet is allowed to ping our machines. Any ingress ICMP message other than ICMP ping replies must be filtered. Any egress ICMP message other than ICMP ping requests must be filtered.

I) No UDP traffic is allowed, both ingress and egress, except for DNS traffic.

J) All packets with invalid addresses (broadcast, private, 0.0.0.0, etc.) must be filtered, both ingress and egress at the perimeter of the network (with Internet).

K) Packets with spoofed source IP addresses must not leave our network.

L) TCP Reset packets must not leave our network.

M) No unnecessary packet or connection must be allowed, ingress or egress (least privilege principle). The fail-safe default principle must be followed.

N) The firewalls are stateful.

## Tasks:

1. **Design the Network:**
    - Include zones for external DMZ, internal DMZ, and separate zones for each department.
    - Consider adding a Trusted Zone (hint: for the DB server).
    - Place firewalls at appropriate places in the architecture (hint: at perimeters).
    - Use examples from the slides on Network Architecture Design.

2. **Define Firewall Rules:**
    - For each firewall and each interface, define the sequence of rules, ending with the default rule.
    - Ensure that firewall rules fully implement security policies (A to N).

## Firewall Rules Conventions:

Use the following conventions in defining your firewall rules for simplicity:

- **Firewall names:** Use meaningful names for your firewalls (e.g., border firewall, internal DMZ firewall, etc.)
  
- **Interface names:** Name each interface of the firewall (preferably call them ingress or egress; note that a firewall may have 2 or more interfaces)

- **Protocol:** ICMP, IP, UDP, TCP, or ANY

- **IP Source/Destination:** E.g., IP(Public Webserver) means IP of the public web server. It could also be ANY to mean any IP address.

- **Port Source/Destination:** E.g., WWW, TELNET, or 80, 23; it can also be ANY.

- **Action:** Permit or Deny
