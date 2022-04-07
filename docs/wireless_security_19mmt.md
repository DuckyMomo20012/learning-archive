# 19MMT_Group2_Wireless Security: WEP, WPA, WPA2, RSN

## GROUP 2

- **Trần Thiên Phúc**
- **Trần Anh Quân**
- **Triệu Nguyễn Minh Huy**
- **Tăng Thanh Quang**

## INTRODUCTION

With the strong development of mobile computing devices such as laptops, mobile phones and some other devices, the need for wireless network connection is almost inevitable. Wireless networks bring convenience to users because of their high flexibility, regardless of the network connection, but they can still access the network at any location as long as they have an access point.
However, in the wireless network system, there are great risks from security, vulnerabilities that can allow attackers to break into the system to steal information or perform destructive actions. Therefore, my group decided to choose the topic of **Wireless Security**: including **WEP, WPA, WPA2, RSN** to learn, research and apply this security solution in a real environment.

## **1. WEP**

### **1.1. History**

Introduced in 1997, **Wired Equivalent Privacy** (WEP) was a security algorithm for 802.11 wireless networks. It was the first attempt at wireless protection. The aim was to add security to wireless networks by encrypting data. If wireless data were intercepted, it would be unrecognizable to the interceptors since it had been encrypted.

### **1.2. How it works?**

**1.2.1. Encryption**
First WEP performs a 32-bit cyclic redundancy check (CRC) checksum operation on the message. WEP calls this the integrity check value and concatenates it to the end of the plaintext message. Next, we take the secret key and concatenate it to the end of the initialization vector (IV). Plug this IV + secret key combination into the RC4 Pseudo-Random Number Generator (PRNG) and it will output the key stream sequence. The key stream is merely a series of 0s and 1s, equal in length to the plain text message plus CRC combination. Finally, we perform a XOR operation between the plain text message plus CRC combination and the key stream. The result is the cipher text. The IV (unencrypted) is prepended to the cipher text and included as part of the transmitted data.

