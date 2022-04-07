# 19MMT_Group06_Securing Microservices Communication: mTLS, JWT and gRPC

## Overview

### Micoservices:

---

Microservices is an approach to software architecture that instead of building a big monolithic project, the same project can be build the same project in a faster way from multiple small components that each perform a single function, such as authentication, notification, or payment processing. Each microservice is a distinct unit within the software development project, with its own codebase, infrastructure, and database, and those interact by messages.
![](https://i.imgur.com/pMFC0jg.png)

### Why microservices

---

By using microservices to build your project, that means you turn it into a set of independent services, which are faster to develop and much easier to understand and maintain. Each service can also be developed separated and that team could focus on that service only.

ADVANTAGES:

- Load Balancing: Safely and independently scale out individual app components using advanced load balancing
- Faster development: Update app components on their own schedules without worrying about dependencies on other components
- Flexible development: Deploy app components piece-by-piece without affecting other systems
- Simpler: Develop and maintain more easily
- Cache: Improve performance while reducing load on your app with flexible content caching

### Securing Microservices

---

One of the most complex problems in building software systems or applications is the security. This problem became more difficult while using microservices architecture, when the system is divided into many independent components, operating distributed on many devices with different technologies. The communication between components also becomes more overlapping and complex, thereby easily creating security weaknesses in the system if not designed and managed strictly. For that reason, we need to focus on security requirements with the ability to encrypt end-to-end information, implement monitoring and control mechanisms for all both the communication between the system and the external environment as well as the communication between services.

Here are some kind of Securing Microservices Communication: mTLS, JWT and gRPC

## mTLS

### 1. What is TLS?

---

Transport Layer Security (TLS) is an encryption protocol in wide use on the Internet. TLS, which was formerly called SSL, authenticates the server in a client-server connection and encrypts communications between client and server so that external parties cannot spy on the communications.
There are three important things to understand about how TLS works:

1.  Public key and private key.

TLS works using a technique called public key encryption, which relies on a pair of keys — a public key and a private key.

- Anything encrypted with the public key can be decrypted only with the private key
- Anything encrypted with the private key can be decrypted only with the public key

Therefore, a server that decrypts a message that was encrypted with the public key proves that it possesses the private key. Anyone can view the public key by looking at the domain's or server's TLS certificate.

2. TLS certificate.

A TLS certificate is a data file that contains important information for verifying a server's or device's identity, including the public key, a statement of who issued the certificate (TLS certificates are issued by a certificate authority), and the certificate's expiration date.

3. TLS handshake.

The TLS handshake is the process for verifying the TLS certificate and the server's possession of the private key. The TLS handshake also establishes how encryption will take place once the handshake is finished.

### 2. What is mTLS?

---

Mutual TLS, or mTLS for short, is a method for mutual authentication. mTLS ensures that the parties at each end of a network connection are who they claim to be by verifying that they both have the correct private key. The information within their respective TLS certificates provides additional verification.
mTLS is often used in a Zero Trust security framework\* to verify users, devices, and servers within an organization. It can also help keep APIs secure.

\*_Zero Trust means that no user, device, or network traffic is trusted by default, an approach that helps eliminate many security vulnerabilities._

### 3. How does mTLS work?

---

| TLS                                                                  | mTLS                                                                  |
| -------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Client connects to server.                                           | Client connects to server.                                            |
| Server presents its TLS certificate.                                 | Server presents its TLS certificate.                                  |
| Client verifies the server's certificate.                            | Client verifies the server's certificate.                             |
| Client and server exchange information over encrypted TLS connection | Client presents its TLS certificate                                   |
|                                                                      | Server verifies the client's certificate                              |
|                                                                      | Server grants access                                                  |
|                                                                      | Client and server exchange information over encrypted TLS connection. |

### 4. Why use mTLS?

---

mTLS helps ensure that traffic is secure and trusted in both directions between a client and server. This provides an additional layer of security for users who log in to an organization's network or applications. It also verifies connections with client devices that do not follow a login process, such as Internet of Things (IoT) devices.
mTLS prevents various kinds of attacks, including:

- On-path attacks: On-path attackers place themselves between a client and a server and intercept or modify communications between the two. When mTLS is used, on-path attackers cannot authenticate to either the client or the server, making this attack almost impossible to carry out.
- Spoofing attacks: Attackers can attempt to "spoof" (imitate) a web server to a user, or vice versa. Spoofing attacks are far more difficult when both sides have to authenticate with TLS certificates.
- Brute force attacks: Typically carried out with bots, a brute force attack is when an attacker uses rapid trial and error to guess a user's password. mTLS ensures that a password is not enough to gain access to an organization's network. (Rate limiting is another way to deal with this type of bot attack.)

## JWT

### 1. What is JSON Web Token?

---

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA. Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

### 2. When should you use JSON Web Tokens?

---

- Authorization: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.
- Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

### 3. JWT Stucture

---

JSON Web Token (JWT) includes 3 components: Header, Payload, Signature. These elements are separated from each other by the character “.”. Therefore, we can imagine its structure will follow the following format: “header.payload.signature”.

1. Header

The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

- For example:
  ![](https://i.imgur.com/RVwk7ee.png)

Then, this JSON is Base64Url encoded to form the first part of the JWT.

2. Payload

The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.

- Reserved claims: These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: iss (issuer), exp (expiration time), sub (subject), aud (audience), and others.
- Public claims: These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.
- Private claims: These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.

For example:

![](https://i.imgur.com/uuPyWiT.png)

The payload is then Base64Url encoded to form the second part of the JSON Web Token

3. Signature:

To create the signature part you have to take the encoded header, the encoded payload, a secret string, the algorithm specified in the header, and sign that.

For example if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:
![](https://i.imgur.com/n5rhKg7.png)

The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.
Then, we put all together is separated by a dot (“.”)
Example:
![](https://i.imgur.com/RzNYS9N.png)
If you want to play with JWT and put these concepts into practice, you can use jwt.io Debugger to decode, verify, and generate JWTs.

![](https://i.imgur.com/h1NHcRu.png)

### 4. How do JSON Web Tokens work?

---

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:
![](https://i.imgur.com/GyEtss1.png)

This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced, though this may not always be the case.

Note that if you send JWT tokens through HTTP headers, you should try to prevent them from getting too big. Some servers don't accept more than 8 KB in headers. If you are trying to embed too much information in a JWT token, like by including all the user's permissions, you may need an alternative solution, like Auth0 Fine-Grained Authorization.

If the token is sent in the Authorization header, Cross-Origin Resource Sharing (CORS) won't be an issue as it doesn't use cookies.

The following diagram shows how a JWT is obtained and used to access APIs or resources:

![](https://i.imgur.com/r31Kx5o.png)

## gRPC

### 1. What is gRPC?

---

- gRPC is an open source framework developed by Google.
- gRPC is a part of project Cloud Native Computation Foundation(CNCF).
- This CNCF project consists of containers like Docker or Kubernetes. These examples are important parts nowadays.
- gRPC let us define method Request and Response for RPC.
- The most important, gRPC is a modern, fast and efficient, based on HTTP/2 protocol, low latency and support streaming. Moreover, it’s language independent so it can support many type of programming language.

For example: Client A uses Java, Client B uses Python, both can make a connection to a Ruby Server. Because of its flexibility it can be used in authentication, load balancing, logging and monitoring

- From gRPC ‘s benefits, it look like a perfect framework

### 2. What is RPC?

---

- RPC stands for Remote Procedure Call.
- RPC is a Client-Server communication using call function method instead of using HTTP protocol.
- It uses IDL(Interface Definition Language) as a rule when writing functions and data type definitions.
- From Client perspective, it looks like just calling a function from the Server.
- gRPC imitate the communication architecture between client and server and implement it, that makes it popular in just 5 years.
- But gRPC is not the first to use this architecture(COBRA does this before). But COBRA use GIOP/IIOP – a method based on TCP/IP while gRPC use HTTP/2 as its protocol. Later HTTP/2 is considered more friendly with Internet infrastructure (ex: proxy, firefox,…)

### 3. gRPC usage:

---

- This is a basic example of using gRPC.

![](https://i.imgur.com/tWSXBYf.png)

- The most important part of using gRPC is defining messages and services.
- We can consider using a message like using struct. It defines the structure in a .proto file.
- A message consists of a series of data pairs called fields.

![](https://i.imgur.com/0AY8nJz.png)

- We can define gRPC services in .proto file with method RPC and return type as protocol buffer.

### 4. What is protocol buffer?

---

- Protocol buffer aka protobuf is a popular IDL which is used in gRPC. It’s where you store data and contracts of function as .proto file.
- Protobuf is language independent thus it can be easily serialized. Serialize is the process that convert an object into a stream of bytes to save or move into memory, database or file.
- It can easily move a big chunk of data.
- Protocol buffer allows API evolution using rules.

## References

https://www.freecodecamp.org/news/what-is-grpc-protocol-buffers-stream-architecture/
https://grpc.io/docs/what-is-grpc/introduction/
https://livebook.manning.com/book/microservices-security-in-action/chapter-1/v-4/69
https://www.microservicesvn.com/docs/security/security.html
https://viblo.asia/p/microservices-la-gi-gAm5yjD8Kdb
https://www.nginx.com/learn/microservices/

- [JSON Web Token Introduction](https://jwt.io/)
- [Tìm hiểu về json web token (JWT)](https://viblo.asia/p/tim-hieu-ve-json-web-token-jwt-7rVRqp73v4bP)
