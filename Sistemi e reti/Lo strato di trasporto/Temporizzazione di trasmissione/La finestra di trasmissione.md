E' una particolare finestra nella quale vengono memorizzati tutti i byte che la sorgente può tramettere in sicurezza senza timore saturare il buffer di ricezione del destinatario e senza bisogno di ricevere alcun messaggio di [[FLag ACK]]. Contiene inoltre i numeri d'ordine dei byte già spediti e non ancora riscontrati. La finestra viene gestita usano 2 variabili:
- [[Send base]]
- [[Next sean]].

![[Pasted image 20251109220256.png]]

Vedi [[WS]].

Nell'intestazione [[Protocollo TCP]] c'è infatti un campo (window) grazie al quale il destinatario comunica al mittente la dimensione da imporre per la finestra di trasmissione. L'ultimo byte inviabile in un determinato momento avrà un [[Sequence number]] pari al [[Send base]] + [[WS]] - 1.

Normalmente [[Next sean]] avrà un valore intermedio compreso tra il [[Send base]] e l'ultimo byte inviabile.

Di conseguenza [[Next sean]] deve essere >= dell'ultimo byte inviabile. Se quest'ultima disequazione non viene più rispettata il mittente deve interrompere momentaneamente l'invio di byte, perché il destinatario ha il buffer di ricezione saturo ( pieno ).

Il valore della cella puntata dal [[Send base]] è l'identificativo del segmento più vecchio inviato non ancora riscontrato. Quindi il timer di ritrasmissione è associato a questo valore. Se si dovesse raggiungere il tempo limite [[RTO]] viene ritrasmesso nuovamente il segmento avente con sequence number uguale o pari al [[Send base]].

Se si riceve un segmento di riscontro possono capitare 2 cose distinte:
- Se il valore dell' ack number fosse superiore a quello puntato dal [[Send base]] viene aggiornato il [[Send base]] col valore dell' ack number che viene comunicato. Perchè significa che un certo numero dei byte inviati, ma non riscontrati, sono appena stati riscontrati.
- Il valore dell' ack number è >= a quello puntato dal [[Send base]]; in questo caso il [[Send base]] resta inalterato e significa che è stato ricevuto semplicemente un [[FLag ACK]] duplicato.

