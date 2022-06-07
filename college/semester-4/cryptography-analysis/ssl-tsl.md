# Cryptographic protocols

> Protocols for establishing authenticated and encrypted links between networked computers

## SSL / TSL

SSL was originally created by the inventors of NETSCAPE. Back in those days traffic was not encrypted. SSL permits computers to authenticate a website and the information sent to it will remain confidential. In practice, it permits an end user to navigate in a secure manner in a website.

### Characteristics

- Confidentiality/Privacy
  - The content that the users sees/does/sends while using a browser must remain confidential.
- Authenticity
  - The site has not been compromised and those who administrate it have not been supplanted

## SSL/TSL Handshake

1. The domain name is figured out through a DNS lookup
2. **ClientHello**: once the domain's name has been resolved, the client sends the server a message containing a suite of the cryptographic algorithms it has at its disposal:
   - SSL/TLS supported versions
   - Public and private key cryptographic algorithms
   - A random number
3. **ServerHello**: the server sees the available algorithms and makes a decision on which one to use. It then sends back a message containing the chosen algorithm, a random number and its authentication certificate.
4. The client then proceeds to check the authenticity of the given certificate with the person that the other site said created it.
   - The certificate is authenticate
   - The certificate is not signed by a proper authority, the user is then prompted to access the website at its own risk
   - The certificate contains irregularities, navigation is not allowed and the process ends
5. **ClientSecretExchange**: a secret is then exchanged with the server using a public key algorithm
6. **PrivateKeyUsed**: the server decrypts the secret
7. **SessionKey**: using the shared secret and the client's and servers' seeds a private key is generated, they must both arrive at the same result (I pulled a sneaky one out you, did you notice the Diffie-Hellman key exchange?)
8. The clients encrypts the ending message with a summary of the afore mentioned messages with the generated private key
9. **ServerFinish**: the server repeats the previous step
10. Communication begins
