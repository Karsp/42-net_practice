Hello Recruiter! I've prepared this project brief for you.

---

# NetPractice Project 🚀

Welcome to my **NetPractice** repository, where I tackle the fascinating world of networking! 🌐 This system administration project consists of solving 10 levels of networking challenges, from basic device connections to managing complex local networks with routers and switches. If you're passionate about network infrastructure or just intrigued by how low-level programming can make systems run smoothly, you've come to the right place.

## 📝 Project Overview

In this project, I worked through a series of **10 progressively challenging levels**, each simulating a non-functioning network. My task was to configure the network, ensuring that it operated correctly by adjusting network parameters like IP addresses, subnet masks, and routing tables.

The project was executed in a **training interface** accessed via a web browser. Each level required:
- **Diagnosing** network issues.
- **Modifying configurations** until the network became functional.
- Exporting and saving configurations to the repository for further review.

The final evaluation consists of solving **3 randomly chosen puzzles** from the more complex levels in **under 15 minutes**, followed by an explanation of my approach.

## 💡 Key Skills Gained

### 1. **Networking Fundamentals**
   - Mastery of **TCP/IP addressing**, subnetting, and routing.
   - Practical experience configuring routers and switches in a simulated environment.
   - An understanding of how devices interact in a local network and how to troubleshoot them.

### 2. **System Administration Techniques**
   - Applying networking knowledge to solve real-world-like puzzles that mimic challenges in system administration.
   - Gaining proficiency in managing IP configurations, subnet masks, and routing tables in different network scenarios.

### 3. **Problem-Solving and Time Management**
   - Under time constraints, I’ve learned to **quickly assess network diagrams**, identify issues, and implement the correct configurations.
   - My experience in solving these puzzles under pressure has sharpened my ability to troubleshoot and think on my feet.

## 🌟 Importance of These Skills in Low-Level Programming

In system administration and low-level programming, understanding how networks operate is crucial. Even at the most basic level, networking underpins everything, from server communication to distributed systems. This project helped solidify my foundational knowledge, which is essential for roles requiring system-level troubleshooting and optimizations. I’ve gained a deep understanding of **how systems communicate**, which is key when optimizing or debugging performance issues at a low level.

## 🌱 What's Next?

This project has given me a solid foundation in networking, but there's always more to learn! I'm excited to further explore advanced network protocols, security configurations, and low-level optimizations in future projects.




---



Hello students! These are the notes that helped me with this project.

---

### My Notes

#### Find the network address 
Apply the mask to the IP address through a [bitwise AND](https://en.wikipedia.org/wiki/Bitwise_operation#AND)
- Check if two ips are part of the same network
Apply a bitwise XOR to the IPs address 
Apply the mask to the IP address through a [bitwise AND](https://en.wikipedia.org/wiki/Bitwise_operation#AND)
Look for any 1 in the result, if there is one, they are not part of the same subnet.

#### Special IP-ranges
The following special address-ranges are reserved for Private Networks:
10.0.0.0 – 10.255.255.255
172.16.0.0 – 172.31.255.255
192.168.0.0 – 192.168.255.255

The following address-range is reserved for so called loopback addresses:
127.0.0.0 – 127.255.255.255

* There is some more special ip-ranges, but for this project, you only need to remember those above.*

#### There are 2 different ways of writing the mask:

- "Dot-decimal notation": `255.255.255.0`
- "Class Inter-Domain Routing" or "CIDR": `/24`


The more usable ip-addresses you need in one subnet, the less subnets you will be able to create.<br>
To help you understanding it, I found this table very helpful:


| CIDR | Dot-decimal | Number of IP-addresses<br /> per subnet | Usable IP-addresses <br /> per subnet | Number of subnets |
| :---: | :-----------: | :---: | :---: | :---: |
| /32 | 255.255.255.255 | 1 | 0 | 256 |
| /31 | 255.255.255.254 | 2 | 0 | 128 |
| /30 | 255.255.255.252 | 4 | 2 | 64 |
| /29 | 255.255.255.248 | 8 | 6 | 32 |
| /28 | 255.255.255.240 | 16 | 14 | 16 |
| /27 | 255.255.255.224 | 32 | 30 | 8 |
| /26 | 255.255.255.192 | 64 | 62 | 4 |
| /25 | 255.255.255.128 | 128 | 126 | 2 |
| /24 | 255.255.255.0 | 256 | 254 | 1 |


The number of usable IP-addresses per subnet is lower than the total number of IP's because the first address is reserved as the network-address of the subnet and the last address is reserved as a broadcast-adress.<br>
i.e. for mask `255.255.255.252`:<br>
network: `190.3.2.252`<br>
broadcast: `190.3.2.255`<br>
usable IP's: `190.3.2.253`, `190.3.2.254`

- There are couple of ways to calculate the number of hosts per subnet:

   *- Subtract between the last number on the mask and 255. Add 1 (because it start counting on 0).*

   With mask: 				255.255.255.192

   Total Number of Hosts: 		255 - 192 + 1 (count .0)  = 64

   Number of Usable Hosts: 	TNH - 2 = 62

   Usable Host IP Range for network:		128.248.100.1

| **Network Address** | **Usable Host Range**           | **Broadcast Address**  |
|---------------------|---------------------------------|------------------------|
| 128.248.100.0       | 128.248.100.1 - 128.248.100.62  | 128.248.100.63         |
| 128.248.100.64      | 128.248.100.65 - 128.248.100.126| 128.248.100.127        |
| 128.248.100.128     | 128.248.100.129 - 128.248.100.190| 128.248.100.191       |
| 128.248.100.192     | 128.248.100.193 - 128.248.100.254| 128.248.100.255       |


#### Checks
- Check fixed data first.
- Default (on RT) has to point to next interface ip.
- Always check the defaults for typos.
- Always copy and paste the network address and change the hostname.
- Sometimes RT doesn't allow defaults.
- Internet never work in reverse way if it's a local ip.
- 
#### Useful Resources

- [Conceptos de Redes - COMO](http://es.tldp.org/COMO-INSFLUG/COMOs/conceptos-de-redes-COMO/conceptos-de-redes-COMO-4.html)  
  A comprehensive guide on networking concepts in Spanish.

- [Best Practices for Using Multiple Network Interfaces](https://www.ni.com/en/support/documentation/supplemental/11/best-practices-for-using-multiple-network-interfaces--nics--with.html#section-1150124084)  
  A detailed article on best practices for configuring and using multiple NICs.

- [IP Address to Binary Conversion](https://whatismyipaddress.com/ip-address-to-binary)  
  A useful tool for converting IP addresses to binary format.

- [NetPractice - GitHub Repository](https://github.com/lpaube/NetPractice)  

- [Another NetPractice - GitHub Repository]([https://github.com/lpaube/NetPractice](https://github.com/tblaase/Net_Practice/tree/main))  

- [IP Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html?cclass=any&csubnet=26&cip=128.248.100.1&ctype=ipv4&x=Calculate)  
  An IP subnet calculator to aid in network configuration and subnetting.

  

---
