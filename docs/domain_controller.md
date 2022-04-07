# **19CNTT_Group3_Domain Controller with Packet filtering, NAT, WAF, DMZ**

- Nguyễn Quốc Bảo
- Trịnh Anh Khoa
- Nguyễn Quang Huy
- Nguyễn Quang Thuận

# **Domain Controller with Packet filtering, NAT, WAF, DMZ**

## **Domain controller**

**What is a domain controller?**

- A domain controller is a type of server that processes requests for authentication from users within a computer domain.
- Domain controllers are most commonly used in Windows Active Directory (AD) domains but are also used with other types of identity management systems.
- Domain controllers duplicate directory service information for their domains, including users, authentication credentials and enterprise security policies.

**What are the main functions of a domain controller?**

- Domain controllers restrict access to domain resources by authenticating user identity through login credentials, and by preventing unauthorized access to those resources.
- Domain controllers apply security policies to requests for access to domain resources.
- For example, in a Windows AD domain, the domain controller draws authentication information for user accounts from AD.

**Why is a domain controller important?**

- Domain controllers control all domain access, blocking unauthorized access to domain networks while allowing users access to all authorized directory services.
- The domain controller mediates all access to the network, so it is important to protect it with additional security mechanisms such as:
  - Firewalls
  - Secured and isolated networks
  - Security protocols and encryption to protect stored data and data in flight
  - Restricted use of insecure protocols, such as remote desktop protocol, on controllers
  - Deployment in a physically restricted location for security
  - Expedited patch and configuration management
  - Blocking internet access for domain controllers
- Domain controllers control all access to computing resources in an organization, so they must be designed to resist attacks and to continue to function under adverse conditions.

**How many ways to protect domain controllers?**
There are 4 ways:

- Domain controllers with packet filtering
- Domain controllers with NAT
- Domain controllers with WAF
- Domain controllers with DMZ

## Domain controller with Packet filtering

**What is Packet filtering?**

Packet filtering controls (allows or drops) packet or data transfer based on the following standards:

- The address the packet is coming from.
- The address the packet is going to.
- The application protocols or rules set to transfer the data.

**The execution of Packet filtering?**

The packet filtering firewall checks access control lists (ACLs) to separate packets depending upon the upper-layer protocol ID, source and destination port numbers, source and destination IP addresses, and packet transmission route.

**Type of Packet filtering?**

- **Static packet filtering firewall**: In this type of firewall rules are established manually, and the connection between the internal and external networks left open or closed at all times until changed manually.

- **Dynamic packet filtering firewall**: This type of firewall is a more intelligent way of filtering as rules may be changed dynamically depending upon the conditions, and ports are open only for a specific time otherwise remains closed.

- **Stateful packet filtering firewall**: It uses a presettable for maintaining a secure connection, and packets pass through in a sequence as approved by the filter rules.

**The example of Packet filtering:**

If you set rules denying access to port 80 to outsiders, you would block off all outside access to the HTTP server as most HTTP servers run on port 80. Alternatively, you can set packet filtering firewall rules permitting packets designated for your mail or web server and rejecting all other packets.

## Domain controller with NAT

**What is NAT(Network Address Translation)?**

Network Address Translation (NAT) is a process that enables one, unique IP address to represent an entire group of computers. In network address translation, a network device, often a router or NAT firewall, assigns a computer or computers inside a private network a public address.

**The execution of NAT?**

In this way, network address translation allows the single device to act as an intermediary or agent between the local, private network and the public network that is the internet. NAT’s main purpose is to conserve the number of public IP addresses in use, for both security and economic goals.

**Type of NAT?**

- **Static network address translation SNAT:** SNAT maps unregistered IP addresses using 1 to 1 network address translation to match up with registered IP addresses. It is particularly useful when a device needs to be accessible from outside the network.

- **Dynamic network address translation DNAT:** In this type of NAT, multiple private IP addresses are mapped to a pool of public IP addresses. It is used when we know the number of fixed users who want to access the Internet at a given point in time.

