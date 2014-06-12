loadtesting
===========

https://yandextank.readthedocs.org/en/latest/intro.html

For instance, add following repos to sources.list :

deb http://ppa.launchpad.net/yandex-load/main/ubuntu precise main
deb-src http://ppa.launchpad.net/yandex-load/main/ubuntu precise main

or this way

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:yandex-load/main

Then update package list and install yandex-load-tank-base package:

sudo apt-get update && sudo apt-get install yandex-load-tank-base
