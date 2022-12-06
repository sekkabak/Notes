# ssh

### dodawanie algorytmów do komend

```bash
ssh -o kexalgorithms    # dodaje algorytmy które ssh możę użyć
```

### dodawanie algorytmów do configa ... przydaje się np przy bruteforce

```bash
	~/.ssh/config    # ścieżka
```

```
Przykładowa zawartość
```

```bash
Host 10.10.10.7
	KexAlgorithms ...
	HostKeyAlgorityms ...
```
