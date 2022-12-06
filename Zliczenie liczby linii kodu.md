### BASH
```bash
find . -name '*.cs' | sed 's/.*/"&"/' | xargs wc -l
```

### PowerShell
```Powershell
(Get-ChildItem -Include *.cs -Recurse | Select-String -pattern .).Count
```