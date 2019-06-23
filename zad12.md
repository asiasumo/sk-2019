
ZADANIE 12
--- 


* Wi-Fi``192.168.0.0/22``


* LAN  np. ``10.0.9.0/26``
 * /26 = 62 hostów
  
  
#### Przydział adresów:
------
### Poziom 0
  * sala 009:
    *  ``10.0.9.0/26``
  * sala 013:
    *  ``10.0.13.0/26``
  * sala 014:
    *  ``10.0.14.0/26``
  * sala 017:
    *  ``10.0.17.0/26``
  Po 35 komputerów w każdej sali co daje nam 140 komputerów na pięrze 0.
    
### Poziom 1
  * sala 115:
    * ``10.0.115.0/26``
  * sala 116:
    * ``10.0.116.0/26``
  * sala 117:
    * ``10.0.117.0/26``
  * sala 122:
    * ``10.0.122.0/26``
  Po 35 komputerów w każdej sali co daje nam 140 komputerów na pięrze 1.    
    
### Poziom 2
  * sala 201:
    * ``10.0.201.0/26``
  * sala 202:
    * ``10.0.202.0/26``
  * sala 203:
    * ``10.0.203.0/26``
  * sala 204:
    * ``10.0.204.0/26``
  Po 35 komputerów w każdej sali co daje nam 140 komputerów na pięrze 2.
  
  Czyli łącznie 3 x 140 komputerów  = 420 komputerów
  
  
  ### Diagram:
  ---
  ![diagram](sieci.png)
  
  
  
### IP Forwarding
---
``echo 1 >/proc/sys/net/ipv4/ip_forward``

### Routing
---
``ip route add default via 10.0.9.1``  
``ip route add default via 10.0.115.1``  
``ip route add default via 10.0.201.1``  


### Masquerade
---
#### Serwer główny
``sudo iptables -t nat -A POSTROUTING -s 188.156.220.160/28 -o enp0s3 -j MASQUERADE``  
``sudo iptables -t nat -A POSTROUTING -s 188.156.220.176/28 -o enp0s3 -j MASQUERADE``  
``sudo iptables-save | sudo tee /etc/iptables.sav``  

### DHCP
---
``Instalacja DHCP: apt install isc-dhcp-server``  
``Odkomentowujemy: config DHCPDv4_CONF``    

### SALE
---
```
subnet 10.0.9.0 netmask 255.255.252.192 {
        option routers                  10.0.9.1;
        option subnet-mask              255.255.252.192;
        option domain-name-servers      10.0.9.1;
        range                           10.0.9.2 10.0.9.62;
}

subnet 10.0.115.0 netmask 255.255.252.192 {
        option routers                  10.0.115.1;
        option subnet-mask              255.255.252.192;
        option domain-name-servers      10.0.115.1;
        range                           10.0.115.2 10.0.115.62;
}

subnet 10.0.201.0 netmask 255.255.252.192 {
        option routers                  10.0.201.1;
        option subnet-mask              255.255.252.192;
        option domain-name-servers      10.0.201.1;
        range                           10.0.201.2 10.0.201.62;
}

```

### Wi-Fi
---
```
subnet 10.10.0.0 netmask 255.255.252.0 {
        option routers                  11.0.0.1;
        option subnet-mask              255.255.252.0;
        option domain-name-servers      11.0.0.1;
        range                           11.0.0.15 11.0.3.250;
}
```
