## SHORT Questions

### Cyber Threat

A cyber threat is a malicious act which tries to steal data, damage data or aims to gain unauthorised access to data.
Cyber threats include virus attack, Dos attack, trojan horse attack, etc.
cyber threats can come from inside organization with authorized user or by a third party remotely.

### Trojan Horse

Trojan horse is a malicious software that is camouflaged as a real software, like a game, program, or even an antivirus software.
When installed it causes harm to the system like deleting hard drive data, killing background system apps etc.

### Passive Attack

A passive attack aims to use information of system but doesn't affects its resources. The attacker simply observes or eavesdrops on the communication between two parties, without altering or affecting the communication in any way. The purpose of a passive attack is typically to gather information or data without being detected.

### Cryptography

Cryptography is a technique of securing data from unauthorized access by converting data into cipher text, then only the people with decryption key can access the original data.
there are 3 types of cryptography

- symmetric key cryptography
- asymmetric key cryptography
- hash function cryptography
  Cryptography is used **everywhere in our daily lives**, Banking transaction, e-commerce websites, etc.

### Encryption

Encryption is a technique in which data is converted into cipher text that is unreadable by any human.
The purpose of encryption is to protect sensitive data from unauthorized access.
Encryption is a specific type of cryptographic technique. In other words it is a subset of cryptography.

### Cipher text

cypher text or encrypted text is a series of randomised letters that a human cannot understand.
An encryption algo takes in plain text and then converts it into cipher text.
This cipher text can then be reversed through decryption to get back the original text.

## Types of Cryptography

**Symmetric key cryptography-** In this method both sender and receiver use single key for encrypting and decrypting the data. symmetric key cryptography is fast but the sender and receiver must somehow share the common key in a secure manner.  
**Asymmetric key cryptography-** In this method different keys are used for encryption and decryption of data. In Asymmetric method sender uses an public key for encryption and receiver uses a private key for decrypting data.  
**Hash functions-** This method doesn't use any key instead it uses a hash code made from integer and alphabet combo.

## Discuss the essential ingredients of a symmetric key cryptography.

symmetric key cryptography is a method of encrypting data to protect it from unauthorized access.
its components are:

- **key:** security key is a secret code used to turn data in to cipher text, without this key no one can access the original data. Both sender and receiver should have access to this key.
- **encryption algo:** The algo's used to convert data into cipher text.The same algo is used in encryption and decryption.
- **decryption algo:** The algo's used to convert cipher text back to plain text or data. The same algo is used to convert
- **secure key exchange:** A channel to securely share the security key.

## Explain the difference between symmetric key & asymmetric key cryptography.

| Symmetric Key Cryptography                                                                                                                                               | Asymmetric Key Cryptography                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Uses the same key for encryption and decryption                                                                                                                          | Uses different keys for encryption and decryption                                                                                                                                                                 |
| Faster and more efficient than asymmetric key cryptography                                                                                                               | Slower and less efficient than symmetric key cryptography                                                                                                                                                         |
| Requires a secure exchange of the secret key                                                                                                                             | Does not require a secure exchange of keys                                                                                                                                                                        |
| Suitable for encrypting large amounts of data                                                                                                                            | Suitable for encrypting small amounts of data                                                                                                                                                                     |
| Examples include AES and DES                                                                                                                                             | Examples include RSA and ECC                                                                                                                                                                                      |
| Used for bulk encryption of data                                                                                                                                         | Used for secure key exchange and digital signatures                                                                                                                                                               |
| The Mathematical Representation is as follows- P = D (K, E(P)) where K –> encryption and decryption key P –> plain text D –> Decryption E(P) –> Encryption of plain text | The Mathematical Representation is as follows- P = D(Kd, E (Ke,P)) where Ke –> encryption key Kd –> decryption key D –> Decryption E(Ke, P) –> Encryption of plain text using encryption key Ke . P –> plain text |
| The length of key used is 128 or 256 bits                                                                                                                                | The  length of key used is 2048 or higher                                                                                                                                                                         |
| The size of cipher text is the same or smaller than the original plain text.                                                                                             | The size of cipher text is the same or larger than the original plain text.                                                                                                                                       |

## Digital Signatures

