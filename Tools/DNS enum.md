# DNS enum

Znajdzie pliki pomocne do enumeracji subdomen/vhostów na atakowanej maszynie

```shell
locate subdomains
```

#### wfuzz

```bash
sudo wfuzz -c -f result.txt -Z -w /usr/share/dnsrecon/subdomains-top1mil-5000.txt --sc 200,202,204,301,307,403 -H "Host: FUZZ.<targetURL>" <targetURL>
```
