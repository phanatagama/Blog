---
layout: post
published: true
title: Securinets-2K20 PreQuals
date: '2020-03-22'
image: /img/securi.png
---
Another long run of a 24hrs CTF.
My Team ByteForc3 ended 15th (too good) overall :). It was a gr8 CTF.

![back](/img/securinets/back.png)

Here are some of the challs:

### Forensics
1. ### Time Matters
2. ### Time Problems




## Time Matters
![timem01](/img/securinets/timem01.png)

A simple (yet it took our 1337 time) memory forensics challenge. Fired up volatality and ran a profile scan.
![timem02](/img/securinets/timem02.png)

`Win7SP1x86`

Next ran a pslist scan but no suspicious processes were found except for a bunch of chrome.exe's. 

`python2 vol.py --plugins=plugins/ -f ../for1.raw --profile=Win7SP1x86 pslist`

A filescan lead to some interesting files and reference.

![timem03](/img/securinets/timem03.png)


However there were a lot of files but only two things caught us:

```
0x000000001e24bcd0      2      1 R--rwd \Device\HarddiskVolume2\Users\studio\Desktop\steghide
0x000000001e45e730      8      0 R--rwd \Device\HarddiskVolume2\Users\studio\Desktop\DS0394.jpg
```

Meaning , a JPEG and a steghide who doesn't love that.

Dumping the jpeg with:
```
python2 vol.py --plugins=plugins/ -f ../for1.raw --profile=Win7SP1x86 dumpfiles -Q 0x000000001e45e730 --dump-dir .
```
It was a pic of Leonel Messi with a date reference in the right corner(:at the end of the movie).

`29/08/2019`


So from here it was simple, the only thing that was left was password. So the password actually pushed us into some deep rabbit holes.
First a try of strings on the dump (n00b approach) revealed nothing.
Then we extracted the NTLM hashes and tried to crack it but no Luck :(
So on waiting and thinking and talking to admin , we end up using Mimikatz the infamous Red-Team Dagger. (Ofcourse we were stupid enough not to think this before).

![time04.png](/img/securinets/time04.png)

& yea in no time our password was right there.
`Messi2020`

But wait , Steghide did'nt like the password and so here came the date reference at the bottom right corner of image. (29/08/2019). So Changing the `Messi2020` to `Messi2019` gave us our pretty flag.

![timem05](/img/securinets/timem05.png)

.



