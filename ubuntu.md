#### [Remove Old Kernels In Ubuntu With One Command when your `/boot` is full](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

* dry-run
```bash
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get --dry-run remove
```

  * site written
```bash
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```

  * mine
```bash
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -v "linux-libc-dev:amd64" | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```
