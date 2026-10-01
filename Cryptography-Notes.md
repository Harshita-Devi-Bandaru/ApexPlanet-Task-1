# Cryptography Notes

## ApexPlanet Internship – Task 1

This section contains the basic cryptography topics I studied for Task 1.

The topics covered are:

- Symmetric encryption
- Asymmetric encryption
- MD5
- SHA-256
- Digital certificates
- SSL/TLS
- OpenSSL encryption and decryption

---

## 1. What is Cryptography?

Cryptography is used to protect information from unauthorized access or modification.

It is used in many areas of cybersecurity, including secure communication, data protection and authentication.

The basic idea is:

```text
Original Data
     ↓
Cryptographic Process
     ↓
Protected Data
```

---

## 2. Symmetric Encryption

Symmetric encryption uses the **same key** for encryption and decryption.

```text
Plaintext
    ↓
Encryption + Key
    ↓
Ciphertext
    ↓
Decryption + Same Key
    ↓
Plaintext
```

The main advantage is that it is generally fast and suitable for encrypting large amounts of data.

The main challenge is securely sharing the secret key.

Examples include:

- AES
- DES
- 3DES

---

## 3. Asymmetric Encryption

Asymmetric encryption uses two keys:

- Public key
- Private key

The public key can be shared, while the private key should be kept secret.

A simplified example:

```text
Sender
   ↓
Receiver's Public Key
   ↓
Encrypted Data
   ↓
Receiver's Private Key
   ↓
Original Data
```

Examples include:

- RSA
- ECC

---

## 4. Symmetric vs Asymmetric

| Symmetric | Asymmetric |
|---|---|
| Uses one shared key | Uses public and private keys |
| Generally faster | Generally slower |
| Key must be shared securely | Public key can be shared |
| Example: AES | Example: RSA |

---

## 5. Hashing

Hashing converts input data into a fixed-size value called a hash.

```text
Input
  ↓
Hash Function
  ↓
Hash Value
```

Hashing is different from encryption because a cryptographic hash is designed as a one-way operation.

It can be used for checking whether data has changed.

---

## 6. MD5

MD5 stands for **Message-Digest Algorithm 5**.

It produces a **128-bit hash**.

Example:

```text
File
 ↓
MD5
 ↓
128-bit hash
```

MD5 is no longer considered secure for applications that require collision resistance. It may still be found in older systems and files.

---

## 7. SHA-256

SHA-256 is part of the SHA-2 family.

It produces a **256-bit hash**.

It can be used for things such as:

- File integrity checking
- Data verification
- Security applications

Example:

```text
File
 ↓
SHA-256
 ↓
256-bit hash
```

### MD5 and SHA-256

| MD5 | SHA-256 |
|---|---|
| 128-bit output | 256-bit output |
| Older hash algorithm | SHA-2 family |
| Not recommended for security-sensitive collision resistance | Widely used for integrity-related purposes |

---

## 8. Digital Certificates

A digital certificate is used to associate a public key with an identity.

Certificates are commonly used in HTTPS connections.

A certificate can contain information such as:

- Domain/subject
- Public key
- Issuer
- Validity period
- Digital signature

A **Certificate Authority (CA)** issues and signs certificates.

---

## 9. SSL/TLS

TLS stands for **Transport Layer Security**.

It is used to protect communication over a network.

HTTPS uses HTTP over TLS.

```text
HTTP
   +
 TLS
   ↓
HTTPS
```

TLS helps provide:

- Confidentiality
- Integrity
- Authentication

When a website uses HTTPS, the browser establishes a TLS-secured connection with the server.

---

## 10. OpenSSL

OpenSSL is a tool that can be used for cryptographic operations and TLS-related tasks.

For this task, I used OpenSSL to practice basic encryption, decryption and hashing.

---

## 11. Creating a Test File

I created a small text file in Kali Linux:

```bash
echo "ApexPlanet Task 1" > message.txt
```

To check the file:

```bash
cat message.txt
```

---

## 12. Encrypting the File

I used OpenSSL with AES-256-CBC:

```bash
openssl enc -aes-256-cbc -salt -in message.txt -out message.enc
```

OpenSSL asks for a password during the process.

The encrypted file is saved as:

```text
message.enc
```

---

## 13. Decrypting the File

To decrypt the file:

```bash
openssl enc -d -aes-256-cbc -in message.enc -out decrypted.txt
```

I entered the same password that was used during encryption.

Then I checked the decrypted file:

```bash
cat decrypted.txt
```

The output should match the original contents of `message.txt`.

---

## 14. SHA-256 Hash

I used `sha256sum` to generate a SHA-256 hash:

```bash
sha256sum message.txt
```

I also checked it using OpenSSL:

```bash
openssl dgst -sha256 message.txt
```

Both commands can be used to calculate the SHA-256 digest of the file.

---

## 15. Encryption vs Hashing

| Encryption | Hashing |
|---|---|
| Protects data confidentiality | Mainly used for integrity/verification |
| Can be decrypted with the required key | Designed as a one-way operation |
| Produces ciphertext | Produces a hash/digest |
| Example: AES | Example: SHA-256 |

---

## 16. Practical Exercise

### Step 1 – Create a file

```bash
echo "Cybersecurity Task 1" > crypto-test.txt
```

### Step 2 – Encrypt it

```bash
openssl enc -aes-256-cbc -salt -in crypto-test.txt -out crypto-test.enc
```

### Step 3 – Decrypt it

```bash
openssl enc -d -aes-256-cbc -in crypto-test.enc -out crypto-decrypted.txt
```

### Step 4 – Check the result

```bash
cat crypto-decrypted.txt
```

### Step 5 – Generate SHA-256

```bash
sha256sum crypto-test.txt
```

---

## 17. Quick Reference

| Topic | What I understood |
|---|---|
| Symmetric encryption | Same key for encryption and decryption |
| Asymmetric encryption | Public/private key pair |
| MD5 | 128-bit hash, not suitable for modern security-sensitive use |
| SHA-256 | 256-bit SHA-2 hash |
| Digital certificate | Connects an identity with a public key |
| TLS | Helps secure network communication |
| OpenSSL | Tool for cryptographic operations |

---

## What I Learned

I learned the basic difference between encryption and hashing and the difference between symmetric and asymmetric encryption.

I also practiced creating a file, encrypting it with OpenSSL, decrypting it again and generating a SHA-256 hash.

These exercises helped me understand some of the cryptography concepts used in cybersecurity.
