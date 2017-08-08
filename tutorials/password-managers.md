## The problem with passwords

Most people use weak passwords, even though they might not realise it. The solution is simple: use strong passwords -- ones that contain both upper and lower case letters, numbers and special characters (!"#$%& etc). So that's the password problem solved, right?

Unfortunately, no. <mark>Password strength isn't the biggest issue. Reusing passwords is.</mark> Odds are you reuse passwords too.

<p align="center"><img alt="People reuse passwords" src="/img/reuse.png"></p>

Your password can be a million characters long, contain all that's mentioned above plus all Greek, Cyrrilic, Chinese and Arabic letters, but still be rendered useless if you use it on more than one website. Many websites don't store passwords securely -- and get hacked. This way, your password can be obtained and whether your password is `123456` or `BbPzgEDpa8bXN8Ftq9MVwWqdSAA3Xn 3595azebav5ZBmEjFzvZjXc6rup2c3 3xbdeDqpNXvf6SaGaHuFTgFufDa3Uj 2N7v2d2e` (without spaces) doesn't matter.

Websites get hacked, passwords get leaked, people get hacked.

So the solution is a unique strong password for each website/service. But how the hell are we supposed to remember all those passwords?

## Password managers

That's what password managers are for. <mark>Password managers are tools that generate and store your passwords.</mark> That way, you can use a unique strong password for each service you use.

But doesn't that create a single point of failure -- how is that different from writing your passwords on a paper? Password managers use encryption, so as long as you use a strong **master** password (the one used for decrypting the password manager's data), you don't have to worry. You might already be using your browser's "Remember password" feature. The issue with that feature is that it's not secure and it doesn't support generating strong passwords. 

## Creating a strong master password

See our other tutorial for [creating strong passwords](creating-strong-passwords.html).

## Choosing the right password manager

There are two kinds of passwords managers: online and local.

The huge advantage of online password managers is that you don't have to store (and backup!) anything on your device. The disadvantage is that you have to trust the provider, since all you see is the user interface -- you have no idea what happens behind the scenes.

Local password managers offer higher security than online password managers, but are far less practical. You need to backup it regularly (every day, or when you add a new password) in order to not lose all your passwords. And because you want to use open-source software, you (can) know exactly what's happening behind the scenes (in practice, you check if it's been audited or just hope it's been peer-reviewed).

However, there's a password manager which doesn't fit into either category. Neither online nor local. It's actually more of an algorithm. It uses your full name and master passwords as a source of randomness (also known as entropy in this context) and generates passwords based on the service name, domain, or whatever you decide to use (for Twitter you might use `twitter` but also `twitter.com`). The downside to this is not having a list of all your accounts, which might actually be a good thing -- it removes the single point of failure thing to some extent.

Now you can decide. It's up to you. Do you need a list of accounts? Do you need maximum security, or prefer usability?

Here's a list of popular password managers for each kind:

- Online: [1Password](https://1password.com/), [LastPass](https://www.lastpass.com/)
- Local: [KeePassX](https://www.keepassx.org/)
- [Master Password](http://masterpasswordapp.com/) -- the password generation algorithm, has many implementations

---

Image source: [xkcd](https://xkcd.com) License: [CC BY-NC 2.5](https://creativecommons.org/licenses/by-nc/2.5/)
