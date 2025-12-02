Dal processo mittente esce un flusso di byte ordinati diretti dallo strato di trasporto del mittente.

Il Payload di un segmento di trasporto è un sottoinsieme ordinato di 91 byte contigui prelevati dal flusso di dati.

La posizione che ciascun byte occupa nel flusso dati si chiama numero d'ordine o [[Sequence number]]. 

Il sequence number viene incluso nell' [[Intestazione TCP]]. 
Nell'intestazione si trova anche un campo che indica la lunghezza totale dell'[[Intestazione TCP]].

In questo modo è possibile determinare per differenza la lunghezza totale del pacchetto IP a cui tolgo la lunghezza dell'[[Intestazione TCP]].

Grazie al [[Sequence number]] e alla conoscenza della lunghezza del payload ( campo dati ) è possibile per il destinatario sapere a priori quale sarà il [[Sequence number]] del prossimo segmento ricevuto più il numero di byte del campo dati.

Nello strato di trasporto del destinatario esiste un buffer di ricezione in grado di memorizzare temporaneamente il campo dei segmenti ricevuti.

**Possono capitare 3 situazioni distinte:**
- [[Sequence number]] ricevuto > di [[Sequence number]] atteso --> ho creato un buco nella continuità dei dati. Memorizzo ugualmente il segmento ma richiedo la ritrasmissione del segmento con [[Sequence number]] atteso.
- [[Sequence number]] ricevuto < di [[Sequence number]] atteso -->  ho ricevuto un duplicato, lo scarto e richiedo la ritrasmissione del segmento [[Sequence number]] atteso.
- [[Sequence number]] ricevuto  = [[Sequence number]] atteso --> memorizzo il segmento che risulta contiguo ai precedenti e richiedo l'invio del prossimo segmento (di cui posso calcolare il [[Sequence number]]).

![[Pasted image 20251109212634.png]]

In ogni segmento di ACK inviato è presente un campo chiamato [[Ack number]] associato al flusso dati nella direzione opposta. 

Una stazione può essere sia il mittente di un segmento sia il destinatario di un segmento per il quale deve produrre un riscontro.
L'[[Ack number]] che il mittente ritorna al destinatario è il numero del primo byte che si aspetta di ricevere al successivo invio ([[Sequence number]] atteso). Se al mittente giunge un certo segmento con un certo numero m nel campo [[Ack number]] significa che il destinatario ha ricevuto sicuramente tutti i byte fino a *n-1* e quindi si aspetta l'invio di un segmento con [[Sequence number]] n.

Un segmento di ACK svolge 2 funzioni:
- Segnala l'avvenuta ricezione di un segmento.
- Controlla la sequenza e l'ordine di invio dei segmenti e controlla il rateo di velocità di invio dei segmenti.

![[Pasted image 20251109213613.png]]

Una volta ricevuto un segmento di ACK non duplicato, il numero di segmenti inviati dipende da quanti la destinazione possa riceverne ed è lei che comunica al mittente, tramite un opportuno campo dell'[[Intestazione TCP]] del segmento di ACK.

Solo quando si riceve un segmento di ACK non duplicato si resetta l'[[RTO]] e se il buffer di ricezione del destinatario lo permette si invia il segmento richiesto altrimenti se si riceve un segmento di ACK duplicato, quest'ultimo non produce nessun evento.

Il mittente libera la memoria associata ai segmenti, in cui i numeri d'ordine sono stati riscontrati, gli altri segmenti restano memorizzati perché possono essere richiesti nuovamente.