## Finestra di trasmissione (Transmission Window)

È una particolare finestra nella quale vengono memorizzati tutti i byte che la sorgente può trasmettere in sicurezza senza timore di saturare il buffer di ricezione del destinatario e senza bisogno di ricevere alcun messaggio di [[Ack]]. Contiene inoltre i numeri d'ordine dei byte già spediti e non ancora riscontrati.

La finestra viene gestita usando due variabili:
- Send base: è un contatore che punta alla cella che contiene il [[Sequence number]] del byte più vecchio non ancora riscontrato.
- Next sean (Next Sequence Number): punta alla cella che contiene il Sequence number del prossimo byte senza bisogno di ricevere altri riscontri.

![[Pasted image 20251109220256.png]]

### Ampiezza della finestra
**WS** è l'ampiezza in byte della finestra di trasmissione. Il suo valore è stabilito dal destinatario, che aumenta o riduce le sue dimensioni in modo dinamico a seconda dello stato in cui si trova il buffer di ricezione.

Nell'intestazione TCP c'è infatti un campo **Window** grazie al quale il destinatario comunica al mittente la dimensione da imporre per la finestra di trasmissione.

L'ultimo byte inviabile in un determinato momento avrà un Sequence number pari a `Send base + WS - 1`.

### Relazione tra variabili
Normalmente `Next sean` avrà un valore intermedio compreso tra il `Send base` e l'ultimo byte inviabile.

Di conseguenza `Next sean` deve essere **≥** dell'ultimo byte inviabile. Se quest'ultima disequazione non viene più rispettata, il mittente deve interrompere momentaneamente l'invio di byte perché il destinatario ha il buffer di ricezione saturo (pieno).

### Gestione del timer di ritrasmissione
Il valore della cella puntata dal `Send base` è l'identificativo del segmento più vecchio inviato non ancora riscontrato. Quindi il timer di ritrasmissione è associato a questo valore. Se si dovesse raggiungere il tempo limite RTO, viene ritrasmesso nuovamente il segmento avente sequence number uguale a `Send base`.

### Ricezione di un ACK
Se si riceve un segmento di riscontro possono capitare due cose distinte:

- Se il valore dell'**Ack number** è **superiore** a quello puntato dal `Send base`, viene aggiornato il `Send base` col valore dell'Ack number comunicato. Questo perché significa che un certo numero di byte inviati, ma non riscontrati, sono appena stati riscontrati.
- Se il valore dell'Ack number è **uguale** a quello puntato dal `Send base`, il `Send base` resta inalterato. Questo indica che è stato ricevuto semplicemente un ACK duplicato.