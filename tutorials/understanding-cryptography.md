## What is cryptography?

According to Wikipedia,
> Cryptography [...] is the practice and study of techniques for secure communication in the presence of third parties called adversaries.

What that means for us is <mark>securing communication (and data) using encryption.

## Encryption

Although today's encryption is extremely complex, utilizing very advanced mathematics, we're lucky as are tools that are relatively easy to use without ANY knowledge of cryptography.

Example: HTTPS (or SSL or TLS) -- like we learned in the [Understanding VPNs](understanding-vpns.html) tutorial -- secures your connection to websites (ones that use it) in a way that makes your activities unreadable to third parties ([adversaries](glossary.html#adversary)). It doesn't require users to do anything whatsoever, yet it protects sensitive data (such as financial information) of millions, if not billions, of users worldwide.

Even though we might not realize it, we use encryption every day -- and it's a crucial part of many systems.

So we know that encryption is basically everywhere around us, being used by providers, for example.

But how can *we* start using encryption (or cryptography, they're synonyms in this context) in order to secure our data? One of the most important ways we can start using encryption is by encrypting our data and communication. There will be big tutorials on these topics later.

## Terminology

However, in order to understand those tutorials, you need to understand some concepts.

### Basic terminology

- **Plaintext** = data before encryption
- **Ciphertext** = data after encryption
- **Key** = data used to convert that specific plaintext to that specific ciphertext. Think of this as the password.

### Symmetric-key encryption

The same key is used for encryption and decryption -- as you'd expect encryption to work.

### Asymmetric-key (Public-key) encryption

Now, this is where it gets interesting. Public key cryptography utilizes **two** keys. One for encryption and one for decryption.

- **Public key** = the key used for encryption. Why is it called public? Simple. You can share it publicly without exposing yourself to any risk. People will use this to encrypt, say, the emails they want to send you.
- **Private key** = the key used for decryption. You guessed it -- it's called private, because only you should posses it. You'll use this to decrypt the messages that are encrypted with your public key.

Let's say we have a plaintext: `HELLO THERE!`. We encrypt it using an encryption key called **public key**: `PUBKEY`. We get a ciphertext: `AZPHXYRHV`. If we try to decrypt it with the **public key**, we get `KXELCVQNU` -- just a bunch of random letters. But we also know the **private key** -- the key used for decryption: ``PRIVKEY``. If we decrypt ``AZPHXYRHV`` with ``PRIVKEY``, we get ``HELLO THERE!``. Neat, isn't it?
