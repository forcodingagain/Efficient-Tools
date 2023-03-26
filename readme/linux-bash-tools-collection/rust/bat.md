---
description: A cat(1) clone with wings.
---

# Bat

## Features

### Syntax highlighting

`bat` supports syntax highlighting for a large number of programming and markup languages

### Git integration

`bat` communicates with `git` to show modifications with respect to the index (see left side bar)

### Show non-printable characters

You can use the `-A`/`--show-all` option to show and highlight non-printable characters

### Automatic paging

By default, `bat` pipes its own output to a pager (e.g. `less`) if the output is too large for one screen. If you would rather `bat` work like `cat` all the time (never page output), you can set `--paging=never` as an option, either on the command line or in your configuration file. If you intend to alias `cat` to `bat` in your shell configuration, you can use `alias cat='bat --paging=never'` to preserve the default behavior.

#### **File concatenation**

Even with a pager set, you can still use `bat` to concatenate files 😉. Whenever `bat` detects a non-interactive terminal (i.e. when you pipe into another process or into a file), `bat` will act as a drop-in replacement for `cat` and fall back to printing the plain file contents, regardless of the `--pager` option's value.

## How to use

Display a single file on the terminal

```bash
> bat README.md
```

Display multiple files at once

```
> bat src/*.rs
```

Read from stdin, determine the syntax automatically (note, highlighting will only work if the syntax can be determined from the first line of the file, usually through a shebang such as `#!/bin/sh`)

```bash
> curl -s https://sh.rustup.rs | bat
```

Read from stdin, specify the language explicitly

```bash
> yaml2json .travis.yml | json_pp | bat -l json
```

Show and highlight non-printable characters

```bash
> bat -A /etc/hosts
```

Use it as a `cat` replacement:

```bash
bat > note.md  # quickly create a new file

bat header.md content.md footer.md > document.md

bat -n main.rs  # show line numbers (only)

bat f - g  # output 'f', then stdin, then 'g'.
```

## Integration with other tools

### **`fzf`**

You can use `bat` as a previewer for [`fzf`](https://github.com/junegunn/fzf). To do this, use `bat`s `--color=always` option to force colorized output. You can also use `--line-range` option to restrict the load times for long files:

```bash
fzf --preview 'bat --color=always --style=numbers --line-range=:500 {}'
```

### **`find` or `fd`**

You can use the `-exec` option of `find` to preview all search results with `bat`:

```bash
find … -exec bat {} +
```

If you happen to use [`fd`](https://github.com/sharkdp/fd), you can use the `-X`/`--exec-batch` option to do the same:

```bash
fd … -X bat
```

### **`ripgrep`**

With [`batgrep`](https://github.com/eth-p/bat-extras/blob/master/doc/batgrep.md), `bat` can be used as the printer for [`ripgrep`](https://github.com/BurntSushi/ripgrep) search results.

```bash
batgrep needle src/
```

**`tail -f`**

`bat` can be combined with `tail -f` to continuously monitor a given file with syntax highlighting.

```bash
tail -f /var/log/pacman.log | bat --paging=never -l log
```

Note that we have to switch off paging in order for this to work. We have also specified the syntax explicitly (`-l log`), as it can not be auto-detected in this case.

### **`git`**

You can combine `bat` with `git show` to view an older version of a given file with proper syntax highlighting:

```
git show v0.6.0:src/main.rs | bat -l rs
```

### **`git diff`**

You can combine `bat` with `git diff` to view lines around code changes with proper syntax highlighting:

```
batdiff() {
    git diff --name-only --relative --diff-filter=d | xargs bat --diff
}
```

If you prefer to use this as a separate tool, check out `batdiff` in [`bat-extras`](https://github.com/eth-p/bat-extras).

If you are looking for more support for git and diff operations, check out [`delta`](https://github.com/dandavison/delta).

### **`xclip`**

The line numbers and Git modification markers in the output of `bat` can make it hard to copy the contents of a file. To prevent this, you can call `bat` with the `-p`/`--plain` option or simply pipe the output into `xclip`:

```bash
bat main.cpp | xclip
```

`bat` will detect that the output is being redirected and print the plain file contents.

### **`man`**
