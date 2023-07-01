# Домашнее задание к занятию "Система мониторинга Zabbix" - `Сергей Миронов - SYS-20`

### Задание 1

При решении этого задания были использованы следующие команды:
su -

wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb

dpkg -i zabbix-release_6.0-4+debian11_all.deb

apt update 

apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts

su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'

su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'

zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf

sudo systemctl restart zabbix-server apache2

sudo systemctl enable zabbix-server apache2

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/4456b2f3-1ddb-40dd-991d-dd2e6fdecade)

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/775128e1-0d52-48a5-95c7-8dcdf84cfbb6)

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/564b1ab8-8665-4c13-a378-8021d626c926)

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/c3d5cab5-2ef4-4226-8fd9-6e9505302dfa)

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/9d4d4de4-feea-48e3-97de-ff6593076cf9)

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/ab8d62f1-58f1-439d-8eb1-fc3c917c6dd1)

### Задание 2

1. Zabbix agent подключен на 1 машине

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/89a4a0f0-c106-4ba5-a40e-38830943e536)

 abbix agent подключен на двух машинах

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/b71fbd4a-5fc0-4a1a-afbb-977ae833b6e1)

2. Скрины выполнения команды
cat /var/log/zabbix/zabbix_agentd.log

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/e85828cf-8576-4ef5-8c00-995ace81c669)

![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/9be9b6cd-b13e-48de-be50-9aa267cc91c5)


3. скриншот раздела Monitoring > Latest data




4. Список использованных команд

sudo apt install postgresql
wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb
dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb
(для машины с Debian 11 команда чуть отличалась wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb)
apt update
systemctl restart zabbix-agent
systemctl enable zabbix-agent

Затем 
sudo nano /etc/zabbix/zabbix_agentd.conf (через Ctrl+w находим строчку Server= и вписываем нужный адрес через запятую)
sudo systemctl restart zabbix-agent
   



