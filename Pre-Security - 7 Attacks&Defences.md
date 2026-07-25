# Pre-Security - 7. Attacks&Defences

## **1. CIA Triad** (**Confidentiality**, **Integrity**, and **Availability**)

**Confidentiality** ensures that sensitive data can only be accessed by authorized individuals. If confidentiality is not maintained, unauthorized individuals can access the data, resulting in financial loss, privacy violations, or legal consequences.

**Integrity** ensures that unauthorized individuals do not modify data. Without integrity, data can be altered and no longer be trusted. Unauthorized changes in data can sometimes lead to dangerous consequences.

**Availability** ensures that data and services are available to authorized users when needed. Although it comes as the third and last pillar of the CIA Triad, it is no less important than the other two. 

## **2. Cryptography Concepts Understanding the Basics**

Cryptography is the science of securing information by transforming **plaintext** into **ciphertext** using mathematical algorithms, ensuring that only authorized parties can interpret the data.

- **Plaintext** - A message you can read normally. Like `HELLO` or `Patient name: Alice Smith`.
- **Ciphertext** - A scrambled version that's not supposed to make sense. Like `KHOOR` or `Sdwlhqw qdph: Dolfh Vplwk`.
- **Key** - The secret ingredient that controls how scrambling and unscrambling work. Think of it as a password that the algorithm uses.
- **Algorithm** - The public recipe—the set of steps that explain how to use the key on the message. Everyone can know the algorithm. Security comes from keeping the key secret.

Real-world cryptography is way more sophisticated than what we'll use here. But the basic pattern stays the same:

**Encryption process: plaintext + encryption algorithm + key  → ciphertext**

and then

**Decryption process: ciphertext + decryptiong algorithm + key   → plaintext**

## **3. Symmetric** encryption **vs Asymmetric** encryption

| **Feature** | **Symmetric Encryption** | **Asymmetric Encryption** |
| --- | --- | --- |
| Number of keys | One key for both encrypting and decrypting | Two keys: public and private |
| Key sharing | Both people need the same secret key | Public key can be shared openly |
| Speed | Very fast | Slower (used for small amounts of data) |
| Main use | Encrypting bulk data (files, network traffic) | Sharing keys, securely and digital certificates |
| Analogy | One key locks and unlocks a box | A mailbox: anyone posts, only the owner retrieves |

In practice, **real systems use both**:

- Asymmetric encryption initiates a connection and securely shares a symmetric key.
- Symmetric encryption takes over for the remainder of the session to efficiently handle data.

Asymmetric encryption uses **two mathematically linked keys**:

- A **public key** that anyone can know and use.
- A **private key** that only one person keeps secret.

Here's the clever part:

- If you encrypt something with someone's **public key**, only their **private key** can decrypt it.
- If you encrypt something with your **private key**, anyone with your **public key** can decrypt it (this is primarily used for digital signatures, which we won't delve into here).

**We looked at two flavours of encryption:**

- Symmetric encryption uses a single key for both encryption and decryption. It's fast and efficient, but you need a secure way to share that key. We used the Caesar cipher to see how this works.
- Asymmetric encryption uses two linked keys: a public key that anyone can use and a private key that only one person keeps. This solves the key distribution problem and powers the initial handshake for HTTPS connections.

We also saw how real systems combine both types:

- Asymmetric encryption sets up a shared key at the start.
- Symmetric encryption handles the actual data because it's faster.