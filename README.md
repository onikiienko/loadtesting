loadtesting
===========


### Устанавливаем yandex-tank

Выполняем команды на выбор:
```bash
deb http://ppa.launchpad.net/yandex-load/main/ubuntu precise main
deb-src http://ppa.launchpad.net/yandex-load/main/ubuntu precise main
```

или так

```bash
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:yandex-load/main

sudo apt-get update && sudo apt-get install yandex-load-tank-base
```
### Настраиваем орудие

Создаем файл с конфигурациями нагрузки, называем его load.ini, файл должен иметь примерно такой вид:

```bash
[phantom]
address = 127.0.0.1
port = 3000
instances = 1000
rps_schedule = const(1,1m) line(2,40,2m) const(40,2m) line(40,2,20m) const(1,1m)
header_http = 1.1
headers = [Host: maps.api.entrances.des.dev.kiev.test]
         [Connection: close]
uris = /2.0/js/?pkg=full
       /2.0/css/?pkg=full
[autostop] autostop = http(5xx,10%,5s)
```
### Начинаем обстрел

Запускаем обстрел, в папке с файлом load.ini выполнямем:
```bash 
yandex-tank
```

### Результаты

После выполнения обстрела будет создана папка с файлами, в ней есть файл формата html, в нем и хранятся результаты.
С сервера на свой комп копировать через scp, примерно так:
```bash
sudo scp -r ./2014-06-13_15-51-00.9zIFj4/*.html  onikiienko@10.110.40.87:~/Projects/
```

Дока по [яндекс-танк](https://yandextank.readthedocs.org/en/latest/tutorial.html)
