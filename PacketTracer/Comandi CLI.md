CLI (command line interface)

**Modalità varie**
```
R# --> (modalità privilegiata)
R(config)# --> (menù configurazione del router R)
R(config-if)# --> (menu configurazione della fast ethernet) 
R(dhcp-config)# --> (menu configurazione del dhcp)
```
**Configurazione generica di un router**
```
R> enable ↵
R# config ↵ 
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
**Comando show**
```
R# show ip route ↵
R# show ip dhcp binding ↵
R# show ip dhcp pool ↵
R# show interface ↵
R# show int fa0/0 ↵
R# show ip nat translation ↵
```
**Comando wr mem**
```
 R# wr mem ↵
```

**Comandi per le rotte statiche**
![[Pasted image 20260113175425.png]]
es.
```
R4(config)# ip route 199.0.0.128 255.255.255.192 11.0.0.1 ↵
R4(config)# ip route 199..0.0.192 255.255.255.192 11.0.0.1 ↵
R4(config)# ip route 200.0.0.0 255.0.0.0 11.0.0.1 ↵
R4(config)# ip route 200.0.1.0 255.255.255.0 11.0.0.9 ↵
R4(config)# ip route 0.0.0.0 0.0.0.0 11.0.0.5 ↵
R4(config)# ip route 200.0.0.1 255.255.255.255 11.0.0.9 ↵ (server HTTP)
```

**Comandi per il Nat**
![[Pasted image 20260113175452.png]]
es.
```
R(config)# ip nat inside source static 192.168.0.253 200.0.0.1 ↵

R(config)# interface FastEthernet 1/0 ↵
R(config-if)# ip nat inside ↵
R(config-if)# exit ↵

R(config)# interface FastEthernet 2/0 
R(config-if)# ip nat outside ↵
R(config-if)# exit ↵

```
