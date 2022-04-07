# 19CNTT_Group1_Wireless Security: WEP, WPA, WPA2, RSN

## **INTRODUCTION**

Nowadays, wireless networking has become very popular. It is present everywhere, from private homes, companies, to public areas. Therefore, hackers always want to find ways to attack wireless networks to steal data and user information.
So, my group decided to learn about wireless networks and its security protocols.
The report consists of two main parts:
• Introduction to wireless network
• Introduction to wireless network security protocols
With limited knowledge, the report may contain errors. We hope you have suggestions so that my group can improve.

## **TABLE OF CONTENTS**

- WIRELESS NETWORK
- WIRELESS SECURITY
  - WEP
  - WPA
  - WPA2
  - RSN
- REFERENCES

## **I. WIRELESS NETWORK**

A wireless network is a computer network that uses wireless data connections between network nodes. Wireless networks are preferred by households, businesses or medium and large businesses that need to connect to the internet but not through too many conversion cables. Wireless networks are managed by the carriers' radio communications systems. These systems are often located centrally or sporadically in the carrier's storage facilities. The commonly used network topology is the OSI topology.
A wireless uses radio waves as a transmission wave or physical layer.
Typical examples of wireless networks are Wi-Fi networks, 3G networks, mobile phone networks, Bluetooth networks, wireless local area networks (WLANs), …

## **II. WIRELESS SECURITY**

Wireless security is the prevention of unauthorized access or damage to computers or data using wireless networks, which include Wi-Fi networks. Wireless security ensures the confidentiality, integrity, or availability of the network. The most common type is Wi-Fi security, which includes Wired Equivalent Privacy (WEP), Wi-Fi Protected Access (WPA) and WPA2…
**THIS REPORT WILL INTRODUCE WEP, WPA, WPA2**

## **A. WEP**

### **1. Introduction**

WEP is part of the IEEE 802.11 standard, which uses a symmetric encryption algorithm RC4 for security and a CRC-32 checksum for information integrity.
WEP key at the client is used to certificate with Access Point, encrypts and decrypts data.
Standard WEP: 64-bit standard (WEP-40, key as 40-bit, 24-bit as IV - Initialization Vector), 128-bit extended standard WEP (WEP-104). In addition, some manufacturers also support 256-WEP in some products.

### **2. Authentication**