![](https://i.imgur.com/elZgSrw.png)

**1.2.2. Decryption**
Decryption is the same process as encryption, but in reverse. We take the IV (which is sent in clear text) and prepend it to the secret key and plug that into the RC4 cipher to regenerate the key stream. Next, we XOR the key stream with the cipher text, which will give us the plain text value. Finally, we reperform the CRC-32 checksum on the message and ensure that it matches the integrity check value in our decrypted plain text. If the checksums do not match, the packet is assumed to have been tampered with and discarded.
![](https://i.imgur.com/swqJHkw.png)

**1.2.3. Authentication**
Two methods of authentication can be used with WEP: Open System authentication and Shared Key authentication.
In Open System authentication, the WLAN client does not provide its credentials to the Access Point during authentication. Any client can authenticate with the Access Point and then attempt to associate. In effect, no authentication occurs. Subsequently, WEP keys can be used for encrypting data frames. At this point, the client must have the correct keys.
In Shared Key authentication, the WEP key is used for authentication in a four-step challenge-response handshake:

1. The client sends an authentication request to the Access Point.
2. The Access Point replies with a clear-text challenge.
3. The client encrypts the challenge-text using the configured WEP key and sends it back in another authentication request.
4. The Access Point decrypts the response. If this matches the challenge text, the Access Point sends back a positive reply.
   ![](https://i.imgur.com/yFqrJIz.png)

### **1.3. Advantage and disadvantage of WEP**

**_Advantage:_**

- All wireless devices support basic WEP encryption. This can be useful when trying to use older devices that need wireless connectivity.
- Self-synchronization
- Computational and resource optimization

**_Disadvantage:_**

- **IV Collision**: When an IV is reused, we call this a collision. When a collision occurs, the combination of the shared secret and the repeated IV results in a key stream that has been used before. Since the IV is sent in clear text, an attacker who keeps track of all the traffic can identify when collisions occur. A number of attacks become possible upon the discovery of IV collisions.
- **Key Management Problems**: WEP uses a symmetric key encryption mechanism, meaning that the same shared secret (key) is used for both encryption and decryption. The key must be shared between the sender and receiver. Each user must know the key and keep it a secret. What happens if one person leaves the company or has a laptop stolen? A new key must be given to every single user and re-entered in her client configuration. Also, if an attacker compromises the key from one session, the same key can be used to decrypt any other session, because everybody is using the same key.
- **Message Injection**: Does not guarantee privacy and integrity. If the attackers know the keystream, they can decrypt and change the data.

## 2. WPA

### 2.1. Introduction

No matter how long or secure Wi-Fi's password is, being easily cracked is a weakness for WEP encryption keys. The IEEE has been hard at work in the 802.11i Task Group to develop a replacement for WEP. Originally called WEP2, the name was changed to WPA, which is, as mentioned earlier, short for **Wi-Fi Protected Access**.

According to rumors inside the Wi-Fi Alliance, the running joke was:

> _“After the ship sinks, you don't name the next one Titanic 2”_
>
> On October 31, 2002, the Wi-Fi Alliance announced WPA, in essence a compromise solution because parts of the 802.11i specification were ready (such as 802.1x and Temporal Key Integrity Protocol [TKIP]) and other parts were not (such as Advanced Encryption Standard [AES] and secure deauthentication/disassociation).

### 2.2. WPA to the Rescue!

WPA makes major improvements to encryption, authentication, integrity, and key management, and adds an element that defines network security. WPA introduces a new encryption technology, TKIP (Temporal Key Integrity Protocol), with integrity check MIC (Message Integrity Protocol) to replace WEP and provide data reliability and network data integrity.

TKIP addresses these weaknesses:

- **Replay attacks**: IVs can be used out of order.
- **Forgery attacks**: ICV using 32-bit CRC is linear and can be manipulated.
- **Key collision attacks**: IV collisions.
- **Weak key attacks**: RC4 stream cipher is vulnerable to FMS attacks (AirSnort, WEPCrack, dweputils, etc.).

### 2.3. TKIP

TKIP is designed to address the vulnerabilities of WEP, without the need to replace old hardware. For this reason, TKIP maintains the basic mechanisms of WEP: IV, RC4 algorithm, ICV. However, the enhanced RC4 encryption scheme uses one key per 128-bit packet and a longer 48-bit IV. Unlike WEP, TKIP encrypts each data packet sent with its own unique encryption key. These keys are automatically generated, providing greater security against intruders based on predicting static keys in WEP. In addition, WPA includes a MIC (Micheal) message integrity check to prevent message corruption.

TKIP has three main elements to enhance encryption:

- A per-packet key mixing function
- An improved Message Integrity Code (MIC) function named Michael
- An enhanced IV including sequencing rules

#### 2.3.1. TKIP in Detail

The client starts off with two keys: a 128-bit encryption key and a 64-bit data integrity key obtained securely during the 802.1x negotiation. The encryption key is called the Temporal Key (TK). The integrity key is called the Message Integrity Code (MIC) key. First, the sender's MAC address is XORed with the TK to create the Phase 1 key (sometimes called the intermediate key). The Phase 1 key is then mixed with a sequence number to produce the Phase 2, per-packet key. The output of Phase 2 is handed over to the WEP engine as a standard 128-bit WEP key (IV + shared secret). The rest of the process occurs as a normal WEP transaction. The difference is that we no longer have all the clients using the same WEP key (because of Phase 1) and we no longer have a correlation between the IV (in this case, the sequence number) and the per-packet key (because of Phase 2). Let's review each part of TKIP in a bit more detail.

![](https://i.imgur.com/xwSGSLX.gif)
_TKIP Encryption_

#### 2.3.2. Per-Packet Key Mixing

The problem with the original WEP design was that the IV was prepended to the secret key and simply plugged into RC4. Under TKIP, Phase 1 ensures that every client has a different intermediate key. Then, Phase 2 further mixes the key with a sequence number before it is finally plugged into RC4. As you can see, this process is much more involved than simply pre-pending the IV to the secret key and handling it over to RC4. TKIP's use of a per-packet key fixes WEP's improper RC4 implementation.

![](https://i.imgur.com/bYgO8NU.gif)
_Per-packet key mixing function_

### 2.3.3. \***\*Michael: TKIP's MIC Function\*\***

MIC is a cryptographic message integrity algorithm to prevent any modification to a packet. It uses a hash function instead of a linear checksum, which solves the vulnerabilities in ICV. The hashing algorithm, called Michael, is designed to ensure that the contents of a data packet are sent only by legitimate clients and that there is no data modification during the transmission of the packet. Michael generates a 64-bit hash, which is then compared to both senders/receivers. The MIC value must match the data to be accepted. Otherwise, the packet is ignored because it is assumed that packet integrity has been compromised, unless countermeasures are taken. In this case, all packet transmissions and receptions are disabled and all clients must authenticate and new combinations are stopped within 60 seconds.

### 2.3.4. \***\*A Larger IV Space\*\***

The 24-bit IV was replaced by a 48-bit TKIP Sequence Counter (TKIP Sequence Counter) to solve the IV reuse problems in WEP. The TSC is a 48-bit counter that starts with 0 and increments by 1 for each packet, providing the receiver with a means of maintaining a trail of the highest value for each MAC address to ensure that the packet arrives on time. Chain. A packet is dropped if the TSC value is less than or equal to the packet just received to prevent re-use attacks because the TSC function allows a key sequence to never be reused with the key. This protocol prevents an attacker from performing a reuse attack, known as known plaintext attacks and dictionary-based attacks, after recovering a key stream.

### 2.4. Key Management in WPA

The PTK is generated from the PMK using a 4-way handshake and all information used to calculate its value is transmitted in plaintext. So the strength of the PTK is based on the values of the PMK, so that the PSK is effective by using strong passwords. As pointed out by Robert Moskiwitz, the second message of the 4-way handshake must be resistant to dictionary and brute force attacks. To perform this attack the attacker must capture the messages during the 4-way handshake by either passively monitoring the wireless network or using an unauthenticated attack.

![](https://i.imgur.com/SxPklR8.png)
_4-way handshake_

**Attack steps:**

- Step 1: Enable observation mode.
- Step 2: Find the network and the clients connected to it.
- Step 3: Perform a dictionary attack.

### 2.5. Summary

WPA was an interim measure, which took some pieces of 802.11i that were ready for prime time, and left other pieces for the 802.11i working group to continue developing. The remaining parts of 802.11i (primarily the AES cipher and ad-hoc security) were not released until more than a year later. The best part of WPA was that it was backwards compatible with existing hardware and could be deployed as a simple software/firmware upgrade. When you think of WPA, you should immediately associate it with **TKIP and 802.1x**.

## 3. WPA2

### 3.1. Introduction

Wi-Fi Alliance introduced WPA and is considered to eliminate all WEP attack vulnerabilities, but users still do not really trust WPA because it still has limitations.

To overcome this shortcoming of WPA, a long-term solution is to quickly develop a better security standard, more closely following the IEEE 802.11i standard, which is the WPA2 (Wi-Fi Protected Access 2) standard, which is supported by Wi-Fi Alliance officially replaced WPA in 2006.

![](https://i.imgur.com/fd09d82.png)

### 3.2. How it works?

Like WPA, WPA2 is designed for security on all 802.11b, 802.11a, 802.11g and 802.11n versions supporting multi-channel, multi-mode and allowing implementation over IEEE 802.11X/EAP or PSK. It increases data security, controls network access, and overcomes all the weaknesses of WEP and WPA.

### 3.3. Compare with WPA

The biggest difference between WPA and WPA2 is that while WPA uses TKIP for encryption and Michael's algorithm for ensuring the integrity of each data packet, WPA2 uses standard encryption AES (Advanced Encryption Standard) to ensure confidentiality, data integrity and use CCMP (Counter Mode Cipher Block Chaining Message Authentication Code Protocol) for data encryption and packet integrity checking.

### 3.4. Disadvantages of WPA2

However, the WPA2 security protocol can still be compromised. Bad guys can take advantage of this loophole to steal any information that is passed back and forth between the device (phone, computer,...) and the Wi-Fi access point.

WPA2 requires hackers to have access to a Wi-Fi network first before they can hack into other clients on the same network. Therefore, WPA2 can be considered as a secure standard for home Wi-Fi networks, and with the above flaw, hackers can only penetrate Wi-Fi networks of businesses (with a lot of connected devices).
![](https://i.imgur.com/gZallGO.png)
Hackers only need to be within range of the device to be able to use the **Key Reinstallation Attack** (KRACK) method to penetrate the connection between the device and the hotspot. Essentially, KRACK undermines an important aspect of WPA2's 4-way handshake, allowing hackers to intercept and manipulate the generation of new encryption keys during a secure connection. This approach allows an attacker to read any information that is supposedly encrypted.

## 4. RSN

### 4.1. 802.11i Foundation

IEEE created a group called Standards Association - SA. IEEE-SA has responsible for creating IEEE 802 standards. These are standards for local area networks and metropolitan networks. EEE 802 is again divided into working groups, where each group is divided into different standards for each area and “.11” is the working group that creates standards for wireless networks.
![](https://i.imgur.com/cKCwZIl.png)

IEEE 802.11 is a long and complex standard . Regardless of the positive effects of the entire standard, there are sides that are unclear and not fully defined. Some features are still optional. To avoid this problem, a “WiFi” alliance was established. To be “WiFi” certified, a manufacturer must submit their product for testing. The WiFi Alliance offers a test plan based on IEEE 802.11. Some IEEE 802.11 features are not required in the certification, but conversely some features are added. As such, WiFi includes a subset of the 802.11 standard with some extensions.

![](https://i.imgur.com/n2BRDoq.png)

Because the definition of WiFi came when IEEE 802.11 was completed. However, the WiFi production manufacturers have decided that safety is very important forcing users to replace the use of WEP with a more secure algorithm in the fastest time possible. Furthermore, they also concluded that customers cannot throw away all their old WiFi devices to switch to RSN, they just want to update the product through software. To do this, Task Group I developed a secure solution that builds on the existing functionality of the old product. This thing create TKIP temporal keys integration protocol, and it is allowed as an optional mode in the RSN.

The development of TKIP was a big help to enable updating of existing systems, but they couldn't wait until the standards were accepted. So the WiFi alliance follow a new safety approach based on the “draft RSN” (draft RSN) but specifying the TKIP. This subset of RNs is called WiFi Protected Access (WPA).

### 4.2. Robust Security Network definition - RSN

RSN is an implementation of 802.11i enough to be interoperable with WPA2. 802.11i uses AES block cipher, and WEP and WAP use RC4 stream cipher.

Unlike WEP, RSN has many keys in a key architecture and most of them are not known until the authentication process ends. These keys are generated after the authentication process and so they are called temporal keys or session keys. These keys are always updated in real time and they will be deleted when the "safety situation".

Authentication is based on some confidential information that cannot be done automatically. An authentication key must be generated by a trusted source and associated with a user in such a way that it cannot be easily copied or stolen. Such a key is called a master key.

RSNs have two types of keys: a permanent key (primary key) for proof of identity and a some of temporal keys used in sessions.

### 4.3. RSN security layers

There are three security layers of RSN :

- Wireless LAN layer.
- Access control layer.
- Authentication layer.

Wireless LAN layer corresponds to the "Data link" layer in the OSI model, which is responsible for encrypting and decrypting data when a "safety situation".

Access control layer is the middle management layer, managing the security context ("safe situation"). It must stop regardless of when data is sent and coming from an "enemy". Enemy here is understood as someone who does not have an existing security context set up (does not have "safe situation"). It take part in the generation of keys.

Authentication layer is the top layer. This layer generates policy decisions and proofs of whether the identity is accepted or rejected. The authentication layer allows anyone who wants to access the LAN and authorizes the access control layer once it accepts someone to connect to the LAN.

![](https://i.imgur.com/NiKUAed.png)

## 5. SUMMARY

Security remains a major concern in WLANs globally. While wireless networks offer convenience and flexibility, they also increase network vulnerability. Security threats like unauthorized access, denial of service attacks, IP and MAC spoofing, session hijacking, and eavesdropping can all be problems for WLANs. To deal with these threats, many standard authentication and encryption techniques are combined with other access control mechanisms.

Here are a few ways to protect your Wi-Fi:

- Changing the default password and SSID.
- Make sure your password is at least 10 characters long and contains non-alphanumeric characters.
- Enable the router’s firewall.
- Enable MAC address filtering.
- Disable remote administration.

## 6. REFERENCES

1. Barken, L. (2004). How secure is your wireless network?: Safeguarding your wi-fi-lan. Prentice Hall PTR.
2. Nguyễn Hiếu Minh (FIT - MTA). Slide: An ninh mạng không dây (IEEE 802.11)
3. Nguyễn Hoàng Việt. (6.2015). Giải pháp đảm bảo an toàn mạng không dây theo chuẩn 802.11I
4. Wiki IEEE 802.11i-2004
5. An Nhiên. (10.2017). WPA2 là gì? WPA2 đã bị hack như thế nào?
6. Wired Equivalent Privacy - Wikipedia
7. Advantages and Disadvantages of WEP WPA Network Security - Bright Hub
8. Ad-hoc network wiki
