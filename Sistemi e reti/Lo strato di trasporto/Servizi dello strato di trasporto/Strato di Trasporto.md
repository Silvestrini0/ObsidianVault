
Si trova al **4° livello** della pila ISO/OSI e si comporta da interfaccia tra gli strati applicativi e quelli di rete. Il suo scopo è instaurare un **[[Canale Logico]]** di comunicazione tra processi in esecuzione su host remoti.

Questo significa che i processi remoti comunicano tra di loro **come se si trovassero sullo stesso dispositivo**. I processi non si devono curare di come avvenga il trasferimento dell'informazione a livello fisico.

![[Pasted image 20251109203121.png]]

## Scelta del protocollo
Quando si programma un'applicazione distribuita è necessario scegliere per il trasporto dei dati uno di questi due protocolli:
- [[UDP]]
- [[TCP]]
## Socket
Un'applicazione che vuole ricevere dati da un'altra utilizzando un [[Protocollo]] del livello di trasporto deve creare una **Socket** formata da:
- **Indirizzo IP** della scheda di rete della macchina su cui il processo è in esecuzione
- **Numero di porta** associato al processo

L'applicazione comunica questa coppia `(IP, numero di porta)` al sistema operativo, in modo tale che tutti i segmenti destinati a quella porta, presenti nei pacchetti destinati a quella scheda di rete, le vengano recapitati.

L'applicazione inoltre invierà segmenti di risposta ad una **socket di destinazione** associata al processo con cui si vuole comunicare.

## Numero di porta
I numeri di porta sono due campi sicuramente presenti sia nell'intestazione UDP che TCP, perché permettono di garantire il **multiplexing** e il **demultiplexing**.