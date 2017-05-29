## What is a VPN?

Before we explain what [VPNs](glossary.html#vpn) are, let's talk about Internet without them.

Your [ISP](glossary.html#isp) (Internet Service Provider) can see everything you do online. Well, nearly -- when websites use **HTTPS/SSL/TLS** (these terms are used interchangeably when talking about websites, they all mean "website encryption"), indicated by that green padlock, your ISP cannot see *exactly* what you're doing on the websites, but can still see what websites you're browsing.

That sounds bad, right? But that's not even the worst part. (*WHAT??!!* -- I know, right?) Not only can your ISP see what you're doing online, they can (and do) insert ads into websites, sell your browsing history (which is now legal in the US), restrict access to some websites and other awful stuff -- because **they have complete control over your Internet connection**.

Fortunately, more and more websites are starting to use HTTPS, but many still don't, and even HTTPS doesn't solve the problem that your ISP can see what websites you're browsing.

## How VPNs can protect us

Luckily, there are VPNs. VPN stands for Virtual Private Network. It secures your Internet connection. How does it work? Instead of letting your ISP see everything you do online, VPNs only let them see that you're connected -- **using an encrypted connection** -- to their servers.

<mark>Basically, instead of connecting directly to the Internet, you connect to one of your VPN providers' servers which connects you to the Internet.</mark>

So `you <----> Internet` becomes `you <----> VPN <----> Internet` and your ISP can only see the `you <----> VPN` part.

## More ways VPNs can protect us

So VPNs are practically awesome, but that's not all, not by far.

Did you know that [if you're on an insecure Wi-Fi network](wifi-security.html), **anyone connected to the same network can see as much as your ISP can?**

Obviously, this isn't an issue at home, unless you have very creepy neighbours and [not-a-very-secure Wi-Fi network](wifi-security.html). However, it is a problem in public places with Wi-Fi, such as cafés.

Since your connection to the VPN is **secure** and **it's the only active connection** on your device, that creepy guy with the laptop sitting in the corner is no longer a threat to your Internet connection.

So, is that all? Not yet. There's still one big advantage. Websites that you're connected to can see this (usually) near-unique identifier, called an **IP address**. But when you use a VPN, the websites don't see your IP address; they see one of the VPN's server's IP address.

This also provides an added side-benefit.  Most VPN providers have servers in many countries -- thus you can make it seem like you're from a completely different country (which, apart from privacy, is useful due to some content and services being available only to specific regions -- like Netflix and Hulu).

But even if you use a different IP address than your "normal" one, isn't it still personally identifiable? Nope. Many people use the same server, letting the websites you visit see only that you're using the same VPN as many other people.

So, now that we understand what a VPN is, how do we choose one? Read our next tutorial, [Choosing a VPN](choosing-a-vpn.html).