Digital signature is a method to verify & authenticate messages transferred via an online medium, like email, invoice etc. In this method the sender uses public key to sign and encrypt a document, then the recipient uses a private key to decrypt the document. This way the confidentiality and authenticity of document is maintained.It is basically an electronic, encrypted stamp used for authenticating digital information.

## Diff. b/w active and passive attacks.

passive 2 types

- **eavesDropping:** attacker intercepts & listens the communication b/w 2 or more parties without their consent.This is very dangerous this type of attack can be performed by packet-sniffing or man-in-the-middle techniques.
- **Traffic analysis:** A traffic analysis attack is a type of cyber attack where an attacker monitors and analyzes network traffic to gain insights into the communication patterns of the targeted system or network.

## virus and its types

A computer virus is a malicious software that is designed to replicate itself and cause harm to a system. It transfers from one system to another without the owners consent.
it can cause many harms to system and user data.
it can crash your system.
it can send your data to some remote computer.

### types of computer viruses

- ransomeware: these are malicious software that encrypts user data and then asks for ransom for giving access to decryption key.
- spyware: these are viruses that install in the background and keep running in the background an collect data about user like their browser history, keystrokes, etc without them knowing.
- trojan horses: these are viruses that feel like a legit application. after they get access to user's device they can steal data.
- worms:

## phases of a virus

The life cycle of a computer virus can be divided into four phases:

#### Dormant phase

The virus is idle in the dormant phase. It has accessed the target device but does not take any action.

> **Note:** Not all viruses have the dormant phase.[](https://en.wikipedia.org/wiki/Computer_virus#cite_note-Stallings_2012_p.183-34)

#### Propagation phase

In the propagation phase, the virus starts propagating by replicating itself. The virus places a copy of itself into other programs or accomplishes certain system areas on the disk. Each infected program will contain a clone[](<https://en.wikipedia.org/wiki/Clone_(computing)>) of the virus, which will enter its own propagation phase as well.[](https://en.wikipedia.org/wiki/Computer_virus#cite_note-Stallings_2012_p.183-34)

#### Triggering phase

The triggering phase starts when the dormant virus is activated. It will perform the actions it is supposed to accomplish. This phase can be caused by various system events like the count of the times the virus has cloned or after a set time interval has elapsed.

#### Execution phase

In the execution phase, the payload will be released. It can harm deleting files, crashing the system, and so on. It can be harmless too and pop some humorous messages on screen.

## OSI

### **2. Security Mechanism**

The mechanism that is built to identify any breach of security or attack on the organization, is called a security mechanism. Security Mechanisms are also responsible for protecting a system, network, or device against unauthorized access, tampering, or other security threats. Security mechanisms can be implemented at various levels within a system or network and can be used to provide different types of security, such as confidentiality, integrity, or availability.

Some examples of security mechanisms include:

- **Encipherment (Encryption)** involves the use of algorithms to transform data into a form that can only be read by someone with the appropriate decryption key. Encryption can be used to protect data it is transmitted over a network, or to protect data when it is stored on a device.
- **Digital signature** is a security mechanism that involves the use of cryptographic techniques to create a unique, verifiable identifier for a digital document or message, which can be used to ensure the authenticity and integrity of the document or message.
- **Traffic padding** is a technique used to add extra data to a network traffic stream in an attempt to obscure the true content of the traffic and make it more difficult to analyze.
- **Routing control** allows the selection of specific physically secure routes for specific data transmission and enables routing changes, particularly when a gap in security is suspected.

### **3. Security Services:**

Security services refer to the different services available for maintaining the security and safety of an organization. They help in preventing any potential risks to security. Security services are divided into 5 types:

- **Authentication** is the process of verifying the identity of a user or device in order to grant or deny access to a system or device.
- **Access control** involves the use of policies and procedures to determine who is allowed to access specific resources within a system.
- **Data Confidentiality** is responsible for the protection of information from being accessed or disclosed to unauthorized parties.
- **Data integrity** is a security mechanism that involves the use of techniques to ensure that data has not been tampered with or altered in any way during transmission or storage.
- **Non- repudiation** involves the use of techniques to create a verifiable record of the origin and transmission of a message, which can be used to prevent the sender from denying that they sent the message.
