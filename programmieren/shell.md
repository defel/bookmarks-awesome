# Shell

* [Explain Shell](http://explainshell.com/) - Zeigt für ein Shell Kommando die Hilfe Texte der Argumente an
* [Shell Check](http://www.shellcheck.net/) - Linter für Shell Skripte
* [Tricks - must read](http://cfenollosa.com/misc/tricks.txt)

## Utilities

* [peco](https://github.com/peco/peco) - Simplistic interactive filtering tool
* [homesick](https://github.com/technicalpickles/homesick) - Your home directory is your castle. Don't leave your dotfiles behind.
  * [Never Leave Your Dotfiles Behind Again With Homesick](http://technicalpickles.com/posts/never-leave-your-dotfiles-behind-again-with-homesick/)

## sed

* [sed tutorial](http://www.grymoire.com/Unix/Sed.html)

## tricks
see http://cfenollosa.com/misc/tricks.txt

### shell builtins

> Search in backwards in history as you type
```
CTRL r
```


> Input from the commandline as if it were a file
```bash
# write:
command <<< "some input text"
# instead of:
command < file.in
```

---
> **^** is a sed-like operator to replace chars from last command
```sh
ls docs
^docs^web^
# is equal to:
ls web
```

---
> **!!** expands to the last typed command.
```bash
cat /etc/...
# [permission denied]
sudo !!
```

---
> **!!:n** selects the nth argument of the last command, and **!$** the last arg
```bash
# shows all files and cats only 1 and 2
ls file1 file2 file3
cat !!:1-2'
```

---
> fetch the last parameter of the previous command
```
ESC .
```
- Related, include 'shopt -s histverify histreedit' on your .bashrc to
  double-check all expansions before submitting a command

---
> More inline substitutions:
> - [8 Bash Tricks you should know](http://linuxers.org/article/10-bash-shortcuts-you-should-know)
> - [bash history expansion](https://news.ycombinator.com/item?id=5338321)

---
> leave stuff in background even if you logout
```bash
nohup ./long_script &
```

---
> nohup ./long_script &
```bash
cd -
```

---
> opens an editor to work with long or complex command lines
```
ctrl-x ctrl-e
```

---
> Use traps for cleaning up bash scripts on exit
- [How "Exit Traps" Can Make Your Bash Scripts Way More Robust And Reliable](http://redsymbol.net/articles/bash-exit-traps/)

---
> automatically fixes your 'cd folder' spelling mistakes
```bash
shopt -s cdspell
```

---
> Add this in your **~/.inputrc** to use the vi keybindings
  for bash and all readline-enabled applications (python, mysql, etc)
```
set editing-mode vi
```

---
> Aggregate history of all terminals in the same .history. On your .bashrc:
```bash
shopt -s histappend
export HISTSIZE=100000
export HISTFILESIZE=100000
export HISTCONTROL=ignoredups:erasedups
export PROMPT_COMMAND="history -a;history -c;history -r;$PROMPT_COMMAND"
```

---
> Freeze Terminal
```
CTRL s
```
> Unfreeze Terminal
```
CTRL Q
```

---
> Pseudo aliases for commonly used long commands
``` bash
function lt() { ls -ltrsa "$@" | tail; }
function psgrep() { ps axuf | grep -v grep | grep "$@" -i --color=auto; }
function fname() { find . -iname "*$@*"; }
function remove_lines_from() { grep -F -x -v -f $2 $1; }
  removes lines from $1 if they appear in $2
alias pp="ps axuf | pager"
alias sum="xargs | tr ' ' '+' | bc" ## Usage: echo 1 2 3 | sum
function mcd() { mkdir $1 && cd $1; }
```

### vim

---
> activate vim spellchecker
```
:set spell
```
> Navigate with `]s` and `[s` between errors, use `zg` to add to dictionary, and `z=` suggets correctly spelled words

---
> check this vimrc to learn more:
* https://github.com/cfenollosa/dotfiles/blob/master/.vimrc

### Tools

---
> Use `htop` instead of `top`

---
> `ranger` is a nice console file manager for vi fans

---
> to see which package provides that file you're missing
```
apt-file
```

---
> `trash-cli` sends files to the trash instead of deleting them forever.
  Be very careful with `rm` or maybe make a wrapper to avoid deleting '\*' by accident (e.g. you want to type `rm tmp*` but type `rm tmp *`)

---
> `file` gives information about a file, as image dimensions or text encoding

---
> check for duplicate lines
```
sort -u
```

---
> starts a command at the specified time
```bash
echo start_backup.sh | at midnight
```

---
> Pipe any command over `column -t` to nicely align the columns

---
> Google 'magic sysrq' to bring a Linux machine back from the dead
```bash
CTRL+ALT+SysRq reisub
# unRaw      (take control of keyboard back from X),
# tErminate (send SIGTERM to all processes, allowing them to terminate gracefully),
# kIll      (send SIGKILL to all processes, forcing them to terminate immediately),
#  Sync     (flush data to disk),
#  Unmount  (remount all filesystems read-only),
reBoot.
```

---
> to see a nice diff
```
code
```

---
> template
```
code
```

---
> template
```
code
```

---
> template
```
code
```



### text manipulation

> get first column of output
```sh
echo "aaa bbb ccc" | cut -f1
```

---
> template
```
code
```
