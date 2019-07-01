# bloknot `/блокнот/`
list of my cheatsheets, command line hacks, templates, etc. 


## bash 

* current process, sorted by cpu usage. 4 direction navigate via `less`

```shell
ps aux --sort -pcpu | less   
```

* current process, sorted by memory usage. 4 direction navigate via `less`

```shell
ps aux --sort -pmem | less
```
 
* firefox processes sorted by memory. 

```bash 
ps aux --sort -pmem | grep "/usr/lib/firefox*" | less 
```

## .rc files

### aliases

* docker

```shell 
alias d="docker"
alias d-c="docker-compose"
```

* git

```shell
alias glog="git log --graph --pretty=format:'%Cred%h%Creset %an: %s - %Creset %C(yellow)%d%Creset %Cgreen(%cr)%Creset' --abbrev-commit --date=relative"
alias glogs="git log --graph --pretty=format:'%>>|(10) %Cred%h%Creset %C(cyan)|%an%Creset: %>>|(40) %Cblue|%cr%Creset %s  %Creset %C(yellow)%d%Creset ' --abbr$
```

* editors

```shell
alias e='emacs -nw'
alias eo='nano'
alias ex='vim'
alias eg='gedit'
```

* ssh 

```ssh
alias ssh-modem='ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 admin@192.168.1.1'
```


