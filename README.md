# Testing unix and dos files

Line terminators are the invisible symbols that are used by the operating system to represent a new line. Windows and UNIX operating systems use different sequences that can lead to inconsistencies when working with different operating systems. In an effort to keep things consistent, create a file named .gitattributes in the root of your repository.

```console
user@host:~$ cat .gitattributes
* text=auto eol=lf
```

After creating and committing the .gitattributes file to the repository run the following command to update the files in the repository.


```console
user@host:~$ git add --renormalize .

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

##### Install pre-commit hook to remove crlf

```console
user@host:~$ cat .pre-commit-config.yaml
---
fail_fast: true
repos:
  - repo: https://github.com/Lucas-C/pre-commit-hooks
    rev: v1.5.5
    hooks:
      - id: remove-crlf
```

##### Manually run pre-commit to remove crlf

```console
user@host:~$ pre-commit run --all-files
CRLF end-lines remover...................................................Failed
- hook id: remove-crlf
- exit code: 1

Removing CRLF end-lines in: file_with_crlf.txt

CRLF end-lines have been successfully removed. Now aborting the commit.
You can check the changes made. Then simply "git add --update ." and re-commit
```

* Reference

[GitHub article describing the purpose of the .gitattributes file](https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings).

[YouTube Video by ASCODE explaining the trouble with line endings](https://www.youtube.com/watch?v=zn7m2Mdm_Vg)

[Line Ending Article](https://www.aleksandrhovhannisyan.com/blog/crlf-vs-lf-normalizing-line-endings-in-git/)
