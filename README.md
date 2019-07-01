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

* report: `firefox` cpu, and memory usage (percentage)

```bash
# firefox memory, and cpu usage
# try another application,                  <------->  change this part
ps aux | awk 'BEGIN {cpu=0;mem=0;i=0} $11 ~ /firefox/ { cpu+=$3;mem+=$4;i+=1; print $2 "\t" $3 "\t" $4 "\t" $11 } END { print "\ncpu\t" cpu "\nmem\t" mem "\ncount\t" i }'
```
```shell
# sample output: 
3137	0.8	    3.0     	/usr/lib/firefox-nightly/firefox-bin
10852	0.1	    1.4     	/usr/lib/firefox-nightly/firefox-bin
...
24761	0.9	    4.1     	/usr/lib/firefox-nightly/firefox-bin
30586	0.9	    3.3     	/usr/lib/firefox-nightly/firefox-bin

cpu     20.8
mem     53
count   14
```

```bash 
# less detail, prints last three lines
ps aux | awk 'BEGIN {cpu=0;mem=0;i=0} $11 ~ /firefox/ { cpu+=$3;mem+=$4;i+=1 } END { print "cpu\t" cpu "\nmem\t" mem "\ncount\t" i }' 
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

```shell
alias ssh-modem='ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 admin@192.168.1.1'
```


