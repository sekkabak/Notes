- fast TCP/UDP tunnel over HTTP written in go

program który ściągamy z githuba w postaci binarki do poruszania się po przejętych maszynach np do intranetu


użycie:
```bash

./chisel server -p 8001 --reverse
./chisel client 10.10.10.1:8001 R:socks

```