Before sending data, client must be verified. With WEP, there are 2 ways to authenticate:
**i. Open System Authentication:**
• The client does not need to provide its credentials to the Access Point during the authentication process. Thus, any client can authenticate itself and connect to the Access Point without the need for a WEP key. WEP is stopped to encrypt data only after authentication and successful connection to the Access Point.
• Open System Authentication process:
Client sends a request for authenticating includes MAC address in Open System Authentication way.
Access Point responds a message whether the authentication is successful or not.
![](https://i.imgur.com/vyPqUEa.png)

**ii. Shared Key Authentication:**
Access Point checks whether the client is valid or not through a predefined key between the client and the Access Point (Shared key). WEP is used for authentication.
4 steps to authenticate:
• The client sends a request for authentication to Access point.
• Access Point responds a nonce which has a random bit string to challenge the client.
• The client encrypts nonce using WEP and a preconfigured WEP key, sending another authentication request including the encrypted nonce.
• Access Point decodes the nonce, compares it with the nonce it sent, if it is, it will reply with a valid response and vice versa. Once authenticated and connected to the Access Point, WEP is used to encrypt the data.
![](https://i.imgur.com/ZF0lGMU.png)

### **3. Advantages**

• Fast proceed.

### **4. Disadvantages**

• Still can't resist reused key attack even though IV is used. Because IV has only 24 bits, when the packet volume is large (about 5000 packets), the IV is reassembled.
• There is no automatic key change mechanism.
• It is impossible to avoid "weak IV", "weak IV" are IVs that can reveal the content of the message.
• DoS (Denial of service) attack is not prevented.
• It is not possible to change the transmitted information even though the checksum is used.

## **B. WPA**

### **1. Introduction**

WPA (Wi-Fi Protected Access) is a Wi-Fi security standard and protocol developed by the Wi-Fi Alliance in 2003. WPA provide more sophisticated data encryption and better user authentication than WEP.
WPA uses Temporal Key Integration Protocol for encryption. TKPI create a 128 bits key for each packet. WPA also uses the Michael protocol to check the integrity of the packet, to make sure they are not caught and changed by anyone.

### **2. Authentication**

i. Open System Authentication: Same as WEP
ii. 802.1X:
• WPA-EAP for enterprise, uses an 802.1x authentication via Radius (Remote Authentication Dial-in User Service) Server. Server will authenticate and provide key for each session.
• WPA-PSK (Pre-Shared Key) for personal, uses Simultaneous Authentication of Equals (SAE) to create a secure handshake. A 256-bit authentication key is used for all wireless devices connected.

### **3. Advantages**

• No hardware needed
• Ensures authentication between Access Point and User against man-in-the-middle attacks
• Ensure data integrity

### **4. Disadvantages**

• Can be attacked by DoS
• Since it uses RC4, it can be attacked by the FMS
• PSK has a problem of sharing keys between multiple users

## **C. WPA2**

### **1. Introduction**

WPA2 (Wi-Fi Protected Access 2) is the second generation of the Wi-Fi Protected Access wireless security protocol What is the upgrade version of WPA. Like its predecessor, WPA2 was designed to secure and protect Wi-Fi networks. WPA2 ensures that data sent or received over your wireless network is encrypted, and only people with your network password have access to it.
WPA2 has a very high level of security like standard WPA.
WPA2 also has 2 versions: personal and enterprise.
• WPA2 Enterprise: suitable for networks with high security such as main government, large enterprises.
• WPA2 personal: suitable for small and medium networks, home networks. Authentication in this type, use PSK same as WPA, but it used AES algorithm. The algorithm is stronger than TKIP in WPA.
WPA2 is a certification from the Wi-Fi Alliance for 802.11i-compliant products. The 802.11i amendment has a few security protocols that make it a strong replacement for WEP. All Wi-Fi-certified products since 2006 are required to support WPA2 as well.
WPA2 is structured a lot like WEP. When you used WEP (assuming nobody cracked your key), hackers were kept off and data were encrypted. When you use WPA2, both the network and the data are secured as well. Only this time you’re using AES-CCMP (Advanced Encryption Standard – Counter-Mode Cipher-Block-Chaining Message-Authentication-Code Protocol) encryption, which has no known flaws. That means no cracking, no sniffing and, most importantly, no network access for hackers.
WPA2 is recommended by the National Institute of Standards and Technology (NIST)

### **2. Authentication**

#### WPA2 – Personal:

• WPA2-Personal or WPA2 Pre-Shared Key (WPA2-PSK) is a widely adopted method to secure wireless networks. A pre-shared key or passphrase is used for authentication, in the personal mode. In a WPA2-PSK that is wpa2-personal, access is granted by common pre-shared key means a common password at the router level and it does not require an additional authentication server.
• WPA2-PSK (Pre-Shared Key) requires a single password to get in hold with the wireless network. It’s commonly a notion that a single password to access Wi-Fi is safe, but it’s only as much as one trusts the individual using it. Basically WPA2-PSK is a technique of securing a network using WPA2 with the use of the optional Pre-Shared Key (PSK) authentication. It is mostly designed for home users without an enterprise authentication server.
• To encrypt a network with WPA2-PSK the router is not provided with an encryption key but rather a plain-English passphrase between certain amounts of characters. The passphrase along with the network SSID by using a technology called TKIP (for Temporal Key Integrity Protocol) is used to generate unique encryption keys for each wireless client. Encryption keys are constantly changed.

#### WPA2 - Enterprise:

• WPA2 – enterprise use 802.1X/EAP authentication
• 802.1X is an IEEE standard framework for encrypting and authenticating a user who is trying to associate to a wired or wireless network. WPA-Enterprise uses TKIP with RC4 encryption, while WPA2-Enterprise adds AES encryption.
• 802.1X can be transparent to wireless users. For example, Windows machines can be configured for single sign-on, such that the same credentials that a user enters to log into his machine are passed automatically to the authentication server for wireless authentication. The user is never prompted to re-enter his credentials.
• 802.1X utilizes the Extensible Authentication Protocol (EAP) to establish a secure tunnel between participants involved in an authentication exchange. The MR supports multiple EAP types, depending on whether the network is using a Meraki-hosted authentication server or a customer-hosted authentication server. The following table shows the EAP types supported by the MR access points:
![](https://i.imgur.com/yEQnpqh.png)
![](https://i.imgur.com/dqGlvOB.png)

### **3. Advantages**

• WPA2 gives Wi-Fi users a higher level of security. And this is so that data shared over the network can only be accessed by authorized users.
• It delivers more secure network access control and stronger data protection.
• WPA2 also simple to use

### **4. Disadvantages**

• WPA2 is the amount of processing power that it needs to protect your network. Thus, this translates to a direct need for more powerful hardware, or one will suffer a reduction in network performance for heavily used networks. This is an issue with older access points which were designed and built prior to WPA2 and only implemented WPA2 via a firmware upgrade.

## **D. RSN**

### **1. Introduction**

Robust Security Network (RSN), which dynamically negotiates the authentication and encryption algorithms to be used for communications between WAPs and wireless clients. This means that as new threats are discovered, new algorithms can be added.
RSN uses the Advanced Encryption Standard (AES), along with 802.1x and EAP.

### **2. Authentication**

#### Key Hierarchies and Key Distribution and Management

#### Pairwise Key Hierarchy

##### Pre-Shared Key (PSK):

A PSK is a static key delivered to the AS and the STA through an out of-band mechanism. The PSK may be generated and installed in any number of ways, including proprietary automated public-key cryptographic approaches, and manual means such as a USB device or a passphrase.
![](https://i.imgur.com/6iCdhSs.png)

##### Authentication, Authorization, and Accounting Key (AAAK):

The AAA key, also known as the Master Session Key (MSK), is delivered to the AP through the Extensible Authentication Protocol (EAP) during the process of establishing an RSNA. Each time a user authenticates to the WLAN, the AAA key changes; the new key is then used for the duration of the user’s session, which lasts until the key lifetime expires or the user reauthenticates.
The root key—either the PSK or the AAAK—is used to formulate the Pairwise Master Key (PMK). The PMK is a key-generating key used for the derivation of the Pairwise Transient Key (PTK), along with the MAC address of the STA and AP and nonces that each creates for the key generation process. The PTK is composed of the following three keys:

- EAP Over LAN (EAPOL) Key Confirmation Key (EAPOL-KCK)
- EAPOL Key Encryption Key (EAPOL-KEK)
- Temporal Key (TK)

##### Group Temporal Key (GTK): :

Unlike the PMK, the GTK is generated by the authenticator (AP) and transmitted to its associated STAs.
![](https://i.imgur.com/VCKRXRt.png)

#### RSN Data Confidentiality and Integrity Protocols

Two RSNA data confidentiality and integrity protocols: Temporal Key Integrity Protocol (TKIP) and Counter Mode with Cipher Block Chaining MAC Protocol (CCMP).

##### - Temporal Key Integrity Protocol (TKIP):

TKIP is a cipher suite for enhancing the WEP protocol on pre-RSN hardware without causing significant performance degradation. TKIP works within the processing constraints of first-generation STAs and APs, and therefore enables increased security without requiring hardware replacement.
TKIP provides the following fundamental security features for IEEE 802.11 WLANs

##### - Counter Mode with Cipher Block Chaining MAC Protocol (CCMP):

CCMP is the second data confidentiality and integrity protocol that may be negotiated as a cipher suite for the protection of user traffic in an RSNA. Like TKIP, CCMP was developed to address all known inadequacies of WEP; however, CCMP was developed without the constraint of requiring the use of existing hardware. CCMP is considered the long-term solution for the creation of RSNs for WLANs. It is mandatory for RSN compliance.

### **3. Advantages**

- Optimized Client Services.
- Your clients are the backbone of your business. ...
- Increased Profits.
- Flexible, Scalable Security Measures.
- Greater Vulnerability Detection.

## **REFERENCES**

https://techgenix.com/80211i-wpa-rsn-wi-fi-security/
https://zencc.net/solutions/netpass-network-security/wpa2-enterprise-authentication.php#:~:text=WPA2%2D%20Personal%20uses%20pre%2Dshared%20keys%20(PSK)&text=A%20pre%2Dshared%20key%20or,require%20an%20additional%20authentication%20server.
https://www.encryptionconsulting.com/is-wpa2-psk-vulnerable/
https://scadahacker.com/library/Documents/Standards/NIST%20-%20800-97%20-%20Establishing%20Wireless%20Robust%20Security%20Networks.pdf
https://www.techtarget.com/searchmobilecomputing/definition/Wi-Fi-Protected-Access
