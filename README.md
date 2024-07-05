# Password Complexity Evaluator

> [!IMPORTANT]
> Stubbing out a future project. Nothing in this repo works at the moment — they're just notes.

In order to help people identify insecure credentials, my idea for this tool is to be able to read a password/passphrase (as a string), and evaluate its complexity (strength) based on certain criteria.

Scores will have a value between `0` and `1`, and the user of this system should be able to set a complexity threshold for pass/fail evaluations.

* <https://dropbox.tech/security/zxcvbn-realistic-password-strength-estimation>
* <https://www.usenix.org/conference/usenixsecurity16/technical-sessions/presentation/wheeler>
* <https://github.com/nbutton23/zxcvbn-go>

Most of the time, things like "can't be the same as your username" or "MUST have X upper, lower, and symbol characters" are poor substitutes for simply _generating a secure password_. Sometimes you can generate a secure password, and they run afoul of misguided rules like these.

1. The shorter the password, the more complex it needs to be.
1. Expect/pressure/teach users to adopt password managers.
1. Despite the best intentions of [xkcd](https://xkcd.com/936/), we should not be optimizing for human memory.

## Good scores

The human mind is the **worst** place to:

* generate passwords
* store passwords

Once you've taken your brain out of the equation, and started using a password manager to **store** your passwords (as God, Lord Xenu, or the Flying Spaghetti Monster intended), then these become great ways to **generate** secure passwords.

* https://1password.com/password-generator/
* https://sourceforge.net/projects/pwgen/
* https://linux.die.net/man/1/secpwgen

Yes, lots of websites are _awful_ at accepting secure passwords. I often have to _reduce_ complexity or length to make them _less secure_ just so that the website will accept them. And sometimes the client-side evaluation is out-of-sync with the backend validation, meaning that the site will accept a new password on the front-end that the backend fails with.

<https://ryanparman.com/tags/passwords/>

## Poor scores

1. If the password has been in a breach, it gets a score of `0`. Full-stop.
    * https://haveibeenpwned.com/Passwords
    * https://api.pwnedpasswords.com/range/21BD1
    * https://github.com/HaveIBeenPwned/PwnedPasswordsDownloader

1. If the raw password has a high similarity (Levenshtein distance?) to a password on a [top-10-million list](https://github.com/danielmiessler/SecLists/blob/master/Passwords/xato-net-10-million-passwords.txt), it gets a very low score.

1. Determine rules for evaluating [frequently-used words](https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists). This will probably cross paths with "correct horse battery staple".

1. The shorter the password, the more complex it needs to be.
