### Python2 
```bash
python2 -m SimpleHTTPServer 8080
```

### Python3
```bash
python3 -m http.server 9999
```

```bash
sudo python3 -m http.server 80
```


można też od razy podać folder ale trzeba mieć tam READ
| Opcja          | Działanie                                         |
| -------------- | ------------------------------------------------- |
| -m http.server | podajesz port                                     |
| --bind         | podajesz interfejs                                |
| -d             | podajesz katalog w jakim ma serwer serwować pliki |

```bash
sudo python3 -m http.server 80 --bind '127.0.0.1' -d /web
```