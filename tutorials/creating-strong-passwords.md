## Introduction

Strong passwords don't necessarily have to be **hard** to remember, but it's still a trade-off to some extent. How secure your password has to be depends on your [threat model](threat-models.html). The reason is simple. While all methods we recommend are secure enough to protect you against attackers not targeting anyone in particular, but rather a mass of users, some may need much higher protection.

Note that the strength of your password doesn't matter if you use it on all websites you have an account on, so be sure to use a [password manager](password-managers.html).

### Which method should *you* use?

| Method                        | Example password | Pros/Cons | Threat model
| ----------------------------- | -------- | --------- | ------
| **Diceware** | `dismount example spinner skirt clothing camper` | + Relatively easy to remember<br>- Not as secure as the other methods | Attackers targetting a mass of users; non-government attackers targetting you in specific
| **Enhanced Diceware** | `Dismou51#eXamp52$spInn53%skI54^cloThi55&Camp` | + Easier to remember than Schneier's method<br>+ Strength comparable to Schneier's method | Government-level attackers
| **Schneier's method**             | `uTVM,TPw55:utvm,tpwstillsecure` | + Strong enough even against government-level attackers<br>- Harder to remember | Government-level attackers

## Diceware

Roll five dice all at once, write down the numbers (`35162`), look up the corresponding word (`35162	john`) in [EFF](https://eff.org)'s long [diceware list](https://www.eff.org/files/2016/07/18/eff_large_wordlist.txt), write it down, repeat until you have at least six words. Then just come up with a mnemonic to remember it -- might be something like a one-sentence story.


[![Comic about password strength](https://imgs.xkcd.com/comics/password_strength.png)](https://www.xkcd.com/936/)

Note: Although the comic isn't wrong, using *common* words isn't good *enough*.

To give you an idea of how secure mere words are, consider this: 

1. four-character password consisting of letters and numbers (we refer to these as alphanumberic passwords) can be cracked pretty easily, since there are only `(26+10)^4` combinations (`1679616` -- might seem like a lot, but at 1000 tries per second, which is far less than what computers are nowadays capable of, going through all combinations will only take slightly less than 28 minutes)
2. password consisting of four of the 1000 most common words has `1000^4 = 1000000000000` combinations, over 595374 times more combinations than the four-character password.

The reason why using a mere word isn't much more secure than using a single letter is that random-looking passwords are cracked using **brute force attacks** -- checking every single option for every single character -- while common passwords, like one-word passwords are cracked using **dictionary attacks** -- going through the list of most common passwords.

## Enhanced Diceware

1. Use the Diceware method to generate random words. Maybe remove some amount of letters (i.e. `dismount` -> `dismou`; `clothing` -> `clothi`)? Maybe capitalize some letters?
2. Put consequent numbers between them. Ideally not 1234..., but take some **random** number you'll remember and then just keep incrementing ("increasing") it.
3. Add special characters
4. (Optional) Add non-English characters if the password manager allows them.
 
If you aren't concerned about anyone targetting you *in specific*, you can use this method with some short text (like a poem) instead of the words, and, say, your birthdate instead of the random number.

## Schneier's method

The Schneier's method is what you should use if there's a reason why you might be specifically targeted by a sophisticated attacker, or just want to go the extra mile for better security.

> My advice is to take a sentence and turn it into a password. Something like "This little piggy went to market" might become "tlpWENT2m". That nine-character password won't be in anyone's dictionary. Of course, don't use this one, because I've written about it. Choose your own sentence -- something personal.
>
> Here are some examples:
> 
> * WIw7,mstmsritt... = When I was seven, my sister threw my stuffed rabbit in the toilet.
> * Wow...doestcst = Wow, does that couch smell terrible.
> * Ltime@go-inag~faaa! = Long time ago in a galaxy not far away at all.
> * uTVM,TPw55:utvm,tpwstillsecure = Until this very moment, these passwords were still secure.
> 
> You get the idea. Combine a personally memorable sentence with some personally memorable tricks to modify that sentence into a password to create a lengthy password. Of course, the site has to accept all of those non-alpha-numeric characters and an arbitrarily long password. Otherwise, it's much harder.

[Original post on Bruce Schneier's blog](https://www.schneier.com/blog/archives/2014/03/choosing_secure_1.html)