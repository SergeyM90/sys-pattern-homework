# Домашнее задание к занятию «10.1 «Keepalived/vrrp»» - `Сергей Миронов - SYS-20`

###   Задание 1   ###
Разверните топологию из лекции и выполните установку и настройку сервиса Keepalived.

vrrp_instance test {

state "name_mode"

interface "name_interface"

virtual_router_id "number id"

priority "number priority"

advert_int "number advert"

authentication {

auth_type "auth type"

auth_pass "password"

}

unicast_peer {

"ip address host"

}

virtual_ipaddress {

"ip address host" dev "interface" label "interface":vip

}

}


![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/ac1e1996-885c-4936-b9ea-3d474256a0b8)


![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/7282a435-516e-4e47-9130-393c6cc6293e)


![image](https://github.com/SergeyM90/sys-pattern-homework/assets/84016375/a2cea478-cdc1-4c51-a30f-ae89951cef67)

