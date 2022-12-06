## Formatting JSON
```vim
:%!python -m json.tool
```

## Clear registers
```vim
qaq
```

## Copy to system clipboard by pattern
```vim
:g/pattern/y A
:let @+ = @a
```

## Replace by pattern
```
pattern that you want to replace -> p1
pattern that you want to put where p1 is find -> p2
you can also leave p2 empty ;)
```
```vim
:1,$s/p1/p2/g
```

## Copy all text from file to system clipboard
```vim
:%y+
```

## Delete all lines that not match given pattern
```vim
:v/pattern/d
```

## Remove double "enters"|"new lines"
```vim
:g/^$/d
```


