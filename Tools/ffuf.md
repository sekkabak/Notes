
#### Fuzzowanie subdomen
po pierwszym przejściu dodać przełącznik -fw który filtruje po słowach

```bash
ffuf -u <URL> -w <WORDLIST> -H 'Host: FUZZ.<URL>'
```

```bash

-e '.php, .js' # szuka dla rozszerzeń .php i .js
-replay-proxy  # wysyłą znalezione strony do np burpa
-recursion     # fuzuje też znalezione podkatalogi
-x             # przypuszcza CAŁY ruch przez proxy

```


#### Podstawowe użycie
```bash
ffuf -w /usr/share/wordlists/dirb/big.txt -u "http://$IP/FUZZ" -c
```


### Enumeracja założonych kont
```bash
ffuf -w /usr/share/seclists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=admin%40admin.com&password=123123123&cpassword=123123123" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.94.226/customers/signup -mr "username already exists"

# -X    specyfikacja metody
# -d    podanie payloadu do POST
# -H    podanie headera
# -mr   szukany text w response
```


### Bruteforce logowania
```bash
ffuf -w /tmp/usernames.txt:FUZZ1,/usr/share/seclists/Passwords/Common-Credentials/10-million-passwor
d-list-top-1000.txt:FUZZ2 -X POST -d "username=FUZZ1&password=FUZZ2" -H "Content-Type: application/x-www
-form-urlencoded" -u http://10.10.94.226/customers/login


# można podawać więcej wordlist
```