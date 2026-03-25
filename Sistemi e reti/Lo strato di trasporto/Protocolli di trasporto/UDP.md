## UDP (User Datagram Protocol)

L'UDP è un [[Protocollo]] **non orientato alla connessione** (a differenza di quanto indicato nel testo originale, si precisa che UDP è senza connessione). Permette solo il controllo di integrità. Viene utilizzato quando non è necessario che tutti i dati arrivino integri al destinatario, ma esiste un vincolo sulla velocità di trasmissione; si utilizza in tutti quei casi in cui è necessario un alto bit‑rate.

I datagrammi (segmenti UDP) corrotti vengono semplicemente scartati.

### Caratteristiche principali
Il Protocollo UDP è concepito per tutte le applicazioni che **non necessitano della gestione completa della connessione** (cioè non si richiede che il destinatario invii segmenti di riscontro al mittente). Si utilizza per esempio per le applicazioni che distribuiscono contenuti multimediali.  

Per il recapito del segmento l'UDP si appoggia al layer IP. Non c'è nessuna procedura di apertura del canale logico (handshake) né di chiusura dello stesso.  
Si usa per applicazioni che **non tollerano ritardi di consegna** ma tollerano perdite saltuarie di dati.

### Multicast
Il protocollo UDP supporta l'invio **multicast**: è possibile spedire un segmento a più destinatari contemporaneamente usando degli IP particolari che identificano gruppi di macchine (il TCP è solo unicast).

![[Pasted image 20251109203025.png]]

### Dimensioni dei datagrammi
La dimensione dell'IP PDU è al massimo pari all'MTU.  
Per il protocollo IP incapsulato in Ethernet l'MTU vale **1500 Byte**.  
Considerando che l'intestazione IP è di 20 byte, allora in Ethernet il transport PDU ha una lunghezza massima di **1480 Byte**.

### Intestazione UDP
L'intestazione UDP è utilizzata per creare i segmenti UDP chiamati anche datagrammi.

![[Pasted image 20251109202948.png]]