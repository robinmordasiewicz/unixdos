# Testing unix and dos files

Line terminators are the invisible symbols that are used by the operating system to represent a new line. Windows and UNIX operating systems use different sequences that can lead to inconsistencies when working with different operating systems. In an effort to keep things consistent, create a file named .gitattributes in the root of your repository.

```console
user@host:~$ cat .gitattributes
* text=auto eol=lf
```

### Testing file line endings

#### Change file endings

##### DOS crlf

```console
user@host:~$ unix2dos file_with_crlf.txt
unix2dos: converting file file_with_crlf.txt to DOS format...
```

##### UNIX lf

```console
user@host:~$ dos2unix file_with_lf.txt
dos2unix: converting file file_with_lf.txt to Unix format...
```

##### Verify file type

```console
user@host:~$ file file_with_crlf.txt
file_with_crlf.txt: ASCII text, with CRLF line terminators
```

```console
user@host:~$ file file_with_lf.txt
file_with_lf.txt: ASCII text
```

* Reference

[GitHub article describing the purpose of the .gitattributes file](https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings).

[YouTube Video by ASCODE explaining the trouble with line endings](https://www.youtube.com/watch?v=zn7m2Mdm_Vg)
