# 19MMT_Group1_Tor Network, Dark Web and How To Be Anonymous Online

**Group 04:**

- **Thái Duy Nguyễn**
- **Bạch Minh Khôi**
- **Lâm Trí Đức**
- **Trương Bữu Ý**

## 1. DARK WEB

Internet is a common definition that allows interconnection among computers in the network. Most of the services are provided through websites but not all accessible and viewable. Additionally, it leads to the formation of definitions of **Surface web, Deep web, and Dark web**, which all form a common model of **levels of the Internet**.

**Surface web** is what **can be searched on the Internet**, by search engines such as Google or Bing,...

The next level of the Internet is called the **Deep web**, **covered with several security forms**. For instance, using webmail services such as Gmail can be similar to connecting to the Deep web, or sites that can only be viewed when logged in to Facebook.

To the deepest and final layer - **Dark web**, a minor part within Deep web, are **intentionally hidden websites**. The operators behind those do not want to reveal their identity or allow free access to theirs. Those hidden websites can be connected by several methods but mostly by Tor Browser - a browser that allows users to connect to Tor network. In addition, Tor Network is created for safe and anonymous communications through the Internet.

Sites in Dark web are tailing in .onion instead of .com as domain name standards. Provided in Tor with popular uses:

- People use the name Hidden Wikipedia to describe the web: http://zqktlwiuavvvqqt4ybvgvi7tyo4hjl5xgfuvpdf6otjiycgwqbym2qad.onion/
- Dread (be seen as Reddit of Dark web): http://dreadytofatroptsdj6io7l3xptbet6onoyno2yv7jicoxknyazubrad.onion/
- Facebook (origin Facebook that allows anonymous services): facebookwkhpilnemxj7asaniu7vnjjbiltxjqhye3mhbshg7kx5tfyd.onion

Another sub-model of levels of the Internet is formed up from 8 layers: Surface web, Bergie web, Deep web, Charter web, Marianas web, Level 6, The fog/virus soup, The primarch system. This model has detailed determinations of level definitions but it is trivial.

**Security experts recommend using applications such as VPN, anonymous browsers, ad-blockers, security solutions,... to avoid web trackers. If there is no possibility of all referred methods to be available at once, Tor Browser (or Tor) is a potential choice.**

## 2. TOR

### 2.1. Briefly

**TOR - in short of The Onion Router**, is a free open-source providing **anonymous connection to the Internet**. In addition, it is also used for **accessing the Dark web**, where normal browsers such as Google Chrome, Microsoft Edge,... cannot search for and access into.

Tor network (based on Onion Routing) was developed by the United States Naval Research Laboratory in the 90s, later published in 2004, and became a project supported by the Electronic Frontier Foundation - EFF.

Repository: tor - Tor's source code (torproject.org)
Website: www.torproject.org

Tor is written in C, Python, Rust and available on Windows, Unix-like (Android, Linux, macOS). It uses the AES algorithm to encrypt and TCP protocols to communicate.

### 2.2. How Tor works

