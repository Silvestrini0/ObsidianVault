Si trova al 4° livello della pila ISO/OSI e si comporta da interfaccia tra gli strati applicativi e quelli di rete,il suo scopo è instaurare un  [[Canale Logico]] di comunicazione tra processi in esecuzione su host remoti.
Questo significa che i processi remoti comunicano tra di loro come se si trovassero sullo stesso dispositivo. I processi non si devono curare di come avvenga il trasferimento dell'informazione a livello fisico.

![[Pasted image 20251109203121.png]]

Quando si programma un'applicazione distribuita è necessario scegliere per il trasporto dei dati uno di questi due protocolli:
- [[Protocollo UDP]],
- [[Protocollo TCP]].

Un' applicazione che vuole ricevere dati da un'altra utilizzando un [[Protocollo]] del layer di trasporto deve creare una Socket formata dall'indirizzo IP della scheda di rete della macchina su cui il processo è in esecuzione e dal valore del [[Numero di porta]] associato ad esso.

Comunica questa coppia ( ip, [[Numero di porta]] ) al sistema operativo in modo tale che tutti i segmenti destinati a quella porta, presenti nei pacchetti destinati a quella scheda di rete, le vengano recapitati.

L'applicazione inoltre invierà segmenti di risposta ad una socket di destinazione associato al processo con cui si vuole comunicare.

Ovviamente i numeri di porta sono 2 campi sicuramente presenti sia nell'intestazione [[Protocollo UDP]] che [[Protocollo TCP]] perché permettono di garantire il multiplexing e il demultiplexing.





