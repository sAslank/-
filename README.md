1. Вопрос по Ansible. Нам надо запускать Ansible через Bastion или локальный хост?
2. Через Bastion не получается зайти в ВМ, запрашивается пароль даже при явном указании ключа, но доступ к машинам ВМ1 и ВМ2 имеется через команду:ssh -v -o ProxyCommand='ssh -W %h:%p -q fox@51.250.37.254 -i cat' fox@10.1.0.10 -i cat, с локального хоста, к остальным ВМ (kibana.zabbix,elastic) подключаться не удается.
https://github.com/sAslank/-/commit/581747cb76b8ed1301a03af7edaf67a3872b326b