- **Port Address Translation(PAT):** This is also known as NAT overload. In this, many local (private) IP addresses can be translated to a single public IP address. Port numbers are used to distinguish the traffic, i.e., which traffic belongs to which IP address. This is most frequently used as it is cost-effective as thousands of users can be connected to the Internet by using only one real global (public) IP address.

**The example of NAT?**

An inside host may want to communicate with a destination network address translation web server address in the outside world. For further communication, it will send a data packet to the network’s NAT gateway router.

The NAT gateway router determines whether the packet meets the condition for translation by learning the source IP address of the packet and looking it up in the table. It can locate authenticated hosts for the internal network translation purposes on its access control list (ACL), and then complete the translation, producing an inside global IP address from the inside local IP address.

Finally, the NAT gateway router will route the packet to the destination after saving the translation in the NAT table. The packet reverts to the global IP address of the router when the internet’s web server reverts to the request. Referring back to the NAT table, the router can determine which translated IP address corresponds to which global address, translate it to the inside local address, and deliver the data packet to the host at their IP address. The data packet is discarded if no match is found.

## Domain controller with WAF

**What is a Web Application Firewall (WAF)?**

A WAF or web application firewall helps protect web applications by filtering and monitoring HTTP traffic between a web application and the Internet. It typically protects web applications from attacks such as cross-site forgery, cross-site-scripting (XSS), file inclusion, and SQL injection, among others. A WAF is a protocol layer 7 defense (in the OSI model), and is not designed to defend against all types of attacks. This method of attack mitigation is usually part of a suite of tools which together create a holistic defense against a range of attack vectors.

By deploying a WAF in front of a web application, a shield is placed between the web application and the Internet. While a proxy server protects a client machine’s identity by using an intermediary, a WAF is a type of reverse-proxy, protecting the server from exposure by having clients pass through the WAF before reaching the server.

A WAF operates through a set of rules often called policies. These policies aim to protect against vulnerabilities in the application by filtering out malicious traffic. The value of a WAF comes in part from the speed and ease with which policy modification can be implemented, allowing for faster response to varying attack vectors; during a DDoS attack, rate limiting can be quickly implemented by modifying WAF policies.

**What is the difference between blocklist and allowlist WAFs?**

A WAF that operates based on a blocklist (negative security model) protects against known attacks. Think of a blocklist WAF as a club bouncer instructed to deny admittance to guests who don’t meet the dress code. Conversely, a WAF based on an allowlist (positive security model) only admits traffic that has been pre-approved. This is like the bouncer at an exclusive party, he or she only admits people who are on the list. Both blocklists and allowlists have their advantages and drawbacks, which is why many WAFs offer a hybrid security model, which implements both.

**What are network-based, host-based, and cloud-based WAFs?**

A WAF can be implemented one of three different ways, each with its own benefits and shortcomings:

- A network-based WAF is generally hardware-based. Since they are installed locally they minimize latency, but network-based WAFs are the most expensive option and also require the storage and maintenance of physical equipment.
- A host-based WAF may be fully integrated into an application’s software. This solution is less expensive than a network-based WAF and offers more customizability. The downside of a host-based WAF is the consumption of local server resources, implementation complexity, and maintenance costs. These components typically require engineering time, and may be costly.
- Cloud-based WAFs offer an affordable option that is very easy to implement; they usually offer a turnkey installation that is as simple as a change in DNS to redirect traffic. Cloud-based WAFs also have a minimal upfront cost, as users pay monthly or annually for security as a service. Cloud-based WAFs can also offer a solution that is consistently updated to protect against the newest threats without any additional work or cost on the user’s end. The drawback of a cloud-based WAF is that users hand over the responsibility to a third party, therefore some features of the WAF may be a black box to them.

## Domain controller with DMZ

**What is a DMZ in networking?**

In computer networks, a DMZ, or demilitarized zone, is a physical or logical subnet that separates a local area network (LAN) from other untrusted networks -- usually, the public internet. DMZs are also known as perimeter networks or screened subnetworks.

Any service provided to users on the public internet should be placed in the DMZ network. External-facing servers, resources and services are usually located there. Some of the most common of these services include web, email, domain name system, File Transfer Protocol and proxy servers.

