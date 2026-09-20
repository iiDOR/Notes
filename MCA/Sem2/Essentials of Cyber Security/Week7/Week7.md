# Hybrid Encryption
- So Hybrid Encryption is where you is Asymmetric for key exchange.
- and once communicated securely, use symmetric crypto to avoid the overhead from asymmetric crypto.
- **~={blue}THIS IS WAS IS OFFERED IN TLS Transport Layer Security.=~**

- ## HOW TO DO IT.
### Symmetric Key Generation
- Either ALICE or BOB creates the symmetric key in secure manner.
	- This will give as **~={orange}AUTHENTICATION key and ENCRYPTION key.=~**
### Certification Verification
- Before Alice encrypts, **~={orange}she will receive and verify the certificate of BOB=~**
	- this is done with the help of **~={blue}public key from CA and signature of the certificate=~**
### Asymmetric encryption
- The message here is the **~={purple}encryption key and authentication key and use certification to encrypt the message.=~**
### Digital Signature Creation
- Alice will use ~={blue}**her private key and the ciphertext to create a digital signature.**=~
- This **~={green}signature along with the ciphertext=~** is sent to Bob.
### Digital Signature Verification
- **~={yellow}BOB verifies Alice's public key=~** then verify ~={yellow}Alice signature by using Alice's public key, signature.=~
### Asymmetric decryption
- Now bob will decryption using this private key.
- and bob also has his own copy of symmetric authentication and encryption key
# Transport Layer Security
## Transport Layer Security (TLS)
- It is cryptographic protocol aimed at **~={yellow}providing secure communication over a computer network=~**
- Successor to SSL
- Used in HTTPS that is HTTP over TLS / SSL in application layer.
## Architecture
- TLS is divided into 3 parts.
	- **~={cyan}Authentication**=~
		- use Certificates because it **~={yellow}contains domain and public key=~** 
- ~={cyan}**Symmetric Key Exchange**=~
	- Symmetric key is generated and shared.
		- DHE and **its elliptic curve variant** provides **forward security**.
- **~={cyan}Symmetric Encryption=~**
	- after all communication is secured using encryption with data origin authentication.
	- tls allow a variety of symmetric algorithms to be used.
		- use MAC for data origin authentication.

# TLS Authentication
- Both sender and receiver where authentication.
- client authentication can be done, in most cases only server is authenticated
- Server authentication is done in two parts 
	- First the **server certificate is verified** 
	- Then the server must prove that its in possession of the **private key corresponding to the public key**

- **~={green}Authentication Algorithms=~**
	- TLS 1.2 and 1.3 provide
		- RSA 
		- DSA 
		- ECDSA