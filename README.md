1. Вопрос по Ansible. Надо запускать Ansible через Bastion или локальный хост?
2. Через Bastion не получается зайти в ВМ, запрашивается пароль даже при явном указании ключа, но доступ к машинам ВМ1, ВМ2 и еlastic имеется через команду:ssh -v -o ProxyCommand='ssh -W %h:%p -q fox@51.250.37.254 -i cat' fox@10.1.0.10 -i cat, с локального хоста, к остальным ВМ (kibana.zabbix) подключаться не удается.
3.Вопрос по мессенджеру loop, я так понимаю чат группы Sys-32 уже не работает. Получается все возникающие вопросы надо отправлять именно таким способом?
Запуск с локального хоста![alt text](https://github.com/sAslank/-/blob/main/img/к%20дип.jpg)


Это то как он зависает при попытке подключения к ВМ (kibana.zabbix.)![alt text](https://github.com/sAslank/-/blob/main/img/дип1.jpg)

Через Bastion попытка подключения к вм1, создал ключ установил права chmod 600 ![alt text](https://github.com/sAslank/-/blob/main/img/дип2.jpg)

Файл hosts выглядит след образом:

[web_servers]

web-1 ansible_host=web-1.ru-central1.internal ansible_ssh_user=fox ansible_ssh_private_key_file=/home/fox/obraz/cat #проверочная настройка

web-2 ansible_host=web-2.ru-central1.internal ansible_user=fox ansible_python_interpreter=/usr/bin/python3

[zabbix]

zabbix ansible_host=zabbix.ru-central1.internal ansible_user=fox ansible_python_interpreter=/usr/bin/python3


[elasticsearch]

elasticsearch ansible_host=elasticsearch.ru-central1.internal ansible_user=fox ansible_python_interpreter=/usr/bin/python3

[kibana]

kibana ansible_host=kibana.ru-central1.internal ansible_user=fox ansible_python_interpreter=/usr/bin/python3

[bastion]

bastion  ansible_host=51.250.43.198 ansible_ssh_user=fox


[web_servers:vars]

ansible_ssh_user=fox

ansible_ssh='-o ProxyCommand="ssh -W %h:%p -q -i /home/fox/obraz/cat.pub fox@51.250.43.198"'


[zabbix:vars]

ansible_ssh_user=fox

ansible_ssh='-o ProxyCommand="ssh -W %h:%p -q -i /home/fox/obraz/cat.pub fox@84.201.151.234"'


[elasticsearch:vars]

ansible_ssh_user=fox

ansible_ssh='-o ProxyCommand="ssh -W %h:%p -q -i /home/fox/obraz/cat.pub fox@10.3.0.100"'


[kibana:vars]

ansible_ssh_user=fox

ansible_ssh='-o ProxyCommand="ssh -W %h:%p -q -i /home/fox/obraz/cat.pub fox@51.250.44.96"'