![](https://i.imgur.com/tYI4fZo.png)

When using Tor, the browser sends a message through Tor network, which includes **3 layers: Entry guard, Middle relay, Exit relay**. In detail, they are formed from periodically created virtual circuits with an extreme number of nodes. Therefore, the message sent will traverse through these.

The data is **encrypted before sending from Tor client**, and completely **decrypted to raw data when reaching the destination from exit node**. The encryption is not mono, but provided **with a number of layers** wrapping the message. When the encrypted message reaches a node, it provides that node with a key to decrypt for the next hop - in other words, to analyze the next IP address to send the message to.

To conclude from above, a node in the circuit only knows the IP address of the previous node and the next one that the message will be sent to. Therefore, except the entry node knows the source address as well as the exit node that knows the destination address, others cannot determine 2 ends. This helps **prevent any eavesdropping** in the middle relay.

Besides, websites that are based in Tor network can be called **onion services (or hidden services)**. Those are not revealed IP addresses but can be **searched for connection by public keys and introduction points in the Distributed Hash Table** (DHT - which is a part of Tor network helps routing from Tor clients to servers, stores descript of servers).

Every server attempting to become a hidden service in the Tor network has to send packets to some Onion Routers to ask for being its introduction point (arbitrary amount). Since then, Tor clients and servers without knowing of each other still can make connections through these points. Afterwards, the server creates a hidden service descriptor that stores the public key and IP address of introduction points. In the end, it is sent to DHT so that onion routers (even introduction points) have at least a part of information about the hidden service.

To connect to a service in Tor network, a key - onion address is required, which is not public. Therefore, the Tor client will send a request towards Distributed Hash Table (DHT) to request for a full descriptor of relevant service. Then an introduction point is chosen to become a random rendezvous point that temporarily sends a request to connect from client and a response from server. Once accepted, the rendezvous point takes part in the virtual circuit connecting both ends.

For example,

> In short, a hidden service works like this, taken from here:
>
> 1. A hidden service calculates its key pair (private and public key, asymmetric encryption).
> 2. Then the hidden service picks some relays as its introduction points.
> 3. It tells its public key to those introduction points over Tor circuits.
> 4. After that the hidden-service creates a hidden service descriptor, containing its public key and what its introduction points are.
> 5. The hidden service signs the hidden service descriptor with its private key.
> 6. It then uploads the hidden service descriptor to a distributed hash table (DHT).
> 7. Clients learn the .onion address from a hidden service out-of-band. (e.g. public website) (A $hash.onion is a 16 character name derived from the service’s public key.)
> 8. After retrieving the .onion address the client connects to the DHT and asks for that $hash.
> 9. If it exists the client learns about the hidden service’s public key and its introduction points.
> 10. The client picks a relay at random to build a circuit to it, to tell it a one-time secret. The picked relay acts as rendezvous point.
> 11. The client creates a introduce message, containing the address of the rendezvous point and the one-time secret, before encrypting the message with the hidden service’s public key.
> 12. The client sends its message over a Tor circuit to one of the introduction points, demanding it to be forwarded to the hidden service.
> 13. The hidden service decrypts the introduce message with its private key to learn about the rendezvous point and the one-time secret.
> 14. The hidden service creates a rendezvous message, containing the one-time secret and sends it over a circuit to the rendezvous point.
> 15. The rendezvous point tells the client that a connection was established.
> 16. Client and hidden service talk to each other over this rendezvous point. All traffic is end-to-end encrypted and the rendezvous point just relays it back and forth. Note that each of them, client and hidden service, build a circuit to the rendezvous point; at three hops per circuit this makes six hops in total.

(source: https://hackernoon.com/how-does-tor-really-work-5909b9bd232c)

### 2.3. Extend research

#### 2.3.1. About guard nodes

List of guard nodes information in the Tor network is public and updated every minute on websites: dan.me.uk/, torstatus.blutmagie.de/, check.torproject.org/.

#### 2.3.2. About middle nodes

Once performing as a middle node, it never can be an exit node.
Since Tor is an open-source project, the appearance of middle nodes hosted by an individual or organization is allowed and legal.

#### 2.3.3. About bridge nodes

Bridge nodes are unpublic nodes of Tor that their existence is to connect to the Tor network once nodes (that are public and listed) are blocked out by the government firewalls.

### 2.4. Strengths

Tor provides safe and anonymous services that help protect the connections. As none of the nodes within a circuit determine the path of a message.

### 2.5. Weaknesses

Below are some of the obvious cons:

- Because of traversing through numerous nodes in the Tor network, it lengthens browsing time and makes it slow.
- Data between the exit node and destination is not encrypted.
- ISP can determine whether a user is using Tor.
- Sniper attack: an attack DOS towards exit nodes - to full waiting queues of exit nodes by spamming messages between clients and servers. This can cause an out-of-memory in nodes, leading to unavailable services. As a result, the network is affected and a higher rate of targets using attackers’ nodes is exploited. (almost impossible)
- Another weakness is the observation of servers to node addresses, which means that they can be influenced by Internet site operators. For instance, BBC blocks out IP of Tor guards as well as exit nodes; or, Tor clients cannot edit origin Wikipedia when using Tor or any addresses indicated by Tor exit node.

### 2.6. Activities and services statistics

![](https://i.imgur.com/3376HTU.png)

![](https://i.imgur.com/E5SLFB3.png)

(source: Tor (network) - Wikipedia)

It is obvious that most of the prevailing activities on Tor are illegal, and the number of those are increasing every year.

### 2.7. Its maintain despite illegal activities

Tor is still in use or not blocked even though there are a large proportion of illegal activities. There are several reasons:

- For political-military purposes.
- To avoid censorship (of journalists, activists… for e.g The Guardian, The New York…)
- For anonymous purposes to avoid tracking from carriers or third parties, ads…
- There is a large user base (as of 2013, there are more than 4 million users).

## 3. VPN

### 3.1. Briefly

A virtual private network (VPN) extends a private network across a public network and enables users to send and receive data across shared or public networks as if their computing devices were directly connected to the private network. A VPN is created by establishing a virtual point-to-point connection through the use of dedicated circuits or with tunneling protocols over existing networks.
There are 3 categories: Remote access; Site-to-site; Extranet-based site-to-site.

### 3.2. Strengths and Weaknesses

| STRENGTHS                     | WEAKNESSES                                     |
| ----------------------------- | ---------------------------------------------- |
| Allows anonymous web surfing  | Does not guarantee 100% security and anonymity |
| Removes regional restrictions | Not cheap with multiple tools                  |

Keeps high-speed connections
Secures connection via public wi-fi |

## 4. PROXY

### 4.1. Briefly

Proxy servers act as relays between the website you’re visiting and your device. Your traffic goes through a middle-man, a remote machine used to connect you to the host server. The web proxy server hides your original IP address so that the website sees the IP of the proxy. However, proxies only work on the application level, meaning it only reroutes the traffic coming from a single app you set your proxy up with. They also don’t encrypt your traffic.

There are 3 types of proxy servers: HTTP; SOCKS; Transparent proxies.

### 4.2. Strengths and Weaknesses

You can use a proxy to surf the web anonymously because your IP address is hidden. However, you will still be tracked because your connection is not encrypted and it only protects the current browser.

## 5. COMPARISON AMONG VPN, PROXY, AND TOR

All three have one thing in common, which is that they all hide your IP address.

|            | PROXY                                 | VPN                                           | TOR                                                     |
| ---------- | ------------------------------------- | --------------------------------------------- | ------------------------------------------------------- |
| Protection | Only protect browser and app using it | Protects all of the Internet traffic          | Protects all of Internet traffic                        |
| Encryption | No                                    | Yes via secured tunnel provided by VPN server | Multiple layer encryption via nodes                     |
| Speed      | Fast                                  | Faster                                        | Slow due to going through multiple nodes                |
| Benefits   | Browse web anonymously                | Browse the web anonymously                    | Browse the web anonymously                              |
|            | Access to geo-blocked content         | Access to geo-blocked content                 | Access to geo-blocked content                           |
|            |                                       | Protected from hackers and trackers           | Protected from hackers and trackers                     |
|            |                                       |                                               | Gives you total anonymous identity                      |
|            |                                       |                                               | Little additional tools required other than Tor browser |

## REFERENCES

1. [Sự khác biệt giữa Deep Web và Dark Web là gì? - GVN360](https://gvn360.com/cong-nghe/su-khac-biet-giua-deep-web-va-dark-web-la-gi-day-la-cau-tra-loi-danh-cho-ban/?fbclid=IwAR1daAZNdLp8dg-2rfSzWjXwtVIem3y5L7ExHs2oOdjE5nkYWEQx149eQwU)
1. [Tor – Wikipedia tiếng Việt](https://vi.wikipedia.org/wiki/Tor)
1. [Tor (network) - Wikipedia](<https://en.wikipedia.org/wiki/Tor_(network)>)
1. [(4) How does the TOR browser hide my location? - Quora](https://www.quora.com/How-does-the-TOR-browser-hide-my-location)
1. [How does Tor actually work? | HackerNoon](https://hackernoon.com/how-does-tor-really-work-5909b9bd232c)
1. [8 tầng của Internet – Người Đến Từ Bình Dương (nguoidentubinhduong.com)](https://nguoidentubinhduong.com/2020/03/06/8-tang-cua-internet/)
1. [TOR Nodes Explained!. Block it, Track it or Use it. But… | by Raja Srivathsav | Coinmonks | Medium](https://medium.com/coinmonks/tor-nodes-explained-580808c29e2d)
1. https://www.cloudwards.net/vpn-vs-proxy-vs-tor/
1. https://www.security.org/vpn/proxy-vs-vpn/
1. https://www.information-age.com/vpn-considered-better-efficient-proxy-server-123464281/
