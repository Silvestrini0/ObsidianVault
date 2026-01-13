Associata all'invio di un segmento è un timer che viene usato per calcolare il tempo che intercorre tra l'invio di un segmento e la ricezione del segmento di ACK di riscontro. ([[RTT]])

Il timer di ritrasmissione viene resettato in 4 casi:
- Quando la coda dei segmenti in trasmissione è vuota e comincia a riempire con i dati prodotti dal processo che li vuole mandare nel canale logico. In questo caso il flusso viene diviso in segmenti e se il buffer del destinatario è disponibile a riceverli, allora i segmenti vengono inviati in sequenza nel canale logico e può partire il timer di ritrasmissione associato al più vecchio segmento inviato e mai riscontrato.
- Quando si riceve un segmento di ack non duplicato a conferma che il più vecchio segmento inviato non è ancora stato ricevuto dal destinatario. In questo caso si può procedere con l'invio di nuovi segmenti se il buffer del destinatario può raccoglierli. 
- Quando si raggiunge il tempo limite [[RTO]] in questo caso si invia nuovamente il più vecchio segmento inviato ma non ancora riscontrato.
- Nel caso dell'invio veloce.

IL CASO DELL'INVIO VELOCE
se tra il periodo che intercorre tra l'azzeramento del timer e il raggiungimento del tempo limite [[RTO]] si ricevono 3 duplicati dello stesso segmento di ack allora viene resettato il timer e inviato il segmento richiesto.

![[Pasted image 20251109215420.png]]

