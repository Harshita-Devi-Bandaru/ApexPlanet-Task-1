# Cryptography Notes

## ApexPlanet Task 1 – Foundation & Environment Setup

**Internship:** ApexPlanet Software Pvt. Ltd.  
**Domain:** Cybersecurity & Ethical Hacking  
**Task:** Task 1 – Foundation & Environment Setup

---

## 1. Introduction to Cryptography

Cryptography is the practice of protecting information by transforming readable data into a protected form so that unauthorized users cannot understand or modify it.

It is commonly used to provide:

- Confidentiality
- Integrity
- Authentication
- Data protection
- Secure communication

Cryptography is an important part of cybersecurity because sensitive information may travel through untrusted networks.

---

## 2. Symmetric Encryption

Symmetric encryption uses the **same key** for both encryption and decryption.

### Basic Process

```text
Plaintext
   |
   | Encryption + Secret Key
   ↓
Ciphertext
   |
   | Decryption + Same Secret Key
   ↓
Plaintext
```

### Example

If:

```text
Plaintext:  Hello
Key:        SecretKey
```

The encryption process produces ciphertext.

The receiver needs the **same secret key** to decrypt the ciphertext.

### Advantages

- Fast
- Suitable for encrypting large amounts of data
- Requires relatively less computational resources

### Challenge

The secret key must be securely shared between the sender and receiver.

### Examples

- AES
- DES
- 3DES

---

## 3. Asymmetric Encryption

Asymmetric encryption uses a **key pair**:

- Public key
- Private key

The public key can be shared, while the private key should be kept secret.

### Basic Process

```text
Sender
   |
   | Encrypt using Receiver's Public Key
   ↓
Ciphertext
   |
   | Decrypt using Receiver's Private Key
   ↓
Receiver
```

### Example

If a sender wants to securely send information to a receiver:

1. The sender obtains the receiver's public key.
2. The sender encrypts the information using the public key.
3. The encrypted information is sent to the receiver.
4. The receiver decrypts it using the corresponding private key.

### Advantages

- Solves the key-sharing problem associated with symmetric encryption.
- Supports secure communication and authentication mechanisms.

### Examples

- RSA
- ECC

---

## 4. Symmetric vs Asymmetric Encryption

| Feature | Symmetric Encryption | Asymmetric Encryption |
|---|---|---|
| Keys used | One shared key | Public and private key pair |
| Speed | Generally faster | Generally slower |
| Key sharing | Secret key must be shared securely | Public key can be shared |
| Common use | Bulk data encryption | Secure key exchange, authentication |
| Examples | AES, DES | RSA, ECC |

---

## 5. Hashing

Hashing converts data into a fixed-length value called a **hash** or **digest**.

Unlike encryption, hashing is designed as a one-way operation.

```text
Input Data
    |
    | Hash Function
    ↓
Hash / Digest
```

A hash is commonly used to verify whether data has been changed.

---

## 6. MD5

**MD5 (Message-Digest Algorithm 5)** produces a **128-bit hash value**.

Example:

```text
Input
  ↓
MD5
  ↓
128-bit hash
```

MD5 is historically important, but it is **not considered suitable for modern security-sensitive applications** because weaknesses allow collisions.

It may still be encountered when studying legacy systems or existing files.

---

## 7. SHA-256

**SHA-256** is a member of the SHA-2 family of cryptographic hash functions.

It produces a **256-bit hash value**.

Example:

```text
Input Data
    |
    | SHA-256
    ↓
256-bit Hash
```

SHA-256 can be used for:

- Data integrity verification
- File integrity checking
- Digital signatures as part of a larger process
- Security-related applications

### MD5 vs SHA-256

| Feature | MD5 | SHA-256 |
|---|---|---|
| Output size | 128 bits | 256 bits |
| Security | Cryptographically broken | Widely used |
| Common modern security use | Not recommended | Commonly used |
| Purpose | Hashing | Hashing |

---

## 8. Digital Certificates

A digital certificate is used to associate a public key with an identity.

Certificates are commonly used in secure web communication.

A certificate can contain information such as:

- Subject/domain
- Public key
- Certificate issuer
- Validity period
- Digital signature of the certificate authority

### Certificate Authorities

A **Certificate Authority (CA)** is an entity that issues and signs digital certificates.

Examples include publicly trusted certificate authorities used by websites and organizations.

---

## 9. SSL/TLS

**TLS (Transport Layer Security)** is a protocol used to provide secure communication over a network.

You may commonly see **HTTPS**, which uses HTTP over TLS.

### HTTP vs HTTPS

```text
HTTP
Client  <----------->  Server
       Unencrypted

HTTPS
Client  <===========>  Server
          TLS
       Encrypted/Secure
```

TLS helps provide:

- Confidentiality
- Integrity
- Authentication of the server through certificates

### HTTPS Example

When accessing:

```text
https://example.com
```

the browser establishes a TLS-secured connection with the server.

---

## 10. OpenSSL

**OpenSSL** is a widely used open-source toolkit that provides cryptographic functionality.

