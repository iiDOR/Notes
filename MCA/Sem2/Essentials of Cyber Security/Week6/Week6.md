# Symmetric V Asymmetric Encryption
## Problem with our current encryption scheme
- Encryption needs shared encryption key.
	- MAC’s need shared authentication key 
	- Both depend upon the key being a shared secret
## Symmetric encryption
- Symmetric encryption **uses the same key for encryption and decryption**
- That’s why the name, ‘symmetric’.
- This is also the reason why we need a shared encryption key.

- The question is **~={yellow}" is there a way to do encryption and decryption with different keys "=~**
## Asymmetric encryption
- **Asymmetric** meaning different **~={cyan}keys are used for encryption and decryption=~**
	- Also called as **~={yellow}public key cryptography.=~**
	- No **~={cyan}shared secret key required for encryption=~**

- **~={yellow}Pre requisites for Asymmetric encryption.=~**
	- **Alice wants to communicate with Bob** so some type of encryption is needed to confidentiality is need.
	- Alice and Bob both have their own keys
		- One 'public key' which can be made public
		- One ‘private’ key, which should be kept secret

- **Public key encryption**
	- Alice encrypts the message using Bob’s public key 
	- Alice gets Bob’s public key (over insecure channel?) 
	- Alice transmits the ciphertext over to Bob

- **Public key decryption**
	- Bob decrypts the message using his private key 
	- Security of the scheme depends on the private key 
	- No need to share the private key, just the public key

# Digital Signatures
## Digital Signatures
- Digital signatures can be **~={green}used just like MAC’s=~** and **~={green}verified by the receiver=~** to check **~={yellow}authenticity and integrity.=~**
- Digital signatures **~={cyan}are created using private key’s=~** and **~={blue}verified using public keys=~**
## Signing
- Alice wants to **~={yellow}send the ciphertext over to Bob=~**
- She **~={cyan}uses her private key and the ciphertext=~** to **create the signature**
- The **~={purple}ciphertext and the signature=~** is then transmitted over to Bob
## Verification
- Bob first obtains **Alice’s public key**
- Bob then **~={purple}verifies the signature and the message=~** by **~={green}using Alice’s public key=~**
- If the **~={green}ciphertext is verified=~**, **~={cyan}he can be sure that it was not modified and was sent by Alice=~**

# Certificates
## Exchange of keys
- For public key encryption, **~={blue}Alice gets Bob’s public key over an insecure channel=~**
- For digital signature verification, **~={blue}Bob get Alice’s public key over an insecure channel=~**
## Certificates
- Certificates contain 
	- The public key 
	- Information about the owner of the key 
	- Digital signature of the certificate body (above details

- For example, Bob’s public key would contain 
	- Bob’s public key 
	- Name: Bob 
	- Digital signature of the certificate body
## Certificate Authorities
- Who will sign the certificate ? 
- How can the certificate be verified? 
- Who will verify their public keys?

- **~={yellow}Certificate Authorities(CA’s)=~** verify the information presented in certificates and signs them.
	- **Root CAs** are **~={orange}trusted by everyone, and their certificate is installed in all systems involved.=~**
	- **Root CA’s** **~={purple}sign certificates of intermediatory CA’s=~**
## Certificate Revocation
- What happens when someone’s private key is compromised? 
- They can get a new certificate, but what about the validity of the old?

- There are mechanisms such as **~={yellow}Certificate Revocation Lists (CRL’s)=~** and **~={yellow}Online Certificate Status Protocol (OCSP)=~** to address this.
	- CRL’s are a **~={blue}list of certificates that are revokes and therefore invalid=~**
	- OCSP allows **~={blue}one to verify a whether a certificate is revoked or not=~**
## Certificate Generation
- Bob contacts the CA (Claire) **~={yellow}with his public key=~**
- Claire **~={yellow}verifies and signs the certificate=~**