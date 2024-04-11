# Testing unix and dos files

## Change file endings

### DOS crlf

```console
user@host:~$ unix2dos file_with_crlf.txt
unix2dos: converting file file_with_crlf.txt to DOS format...
```

### UNIX lf

```console
user@host:~$ dos2unix file_with_lf.txt
dos2unix: converting file file_with_lf.txt to Unix format...
```

### Verify file type

```console
user@host:~$ file file_with_crlf.txt
file_with_crlf.txt: ASCII text, with CRLF line terminators
```

```console
user@host:~$ file file_with_lf.txt
file_with_lf.txt: ASCII text
```
