---
title: Shell
---

## File management

```shell
cp -R path/source path/target
```

Copy directories.

```shell
find . -name '.DS_Store' -type f -delete
```

Delete all `.DS_Store` files recursively.

## File management, batching

https://stackoverflow.com/a/24265787

### `find`

Search for files in a directory.

```shell
find <dir> <pattern> <action>
```

For example:

```shell
find . -name \*.jpg -type f -print0
```

- `.` searches current directory (recursively)
- `-name` case sensitive search
- `-iname` case insensitive
- `\*.jpg` pattern (why `\`?)
- `-print0` print filename, for e.g. to use with pipe `|`
- `-exec <command> {};` - `<command> command to run, e.g.`cp`-`{}`gets replaced with current file -`;` terminates command

```shell
find . \( -name \*.jpg -o -name \*.jpeg \) -print0
```

- `-o` for `Or`

```shell
find . -name "*.jpg" -delete
```

- Dedicated `find` flag for deleting files.
- The pattern is quoted here, another alternative is to escape the asterisk as in a previous example

- `-type f` selects files only (also `d` for directory and `l` for symlink)
- `-print0` print filename
- `-exec <command> {};` - `<command> command to run, e.g.`cp`-`{}`gets replaced with current file -`;` terminates command

### `xargs`

Execute commands from standard input. Use `|` to pipe commands to `xargs`.

```shell
find . -name \*.jpg -print0 | xargs -I{} -0 cp -v -f {} /home/dir
```

- `-I{}` replacement string
- `-0` separate items with a null character
- `cp` options: `-v` for Verbose, `-f` for Force`

[find -exec vs find | xargs](https://www.everythingcli.org/find-exec-vs-find-xargs/)

## Practical examples

### Find all video files in a tree

- Just a quick list of video file extensions, not exhaustive.
- Probably not a safe copy, since the original tree may have duplicate file names in different directories, but `cp` will overwrite them and only keep the last one in the flattened target directory.

```shell
find . \( -name \*.webm -o -name \*.mkv -o -name \*.flv -o -name \*.vob -o -name \*.ogv -o -name \*.avi -o -name \*.mov -o -name \*.wmv -o -name \*.asf -o -name \*.mp4 -o -name \*.m4p -o -name \*.m4v -o -name \*.mpeg -o -name \*.mpv -o -name \*.mp2 -o -name \*.3gp -o -name \*.swf \) -print0 | xargs -I{} -0 cp -v -f {} /home/dir
```
