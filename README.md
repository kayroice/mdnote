# mdnote
Take a note as markdown!


# Usage

## Take a simple note.

```bash
$ ./mdnote -f /tmp/test.md create 
Press CTRL-D (^D) or send 'EOF' to terminate input...
This is the content of the note.
.

$ cat /tmp/test.md
# Sat Jun 09 23:01:48 PDT 2018
------------------------------

```text
This is the content of the note.

```
```

## Take a note with a comment and a custom header.

```bash

$ ./mdnote -f /tmp/test.md create --comment 'This is a comment.' --header comment_usage --noprompt

$ head -5 /tmp/test.md
# comment_usage / Sat Jun 09 23:05:17 PDT 2018
------------------------------

* `comment:` This is a comment.
```

## Take a note using stdin, but don't write to a file using dry-run mode.

```bash
$ /usr/games/fortune | ./mdnote create --dryrun
# Sat Jun 09 23:11:40 PDT 2018
------------------------------

```text
Unknown person(s) stole the American flag from its pole in Etra Park sometime
between 3pm Jan 17 and 11:30 am Jan 20.  The flag is described as red, white
and blue, having 50 stars and was valued at $40.
                -- Windsor-Heights Herald "Police Blotter", Jan 28, 1987

```
```

## Take a note of URLs with a custom header, a comment, and don't prompt the user for input.


```bash
$ ./mdnote -f /tmp/test.md create --header markdown --comment 'Markdown cheatsheet.' --urls https://help.github.com/articles/basic-writing-and-formatting-syntax https://guides.github.com/features/mastering-markdown --tags markdown github --noprompt

$ head -9 /tmp/test.md
# markdown / Sat Jun 09 23:16:01 PDT 2018
------------------------------

* `comment:` Markdown cheatsheet.
* `tags:` markdown github
* `urls:`
    * [https://help.github.com/articles/basic-writing-and-formatting-syntax](https://help.github.com/articles/basic-writing-and-formatting-syntax)
    * [https://guides.github.com/features/mastering-markdown](https://guides.github.com/features/mastering-markdown)

```

## Take a note as yaml.

```bash
$ ./mdnote -f /tmp/test.yaml create --templatefile templates/notes.yaml.j2 --url http://yaml.org https://en.wikipedia.org/wiki/YAML http://www.yamllint.com --tags yaml lint --noprompt --dryrun
- 
    header: 'Sun Jun 10 16:52:54 PDT 2018'
    tags:
        - yaml
        - lint
    urls:
        - http://yaml.org
        - https://en.wikipedia.org/wiki/YAML
        - http://www.yamllint.com

```

## Take a text note.

```bash
$ ./mdnote -v -f /tmp/test.txt create --templatefile templates/notes.txt.j2 --dryrun --tags ascii text --urls https://en.wikipedia.org/wiki/ASCII https://en.wikipedia.org/wiki/Plain_text --dryrun
Press CTRL-D (^D) or send 'EOF' to terminate input...
Take a note as text.
.
# Sun Jun 10 16:58:30 PDT 2018
# Tags: ascii text
# URLs: https://en.wikipedia.org/wiki/ASCII https://en.wikipedia.org/wiki/Plain_text
------------------------------
Take a note as text.
```
