# Домашнее задание к занятию "`9.1. Обзор систем IT-мониторинга`" - `Мальцев Виктор`

---

### Задание 1

`Установите Zabbix Server с веб-интерфейсом.

Приложите скриншот авторизации в админке. Приложите текст использованных команд в GitHub.`

1) ![alt text](https://github.com/vmmaltsev/screnshot/blob/main/Screenshot_5.png)

2) sudo apt install postgresql
   wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4%2Bdebian11_all.deb
   sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb
   sudo apt update
   sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
   sudo -u postgres createuser --pwprompt zabbix
   sudo -u postgres createdb -O zabbix zabbix 
   zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix 
   sudo nano /etc/zabbix/zabbix_server.conf для редактирования параметра DBPassword=password
   sudo systemctl restart zabbix-server zabbix-agent apache2
   sudo systemctl enable zabbix-server zabbix-agent apache2 


---

### Задание 2

`Установите Zabbix Agent на два хоста.

Приложите скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу. Приложите скриншот лога zabbix agent, где видно, что он работает с сервером. Приложите скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные. Приложите текст использованных команд в GitHub.`

1) ![alt text](https://github.com/vmmaltsev/screnshot/blob/main/Screenshot_9.png)
2) ![alt text](https://github.com/vmmaltsev/screnshot/blob/main/Screenshot_7.png)
3) ![alt text](https://github.com/vmmaltsev/screnshot/blob/main/Screenshot_8.png)



a. Установите репозиторий Zabbix
Документация
# wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4%2Bdebian11_all.deb
# dpkg -i zabbix-release_6.0-4+debian11_all.deb
# apt update
b. Установите Zabbix агент
# apt install zabbix-agent
c. Запустите процесс Zabbix агента

Запустите процесс Zabbix агента и настройте его запуск при загрузке ОС.
# systemctl restart zabbix-agent
# systemctl enable zabbix-agent