Servers and resources in the DMZ are accessible from the internet, but the rest of the internal LAN remains unreachable. This approach provides an additional layer of security to the LAN as it restricts a hacker's ability to directly access internal servers and data from the internet.

Hackers and cybercriminals can reach the systems running services on DMZ servers. Those servers must be hardened to withstand constant attack. The term DMZ comes from the geographic buffer zone that was set up between North Korea and South Korea at the end of the Korean War.

**How does a DMZ work?**

DMZs function as a buffer zone between the public internet and the private network. The DMZ subnet is deployed between two firewalls. All inbound network packets are then screened using a firewall or other security appliance before they arrive at the servers hosted in the DMZ.

![](https://i.imgur.com/7Pg4CNk.png)

If better-prepared threat actors pass through the first firewall, they must then gain unauthorized access to the services in the DMZ before they can do any damage. Those systems are likely to be hardened against such attacks.

Finally, assuming well-resourced threat actors take over a system hosted in the DMZ, they must still break through the internal firewall before they can reach sensitive enterprise resources. Determined attackers can breach even the most secure DMZ architecture. However, a DMZ under attack will set off alarms, giving security professionals enough warning to avert a full breach of their organization.

**What are the benefits of using a DMZ?**

The primary benefit of a DMZ is that it offers users from the public internet access to certain secure services, while maintaining a buffer between those users and the private internal network. There are several security benefits from this buffer, including the following:

- Access control. A DMZ network provides access control to services outside an organization's network perimeters that are accessed from the internet. It simultaneously introduces a level of network segmentation that increases the number of obstacles a user must bypass before gaining access to an organization's private network. In some cases, a DMZ includes a proxy server, which centralizes the flow of internal -- usually, employee -- internet traffic and makes recording and monitoring that traffic simpler.
- Network reconnaissance prevention. A DMZ also prevents an attacker from being able to scope out potential targets within the network. Even if a system within the DMZ is compromised, the internal firewall still protects the private network, separating it from the DMZ. This setup makes external active reconnaissance more difficult. Although the servers in the DMZ are publicly exposed, they are backed by another layer of protection. The public face of the DMZ keeps attackers from seeing the contents of the internal private network. If attackers do manage to compromise the servers within the DMZ, they are still isolated from the private network by the DMZ's internal barrier.
- Protection against Internet Protocol (IP) spoofing. In some cases, attackers attempt to bypass access control restrictions by spoofing an authorized IP address to impersonate another device on the network. A DMZ can stall potential IP spoofers, while another service on the network verifies the IP address's legitimacy by testing whether it is reachable.

**What DMZs are used for**

DMZ networks have been an important part of enterprise network security for almost as long as firewalls have been in use. They are deployed for similar reasons: to protect sensitive organizational systems and resources. DMZ networks are often used for the following:

- isolate and keep potential target systems separate from internal networks;
- reduce and control access to those systems by external users; and
- host corporate resources to make some of them available to authorized external users.

More recently, enterprises have opted to use virtual machines or containers to isolate parts of the network or specific applications from the rest of the corporate environment. Cloud technologies have largely removed the need for many organizations to have in-house web servers. Many of the external-facing infrastructure once located in the enterprise DMZ has migrated to the cloud, such as software-as-a-service apps.

## Reference

- [What is domain controller?](https://www.techtarget.com/searchwindowsserver/definition/domain-controller)
- [What is DMZ?](https://www.barracuda.com/glossary/dmz-network)
- [What is NAT?](<https://avinetworks.com/glossary/network-address-translation/#:~:text=Network%20Address%20Translation%20(NAT)%20is,private%20network%20a%20public%20address.>)
- [What is WAF?](https://cloud.orange-business.com/en/web-application-firewall-waf/)
- [What is Packet filtering](https://www.jigsawacademy.com/blogs/cyber-security/packet-filtering-firewall/)
- [WAF domain controller](https://www.cloudflare.com/learning/ddos/glossary/web-application-firewall-waf/)
- [What is a DMZ in Networking?](https://www.techtarget.com/searchsecurity/definition/DMZ)
