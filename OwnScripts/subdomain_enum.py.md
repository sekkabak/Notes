# subdomain\_enum.py

```python
#!/usr/bin/python3

import requests
import sys

sub_list = open("/home/kali/Downloads/wordlist2.txt").read()
subdoms = sub_list.splitlines()

for sub in subdoms:
    sub_domain = f"http://{sub}.{sys.argv[1]}"

    try:
        requests.get(sub_domain)
    except requests.ConnectionError:
        pass
    else:
        print("Valid domain: ", sub_domains)


```
