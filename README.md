# bloknot `/блокнот/`
لیست دستور‌ها و تقلب‌های کامندلاین (و یه سری ابزار های دیگه)

## bash 

* پروسس های فعال مرتب شده بر اساس مصرف سی پی یو

```shell
ps aux --sort -pcpu | less   
```

* پروسس های فعال مرتب شده بر اساس مموری

```shell
ps aux --sort -pmem | less
```
 
* پروسس هایی که مربوط به فایرفاکس میشن

```bash 
ps aux --sort -pmem | grep "/usr/lib/firefox*" | less 
```

* گزارش از مجموع استفاده یک ابزار مثل فایرفاکس از سی پی یو و مموری . به درصد گزارش شده

```bash
# firefox memory, and cpu usage
#  همین گزارش برای یه ابزار دیگه: فقط قسمت مشخص شده پایین را تغییر بدین
# try another application,                  <------->  change this part
ps aux | awk 'BEGIN {cpu=0;mem=0;i=0} $11 ~ /firefox/ { cpu+=$3;mem+=$4;i+=1; print $2 "\t" $3 "\t" $4 "\t" $11 } END { print "\ncpu\t" cpu "\nmem\t" mem "\ncount\t" i }'
```
```shell
# نمونه خروجی
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
# شبیه دستور بالایی ولی فقط سه تا خط آخر یا همون گزارش و می‌نویسه
ps aux | awk 'BEGIN {cpu=0;mem=0;i=0} $11 ~ /firefox/ { cpu+=$3;mem+=$4;i+=1 } END { print "cpu\t" cpu "\nmem\t" mem "\ncount\t" i }' 
```


## .rc files

### دستور های خلاصه شده برای فایل های آر-سی

* داکر

```shell 
alias d="docker"
alias d-c="docker-compose"
```

* گیت

```shell
alias glog="git log --graph --pretty=format:'%Cred%h%Creset %an: %s - %Creset %C(yellow)%d%Creset %Cgreen(%cr)%Creset' --abbrev-commit --date=relative"
alias glogs="git log --graph --pretty=format:'%>>|(10) %Cred%h%Creset %C(cyan)|%an%Creset: %>>|(40) %Cblue|%cr%Creset %s  %Creset %C(yellow)%d%Creset ' --abbr$
```

* ادیتورها

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


