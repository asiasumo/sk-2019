Ustawianie parametrów sieci
---------------------------

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj oprogramowanie ``http-chat`` dostępne pod adresem ``https://github.com/jkanclerz/http-chat``

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 | Linux Debian  
| IP - address  | 10.0.2.15| polecenie ip a|
| MASKA  |/24 | 255.255.255.0|
|   |  | |
| PC 2  |Linux Debian  | |
| IP - address  |10.0.2.4 | polecenie ip a |
| MASKA  |/24 | 255.255.255.0|



Weryfikacja połączenia

Polecenie
```
ping adres_maszyny    
git clone adres http
sudo apt-get git
sudo apt-get python3
curl -X POST -d '{"text": "Zrób obiadek pls"}' http://adres_ip_hosta:8888/chat
```


Efekt
``` 
sprawdza jej połączenie z drugą(maszyny sie widzą)
instaluje oprogramowanie czatu
instaluje gita 
instaluje pythona 
wysyła wiadomość z klienta na serwer [INFO] <ip_klienta> Zrób obiadek pls
```



Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  Linux Debian
| IP - address  | 192.168.10.10 | |
| MASKA  | 255.255.255.0 | /24|
|   |  | |
| PC 2  | Linux Debian | |
| IP - address  | 172.16.100.100 | |
| MASKA  | 255.255.0.0 |/16|

Weryfikacja połączenia

Polecenie
```
ping adres_ip 
```

Efekt
```
sprawdzi czy maszyny się widzą - w tym wypadku, przy tych konkretnych ustawieniach maszyny się nie zobaczą bo są w innych sieciach(maski są inne a więc inne podsieci). 
```

1. Stworzyć sieć NAT
2. Podłączyć do sieci obie maszyny i zmienić MAC adres jednej z nich(jeśli są sklonowane) .
3. Sprawdzić czy maszyny się widzą. 
4. Ściągnąć oprogramowanie czatu i pythona. 
5. Odpalić plik .py z folderu httpchat ( PC2 jest teraz serwerem a PC1 nadal klientem)
6. Wysłać wiadomość z PC1( curl -X POST -d '{"text": "Zrób obiadek pls"}' http://adres_ip_hosta:8888/chat  )




Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  Linux Debian 
| IP - address  |  | |
| MASKA  |  | |
|   |  | |
| PC 2  | Linux Debian | |
| IP - address  |  | |
| MASKA  |  | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

1. 

Warto wiedzieć
--------------
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| Lokalizacja pliku z konfiguracją sieci| | |
| UP -> Wyłączenie interfejsu sieciowego| | |
| DOWN -> Włączenie interfejsu sieciowego| | |
| Sprawdzenie obecnych parametrów | | |
| lista wszystkich interfejsów | | |
| Które interfejsy jakie porty słuchają | | |
