( User Datagram Protocol )
L' UDP è un [[Protocollo]] orientato alla connessione, permette solo il controllo di integrità, si usa quando non è necessario che tutti i dati arrivino integri al destinatario ma esiste un vincolo sulla velocità di trasmissione, si utilizza in tutti quei casi in cui è necessario un alto bit-rate.

I datagrammi (segmenti UDP) corrotti vengono semplicemente scartati.

Il [[Protocollo]] UDP è concepito per tutte le applicazioni che non necessitano della gestione completa della connessione ( cioè non si richiede che il destinatario invii segmenti di riscontro al mittente ). Si utilizza per esempio per le applicazioni che distribuiscono contenuti multimediali. Per il recapito del segmento l'UDP si appoggia al layer ip. Non c'è nessuna procedura di apertura del canale logico (hand shake) ne di chiusura dello stesso. Si usa per applicazioni che non tollerano ritardi di consegna ma tollerano perdite saltuarie di dati.

Il protocollo UDP supporta l'invio multicast, cioè è possibile spedire un segmento a più destinatari contemporaneamente usando degli ip particolari che identificano gruppi di macchine ( il [[Protocollo TCP]] è solo unicast).

![[Pasted image 20251109203025.png]]

La dimensione dell'ip PDU è al massimo pari all'MTU.
Per il protocollo ip incapsulato in ethernet l'MTU vale 1500 Byte.
Considerando che l'intestazione ip è di 20 byte allora in ethernet il transport PDU ha una lunghezza massima di 1480 Byte.






