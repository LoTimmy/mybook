
![](http://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Gnupg_logo.svg/200px-Gnupg_logo.svg.png)

```
shell> apt-get install rng-tools
shell> rngd -r /dev/urandom
```

Generating a new keypair

```
shell> gpg --gen-key
```    
```
gpg (GnuPG) 1.4.12; Copyright (C) 2012 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection?
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048)
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 
Key does not expire at all
Is this correct? (y/N) y
You need a user ID to identify your key; the software constructs the user ID
from the Real Name, Comment and Email Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Real name:
Email address: myname@example.com
Comment: 
You selected this USER-ID:
    "Timmy Lo <myname@example.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
You need a Passphrase to protect your secret key.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.

Not enough random bytes available.  Please do some other work to give
the OS a chance to collect more entropy! (Need 284 more bytes)
    
```


```
shell> gpg --list-keys
```

Exporting a public key
```
shell> gpg --armor --output   --export
gpg --output alice.gpg --export myname@example.com
```

 
gpg --armor --output ~/your_name_public_key.asc --export your@email.address



----------
[GnuPG](http://zh.wikipedia.org/wiki/GnuPG)
[https://www.gnupg.org/gph/en/manual/c14.html](https://www.gnupg.org/gph/en/manual/c14.html)
[https://www.gnupg.org/gph/en/manual/x56.html](https://www.gnupg.org/gph/en/manual/x56.html)