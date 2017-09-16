## What is GPG

GPG is a command-line encryption tool that follows the [OpenPGP](glossary.html#pgp) standard (but supports other encryption schemes as well). It was developed to replace Symantec's PGP cryptographic software suite. It's one of the most commonly used OpenPGP implementations.

Before reading this tutorial, make sure you [understand PGP](pgp.html).

## How to use GPG

This section explains the most important functions of GPG.

### Listing stored keys

To list all **public** keys stored in your [keyring](glossary.html#keyring), use `gpg --list-keys`.

<!-- For some reason, using ``` for code blocks broke the formatting. TODO: Fix this sometime. -->

<pre>
$ gpg --list-keys
/home/user/.gnupg/pubring.gpg
-----------------------------
pub   4096R/54DDD393 2014-06-27
uid                  VeraCrypt Team &lt;veracrypt@idrix.fr&gt;

pub   3072R/6091B1F8 2016-08-09
uid                  Nadim Kobeissi &lt;nadim@nadim.computer&gt;
sub   3072R/A4D437B0 2016-08-09

pub   4096R/CD994F73 2015-08-14 [expires: 2017-07-15]
uid                  Micah Lee &lt;micah@micahflee.com&gt;
uid                  Micah Lee &lt;micah@freedom.press&gt;
uid                  Micah Lee &lt;micah.lee@theintercept.com&gt;
uid                  Micah Lee &lt;micah@firstlook.org&gt;
uid                  Micah Lee &lt;micah.lee@firstlook.org&gt;

pub   4096R/58ACD84F 2015-01-18 [expires: 2018-01-11]
uid                  Tails developers (offline long-term identity key) &lt;tails@boum.org&gt;
uid                  Tails developers &lt;tails@boum.org&gt;
sub   4096R/752A3DB6 2015-01-18 [expires: 2018-01-11]
sub   4096R/2F699C56 2015-01-18 [expires: 2018-01-11]
sub   4096R/A0EDAA41 2016-08-30 [expires: 2018-01-11]
</pre>

Each "block" of text, separated by a blank line, represents one key. (todo block?)

> pub   **4096**R/**54DDD393** **2014-06-27**

The `pub` means it's a public key, the `4096` is the bit length (how many bits of randomness the key consists of), the `54DDD393` is the Key-ID and the `2014-06-07` is the date the key was generated on.

The `uid` stands for User ID. A User ID is the name/email (and comment) info --- for example `The Privacy Guide (admin) <admin@theprivacyguide.org>`. A key can have multiple Key IDs, as you can see on Micah Lee's public key.

Finally, the `sub` stands for *subkey*. You don't need to worry about this and it's a little complex, so I won't explain it here. If you want some information on subkeys, see these links: [[1]](https://lists.gnupg.org/pipermail/gnupg-users/2011-January/040437.html) [[2]](https://superuser.com/questions/632375/why-does-gpg-pgp-by-default-use-different-keys-for-signing-encryption) [[3]](https://security.stackexchange.com/questions/43590/pgp-why-have-separate-encryption-subkey). 

---

To list all **private** keys stored in your keyring, use `gpg --list-secret-keys`.

<pre>
[user@vault ~]$ gpg --list-secret-keys 
/home/user/.gnupg/secring.gpg
-----------------------------
sec   4096R/4412E912 2017-05-22
uid                  The Privacy Guide &lt;admin@theprivacyguide.org&gt;
ssb   4096R/CC84135D 2017-05-22
</pre>

The `sec` means that it's a private (*secret*) key and the `ssb` is basically the same as `sub`, but for private keys.


### Generating a key

To generate a new key(pair), use `gpg --gen-key`.

(Filled-in values are in **bold and *italic***.)

<pre>
$ gpg --gen-key 
gpg (GnuPG) 1.4.21; Copyright (C) 2015 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? <b><i>1</i></b>
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) <b><i>4096</i></b>
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) <b><i>0</i></b>
Key does not expire at all
Is this correct? (y/N) <b><i>y</i></b>

You need a user ID to identify your key; the software constructs the user ID
from the Real Name, Comment and Email Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Real name: <b><i>The Privacy Guide</i></b>
Email address: <b><i>admin@theprivacyguide.org</i></b>
Comment: <b><i>admin</i></b>
You selected this USER-ID:
    "The Privacy Guide (admin) <admin@theprivacyguide.org>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? <b><i>O</i></b>
You need a Passphrase to protect your secret key.

<b><i>[enter password]</i></b>

We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
+++++
...+++++
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
..............................+++++
....+++++
gpg: key 4412E912 marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
pub   4096R/4412E912 2017-05-22
      Key fingerprint = AE9B 418A 72B2 D4A7 3BEA  F402 90BD 83DE 4412 E912
uid                  The Privacy Guide (admin) <admin@theprivacyguide.org>
sub   4096R/CC84135D 2017-05-22
</pre>

### Generating a revocation certificate

To generate a revocation certificate, use `gpg --gen-revoke`.

(Filled-in values are in **bold and *italic***.)

<pre>
$ gpg --gen-revoke admin@theprivacyguide.org

sec  4096R/4412E912 2017-05-22 The Privacy Guide &lt;admin@theprivacyguide.org&gt;

Create a revocation certificate for this key? (y/N) <b><i>y</i></b>
Please select the reason for the revocation:
  0 = No reason specified
  1 = Key has been compromised
  2 = Key is superseded
  3 = Key is no longer used
  Q = Cancel
(Probably you want to select 1 here)
Your decision? <b><i>0</i></b>
Enter an optional description; end it with an empty line:
> <b><i>[enter]</i></b>
Reason for revocation: No reason specified
(No description given)
Is this okay? (y/N) <b><i>y</i></b>

You need a passphrase to unlock the secret key for
user: "The Privacy Guide &lt;admin@theprivacyguide.com&gt;"
4096-bit RSA key, ID 4412E912, created 2017-05-22

ASCII armored output forced.
Revocation certificate created.

Please move it to a medium which you can hide away; if Mallory gets
access to this certificate he can use it to make your key unusable.
It is smart to print this certificate and store it away, just in case
your media become unreadable.  But have some caution:  The print system of
your machine might store the data and make it available to others!
-----BEGIN PGP PUBLIC KEY BLOCK-----
Comment: A revocation certificate should follow

[... the revocation certificate ...]

-----END PGP PUBLIC KEY BLOCK-----
</pre>

### ASCII mode

Since PGP can operate both in ASCII mode and "raw" mode, it's important to understand when to use which one.

When sending something that will be viewed as text (i.e. an email), you should use ASCII mode. On the other hand, when sending a file, you can (and should, it will make the encrypted file smaller) use the default non-ASCII mode.

To operate in ASCII mode, use the `--armor` (or `-a`) switch.

### Encrypting files

To encrypt a file in GPG, use the `--encrypt` (or `-e`) switch. Note that you have to specify the recipient as well --- so GPG knows which public key to use. To do that, use the `--recipient` (or `-r`) switch.

`$ gpg --encrypt --recipient RECIPIENTS_EMAIL FILE_NAME` or
`$ gpg -e -r RECIPIENTS_EMAIL FILE_NAME`

#### Symmetric cryptography

To encrypt something using [symmetric cryptography](glossary.html#symmetricCrypto), use the `--symmetric` (or `-c`) option.

`$ gpg -c FILE_NAME` and you'll be prompted for the password (the key).

### Encrypting messages

To encrypt a message (for example, an email), you can either save it into a file and then encrypt it, or you can pipe `echo`'s output to `gpg`.

Example:

```
echo """Hello
World""" | gpg -a -e -r RECIPIENTS_EMAIL
```

### Selecting Key ID

If you use multiple keys, you need to specify which key to use for signing and decrypting. You can do this by using the `--local-user` (or `-u`) switch along with the email or Key-ID you want to use. 

`$ gpg -a -e -s -u MY_EMAIL -r RECIPIENTS_EMAIL FILE_NAME` or
`$ gpg -d -u MY_UID FILE_NAME`

### Signing files

To sign files, use the `--sign` (or `-s`) switch.

`$ gpg -s FILE_NAME` or to encrypt it as well
`$ gpg -e -s -r RECIPIENTS_EMAIL FILE_NAME`

### Signing messages

Same as encrypting messages, but using the `--sign` (or `-s`) switch.

`$ gpg -s FILE_WITH_MESSAGE` or
`$ echo "Hello World" | gpg -s`

### Decrypting

To decrypt files (or messages --- again, either by using pipe or saving it into a file), you can use the `--decrypt` (or `-d`) switch, or no switch at all --- it's the default option.

`$ gpg FILE_NAME` or
`$ gpg -d FILE_NAME`

You will be prompted for the password.

### Fingerprints

To find the fingerprint of a key, use the `--fingerprint` option.

```
$ gpg --fingerprint admin@theprivacyguide.org
pub   4096R/4412E912 2017-05-22
      Key fingerprint = AE9B 418A 72B2 D4A7 3BEA  F402 90BD 83DE 4412 E912
uid                  The Privacy Guide <admin@theprivacyguide.org>
sub   4096R/CC84135D 2017-05-22
```

### Verifying files

When you're verifying files, you have two files: the file you want to verify and the file with the signature. Generally, the signature file's name is the same as that of the file you want to verify, but with `.pgp` or `.pgp` (or something like that) after it. Make sure both files are in the same directory.

To verify a file, simply run `$ gpg --verify filename` in the directory with both files.
