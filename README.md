# Entice Chat app

**Title: Creating encrypted chat between two clients**

## 1. Introduction
In the modern digital era, secure communication is a critical requirement. This project implements an encrypted chat system that ensures confidentiality, integrity, and authenticity between two clients. The chat uses a hybrid encryption mechanism combining RSA for key exchange and AES for message encryption.

## 2. Objectives
- To develop a real-time chat application with end-to-end encryption.
- To implement RSA for secure key exchange.
- To use AES for encrypting and decrypting chat messages.
- To ensure seamless and secure communication between two clients over a server.

## 3. System Architecture
The system comprises three main components:
1. **Server (Server.py)**: Handles client connections and message forwarding.
2. **Client 1 (client_1.py)**: First user participating in encrypted chat.
3. **Client 2 (client_2.py)**: Second user participating in encrypted chat.
4. **Encryption Module (RSA.py)**: Manages key generation, encryption, and decryption.

## 4. Encryption Mechanism
### **4.1 RSA (Rivest-Shamir-Adleman) for Key Exchange**
- Each client generates a pair of RSA keys (public and private).
- The public key is shared with the other client through the server.
- The private key remains confidential and is used for decrypting exchanged keys.

### **4.2 AES (Advanced Encryption Standard) for Message Encryption**
- A symmetric AES key is generated and encrypted using RSA.
- Messages are encrypted using AES before transmission.
- The recipient decrypts the AES-encrypted message using the shared AES key.

## 5. Implementation
### **5.1 Server Implementation**
- The server runs a multi-client socket-based application.
- It listens for connections, receives messages, and forwards them securely.

### **5.2 Client Implementation**
- Each client connects to the server and exchanges RSA keys.
- Messages are encrypted using AES before transmission.
- Upon receiving a message, the client decrypts it using AES.

## 6. Code Files
- **Server.py**: Handles client connections and message forwarding.
- **client_1.py & client_2.py**: Implement encrypted messaging logic.
- **RSA.py**: Manages RSA key generation, encryption, and decryption.

## 7. Results
- Successfully established a secure chat channel between two clients.
- Messages exchanged were encrypted, preventing unauthorized access.
- The hybrid encryption approach ensured high security without compromising performance.

## 8. Future Enhancements
- Implement a **Graphical User Interface (GUI)** for improved user experience.
- Add support for **multiple users** with individual encryption keys.
- Integrate **end-to-end authentication** using digital signatures.
- Deploy the chat application over **a secure cloud environment**.

## 9. Conclusion
This project successfully demonstrates a secure chat application using hybrid encryption. By integrating RSA for key exchange and AES for secure message transmission, the system ensures encrypted communication between two users.

---
**Project Developed By: [Soumyadip Saha]**



# RSA (Rivest–Shamir–Adleman)

RSA (Rivest–Shamir–Adleman) is one of the first public-key cryptosystems and is widely used for secure data transmission. In such a cryptosystem, the encryption key is public and it is different from the decryption key which is kept secret (private). In RSA, this asymmetry is based on the practical difficulty of the factorization of the product of two large prime numbers, the "factoring problem". The acronym RSA is made of the initial letters of the surnames of Ron Rivest, Adi Shamir, and Leonard Adleman, who first publicly described the algorithm in 1978. Clifford Cocks, an English mathematician working for the British intelligence agency Government Communications Headquarters (GCHQ), had developed an equivalent system in 1973, but this was not declassified until 1997.

A key generation function code used in this project is given below:

```python3
    def key_generator():
    
        p, q = primes.choose_distinct_primes()
        n = p * q
        phi = (p-1) * (q-1)  # Euler's function (totient)
        e = choice(coprimes(phi))
        d = modinv(e, phi)
        
        public_key = [e, n]
        private_key = [d, n]
        return [public_key, private_key]
```

