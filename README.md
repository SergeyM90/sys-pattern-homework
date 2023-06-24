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

