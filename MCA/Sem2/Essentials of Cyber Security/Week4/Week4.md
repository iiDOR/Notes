## Securing Digital Data
### 3 Stages of digital data
#### 1. Data at rest.
- Data that is **stored permanently on a storage medium.**
- Where is it stored ?
	- **Hard Drives, SSDs, USB drives.**
- Threats --> Theft of device.
#### 2. Data in motion.
- Data that is **actively travelling across a network.**
- Where is it stored ?
	- **Internet, LAN, Wi-Fi.**
- Threats --> Eavesdropping (sniffing), man in the middle (MITM).
#### 3. Data in use.
- Data that is currently **being processed by the system.**
- Where is it stored ?
	- **RAM** (memory), **cache**, **temp** **files**
- Threats --> Memory scraping, cold boot attacks.

# Secure Communication
- **Cryptography** exists to **~={green}ensure secure communication=~**
- **Confidentiality:**
	- **Requirement #1:** Only the **~={cyan}sender and the receiver should be able to understand the message=~** 
	- So, ~={yellow}i**n our scenario, only Alice and Bob should be able to understand the message**=~
	- This property is called ‘**~={green}Confidentiality=~**’, protecting data from unauthorized viewers

- **~={green}Solution to achieve Secure Communication=~** is **Secure Channel**:
	- The solution is to use a channel that’s only accessible to Alice and Bob 
	- If Eve can’t even access the message, there is nothing she can do.

- **Confidentiality in public**
	- **Only the sender and the receiver should be able to understand the message (confidentiality)**
	- Even if the **communication channel is insecure** • Often, we won’t be able to confirm the nature of the underlying communication medium
	
- **Problem with plaintext**
	- If we try to just exchange the message, Eve will be able to read the message.

- **~={green}Solution to this is Encryption=~**
	- Encryption ~={green}~={cyan}**turns the message into unreadable gibberish** =~=~
	- This unreadable **gibberish is called ciphertext** 
	- Decryption turns the **ciphertext back into the message** 
	- Ideally no-one can get any information about the message from the ciphertext
# Kerkhoff's Principle
- Kerckhoff's second principle states that a **~={cyan}military cipher should not involve secrecy=~** and **~={blue}it should not be a problem if it falls into enemy hands=~**.
- **Essentially the ~={yellow}security of the system=~ should not hinge on the ~={green}secrecy of the cipher itself=~**

## Reasonings behind Kerckhoff's principle
- Keeping ~={blue}**small keys secure is much easier** than=~ ~={yellow}**keeping the whole system secure.**=~
- Even **if the enemy obtains the key**, **~={cyan}the usability of the same key is limited to a certain timeframe.=~**
- The fewer secrets required, the easier it is to maintain the system.

## Reasons to use public algorithms
- It's **~={yellow}better to use algorithms that have already withstood years of cryptanalysis by world class experts=~**
- It ensures **~={cyan}that there won't be obvious or trivial oversights=~** in the algorithms themselves.
- The security properties and problems of the algorithms would also have been well understood by experts.

# Symmetric Key Algorithms

## Keys: The secret ingredient 
- In our previous scheme, we had the problems of 
- Eve gaining **access to all future messages** 
- The **practical difficulty in changing the algorithm**

- **Solution is to introduce keys**
	- Both the **Encryption and Decryption algorithm depends on keys**
## Symmetric key algorithms
- Symmetric key algorithms are ~={purple}**based on a simple principle**.=~
	- The **~={yellow}same key is used for both encryption and decryption=~**
- This means that the **keys should have been previously securely** communicated 
- This is also the **~={purple}main drawback of this scheme=~**

- **~={red}Shared Secret=~**
	- Suppose that ~={blue}**Alice is the one who generates the key**=~ 
	- **~={yellow}Alice must find a secure way to communicate the key to Bob=~** 
	- If she can securely share the key, can’t she securely share the message too?
## Symmetric key encryption
- Alice creates the ciphertext by encrypting the message with the shared key 
- Alice then sends this ciphertext across to Bob
## Symmetric key decryption
- Bob decrypts the cyphertext by using the shared key 
- The result of the decryption will be the message that Alice wanted to securely communicate

# Integrity & Authentication
- So based on our current scheme 
	- Alice ~={blue}**creates the ciphertext by encrypting the message with the shared key=~** 
	- Alice then ~={cyan}**sends this ciphertext across to Bob=~**

	- Bob **~={blue}decrypts the ciphertext by using the shared key=~** 
	- The result of the decryption will be the **~={cyan}message that Alice wanted to securely communicate=~**

	- **~={yellow}Guarantees provided by the current scheme=~**
		- ~={pink}Even if the channel is insecure=~, without the key, **~={cyan}the original message cannot be read=~** • Essentially, **confidentiality, protection of data from unauthorized access**

	- **Problem** - **~={red}Eve changing the ciphertext=~**
		- Eve can't access it, can't understand it, but she can change it however she wants and there is no way for BOB to detect that message is changed.

	- **~={purple}Solution Authentication / Integrity / Data origin authentication=~**
		- Bob **~={green}cannot determine whether the message came from Alice or Eve=~**
		- The property that we want here, ~={cyan}**for Bob to confirm that the data came from Alice**=~ **~={yellow}is called Authentication=~**