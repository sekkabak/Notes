### Stabilize Shell

```bash
python3 -c "import pty; pty.spawn('/bin/bash')"
OR
python -c "import pty; pty.spawn('/bin/bash')"
OR
script -q /dev/null -c bash
```



```bash
stty raw -echo && fg
export TERM=xterm
```


```bash
stty rows 26 cols 105
```


```bash
# In reverse shell
$ python -c 'import pty; pty.spawn("/bin/bash")'
Ctrl-Z

# In Kali
$ stty raw -echo
$ fg

# In reverse shell
$ reset
$ export SHELL=bash
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```
