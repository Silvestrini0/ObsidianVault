MTU IP vale al massimo $2^{16}$ byte. L'intestazione IP è lunga 20 byte, l'intestazione TCP è lunga 20 byte. come conseguenza l'MSS ( maximum segment size ) non può superare la lunghezza di $2^{16}$ - 40 byte. 

Se MTL è limitato dall'utilizzo del protocollo ethernet dall'utilizzo del protocollo ethernet, allora il MSS vale 1500 - 40 byte.

![[Pasted image 20251109225305.png]]

Il campo lunghezza dell'intestazione tcp è la lunghezza dell'intestazione [[Protocollo TCP]] espressa in parola da 32 bit e il campo è lungo 3 bit.

**CRW** (congested reduced window) è posto = a 1 se l'host sorgente ha limitato la velocità di ricezione, nel tentativo di ridurre la congestione di un router intermedio.

**ECE** (explicit congestion echo) serve per evitare la congestione dei router, i quali se rilevano una congestione imminente la segnalano modificando a 2 il penultimo e il terzultimo bit del campo TOS dell'intestazione IP.

**URG** (urgent) posto = a 1 impone di considerare il contenuto del campo urgent point. Nel campo 

**ACK** (acknowledgment) se posto uguale a uno si deve considerare il contenuto del campo [[Ack number]].

**PSU** ( push ) serve per velocizzare la spedizione del segmento senza bisogno di raggiungere L'MMS. Allo stato attuale nessuna primitiva richiamabile dall'utente e in grado di forzare il flag PSH.

**RST** ( restart ) posto = a 1 serve per comunicare che è stata rifiutata la connessione e si è intenzionati a inizializzarne una nuova.

**SYN** (Syncronized) posto = a 1 nelle fasi di handshake, indica che si vuole stabilire un collegamento logico e si vuole sincronizzare i [[Sequence number]].

**FIN** (finish) posto = a 1 serve per indicare che si vuole interrompere la trasmissione dei dati e chiudere il [[Canale Logico]]
in una direzione.
