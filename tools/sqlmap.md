### sqlmap

```bash
-u                        # url jaki testujemy
--data='DATA'             # jeśli sprawdzamy request POST to tutaj podajemy payload
--cookie='PHPSESSID=abcd' # potrzebne nam cookiesy
--level={}                # [1-5] level testów
--risk={}                 # [1-3] level ryzyka np (wywalenie bazy niechcący :)  )
--threads={}              # wątki ;3
-r {}                     # podanie pliku requesta np z burpa
--batch                   # zawsze wybiera domyślną opcje
--dbms {}                 # wskazanie z jaką bazą mamy doczynienia
--dbs                     # enumeruje bazę danych
--users                   # enumeruje userów silnika bazodanowego
--current-user            # zwraca aktualnie uzywanego usera
--file-read=FILE          # próbuje pobrać plik z atakowanego systemu
--file-write=FILE         # próbuje zapisać plik na dysku
-D {}                     # wybranie bazy
-T {}                     # wybranie tabeli
--tables                  # enumeruje tabele aktualnej bazy danych
--columns                 # enumeruje kolumny aktualnej bazy
```