It can be used for tasks involving:

- Encryption and decryption
- Hash generation
- Key generation
- Certificates
- TLS-related operations

For this task, OpenSSL can be used to demonstrate basic encryption and decryption.

---

## 11. OpenSSL Encryption and Decryption

### Create a Test File

```bash
echo "ApexPlanet Cybersecurity Task 1" > message.txt
```

Check the contents:

```bash
cat message.txt
```

Expected output:

```text
ApexPlanet Cybersecurity Task 1
```

---

### Encrypt the File

A basic OpenSSL encryption example is:

```bash
openssl enc -aes-256-cbc -salt -in message.txt -out message.enc
```

OpenSSL will ask for a password.

The encrypted file can then be viewed:

```bash
ls -l message.txt message.enc
```

The encrypted file should not display the original readable text when opened as normal text.

---

### Decrypt the File

Use:

```bash
openssl enc -d -aes-256-cbc -in message.enc -out decrypted.txt
```

Enter the same password used during encryption.

Check the decrypted content:

```bash
cat decrypted.txt
```

Expected output:

```text
ApexPlanet Cybersecurity Task 1
```

### Encryption Flow

```text
message.txt
     |
     | AES-256-CBC + Password
     ↓
message.enc
     |
     | Decryption + Same Password
     ↓
decrypted.txt
```

---

## 12. Hashing with OpenSSL

A SHA-256 hash can be generated using:

```bash
openssl dgst -sha256 message.txt
```

Example format:

```text
SHA2-256(message.txt)= <hash-value>
```

The exact hash value depends on the file contents.

You can also use:

```bash
sha256sum message.txt
```

This generates the SHA-256 checksum of the file.

---

## 13. Comparing Encryption and Hashing

| Feature | Encryption | Hashing |
|---|---|---|
| Purpose | Protect data confidentiality | Verify data/integrity |
| Reversible | Yes, with the required key | Designed to be one-way |
| Output | Ciphertext | Fixed-length hash |
| Key | Usually required | Not required |
| Example | AES | SHA-256 |

---

## 14. Practical Cryptography Exercise

### Objective

Demonstrate basic encryption, decryption, and hashing using OpenSSL.

### Step 1 – Create File

```bash
echo "Cybersecurity Foundation Task 1" > crypto-test.txt
```

### Step 2 – Encrypt

```bash
openssl enc -aes-256-cbc -salt -in crypto-test.txt -out crypto-test.enc
```

### Step 3 – Decrypt

```bash
openssl enc -d -aes-256-cbc -in crypto-test.enc -out crypto-decrypted.txt
```

### Step 4 – Verify

```bash
cat crypto-decrypted.txt
```

The decrypted content should match the original file.

### Step 5 – Generate SHA-256 Hash

```bash
sha256sum crypto-test.txt
```

or:

```bash
openssl dgst -sha256 crypto-test.txt
```

---

## 15. Recommended Screenshots

For the Task 1 lab report, capture screenshots showing the actual commands and results.

### Screenshot 1 – Original File

Show:

```bash
cat crypto-test.txt
```

### Screenshot 2 – Encryption

Show:

```bash
openssl enc -aes-256-cbc -salt -in crypto-test.txt -out crypto-test.enc
```

### Screenshot 3 – Encrypted File

Show:

```bash
ls -l crypto-test.txt crypto-test.enc
```

### Screenshot 4 – Decryption

Show:

```bash
openssl enc -d -aes-256-cbc -in crypto-test.enc -out crypto-decrypted.txt
```

### Screenshot 5 – Decrypted Content

Show:

```bash
cat crypto-decrypted.txt
```

### Screenshot 6 – SHA-256

Show:

```bash
sha256sum crypto-test.txt
```

These screenshots provide evidence that the cryptography exercises were performed in the lab.

---

## 16. Key Terms

| Term | Meaning |
|---|---|
| Plaintext | Original readable data |
| Ciphertext | Encrypted data |
| Encryption | Converting plaintext into ciphertext |
| Decryption | Converting ciphertext back into plaintext |
| Key | Value used by a cryptographic algorithm |
| Hash | Fixed-length digest generated from data |
| Symmetric | Uses the same key for encryption and decryption |
| Asymmetric | Uses public and private keys |
| Certificate | Binds an identity to a public key |
| CA | Certificate Authority |
| TLS | Protocol for securing network communication |
| OpenSSL | Toolkit for cryptographic and TLS operations |

---

## 17. Learning Outcome

After completing this section, I understood:

- The basic purpose of cryptography.
- The difference between symmetric and asymmetric encryption.
- The concept of hashing.
- The difference between MD5 and SHA-256.
- The purpose of digital certificates.
- The role of TLS in secure communication.
- Basic encryption and decryption using OpenSSL.
- How SHA-256 can be used to verify file integrity.

---

## 18. Lab Environment

**Operating System:** Kali Linux  
**Virtualization:** VMware Workstation  
**Purpose:** Cybersecurity learning and controlled laboratory exercises

> All cryptography demonstrations were performed for educational purposes in a controlled lab environment.
