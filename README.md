1. Вопрос по Ansible. Надо запускать Ansible через Bastion или локальный хост?
2. Через Bastion не получается зайти в ВМ, запрашивается пароль даже при явном указании ключа, но доступ к машинам ВМ1 и ВМ2 имеется через команду:ssh -v -o ProxyCommand='ssh -W %h:%p -q fox@51.250.37.254 -i cat' fox@10.1.0.10 -i cat, с локального хоста, к остальным ВМ (kibana.zabbix,elastic) подключаться не удается.

Запуск с локального хоста![alt text](https://github.com/sAslank/-/blob/main/img/к%20дип.jpg)


Это то как он зависает при попытке подключения к ВМ (kibana.zabbix. elastic)![alt text](https://github.com/sAslank/-/blob/main/img/дип1.jpg)

Через Bastion попытка подключения к вм1, создал ключ установил права chmod 600 ![alt text](https://github.com/sAslank/-/blob/main/img/дип2.jpg)
