# To change the hostname on ubuntu 16
https://askubuntu.com/questions/9540/how-do-i-change-the-computer-name
You need to edit the computer name in two files:
```
/etc/hostname
```
and
```
/etc/hosts
```
Replace any instances of the existing computer name with your new one. When complete run
```
sudo service hostname start
```
