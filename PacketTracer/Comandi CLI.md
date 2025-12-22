CLI (command line interface)

```
R# --> (modalità privilegiata)
R(config)# --> (menù configurazione del router R)
R(config-if)# --> (menu configurazione della fast ethernet) 
R(dhcp-config)# --> (menu configurazione del dhcp)

R> enable ↵
R# config ↵ (modalità privilegiata)
R(config)# hostname NuovoNome ↵ 
NuovoNome(config)# hostname R ↵ 
R(config)# interface FastEthernet 0/0 ↵ 
R(config-if)# ip address 192.168.0.254 255.255.255.255.0 ↵ 
R(config-if)# no shutdown ↵ 
R(config-if)# exit ↵ 

R(config)# ip dhcp pool ufficio ↵
R(dhcp-config)# network 192.168.0.0 255.255.255.0 ↵
R(dhcp-config)# default-router 192.168.0.254 ↵
R(dhcp-config)# dns-server 8.8.8.8 ↵

R(dhcp-config)# exit ↵
R(config)# ip dhcp esclude-address 192.168.0.255 192.168.0.255 ↵
```



