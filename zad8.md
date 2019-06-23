Zadanie 8 
-------------------



Ustawienia sieci
------------

|       | LAN 1         | LAN 2          | NAT |
| ----- |---------------| ---------------| -   |
| ADRES |172.22.160.0/23| 172.22.128.0/19|  -  |


| MASZYNA | PCO   | PC1  | PC2   |
| --------|-------|------| ------|  
| SIEĆ 1  | NAT   | LAN 1| LAN 2 |    
| SIEĆ 2  | LAN 1 |      |       |
| SIEĆ 3  | LAN 2 |      |       |



Ustawienia maszyn
-----------

PC0
----

1. Zmienić adres MAC KONIECZNIE
2. nano /etc/network/interfaces - zmień ustawienia NAT na DHCP 
3. nano /etc/sysctl.conf odkomentuj ip forwarding 
4. ip a add 172.22.160.1/23 dev enp0s8 - lan1
5. ip a add 172.22.128.1/19 dev enp0s9 - lan2
6. ip link set STH up 
7. jeśli wywala ip z NAT to zrobiłam flusha więc zresetować dhclient -r i dodać
8. echo 1 > /proc/sys/net/ipv4/ip_forward


PC1
----

1. Zmienić adres MAC KONIECZNIE
2. ip a add 172.22.160.100/23 dev enp0s3 
3. ip link set STH up 
4. nano /etc/resolve.conf   nameserver na 192.169.1.1
5. ip route add default via 172.22.160.1/23
6. pinguj PC0 żeby sprawdzić i na odwrót


PC2
----

1. Zmienić adres MAC KONIECZNIE
2. ip a add 172.22.128.100/19 dev enp0s3 
3. ip link set STH up 
4. nano /etc/resolve.conf   nameserver na 192.169.1.1
5. ip route add default via 172.22.128.1/19
6. pinguj PC0 żeby sprawdzić i na odwró†




