to taki fajny interfejs którego można używać przed nmapem
więc można wynik z rustscana przekierować do dokładnego sprawdzenia w nmapie


#### Zwykłe przeskanowanie hosta
```bash
rustscan -a <IP> --script none
```


#### Wrzucenie nmapa na znalezione porty z przełącznikami -sC -sV
```bash
rustscan -a <IP> -p <PORTS> -- -sC -sV
```

```bash
rustscan -a <IP> -r 1-65000 -- -sC -sV
```

#### Przyśpieszenie
```bash
--ulimit 5000
```

