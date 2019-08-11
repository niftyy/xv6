# xv6 for Mac

## Installation

You should have xcode, macports installed on your machine.

Get macports : https://www.macports.org/

```bash
git clone https://github.com/niftyy/xv6.git
cd xv6
sudo port install qemu
sudo port install i386-elf-gcc gdb
```

## To Run

```
cd xv6
make qemu clean
```
