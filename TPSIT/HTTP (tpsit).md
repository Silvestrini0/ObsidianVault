
![[HTTP.pdf]]

**HTTP 1.1**
Introduce il pipelining che consente al client di inviare più richieste senza attendere la risposta tuttavia il server è comunque obbligato a mantenere l'ordine delle risposte. Nonostante è stato pensato per migliorare l'efficienza delle connessioni persistenti, è stato poco utilizzato nella pratica a causa di problemi di compatibilità, con i proxy intermedi. E dal fatto che una risposta lenta poteva ritardare le successive.

**Head of Line Blocking** (in riferimento all'HTTP 1.1)
E' il comportamento per cui una risposta lenta sulla stessa connessione impedisce l'invio delle risposte successive. Questo comportamento è dovuto al modello sequenziale del protocollo **Applicativo** 

**Chunked Transfer** (in riferimento all'HTTP 1.1)
Viene introdotto la **Chunked Transfer Encoding** che permette al server di inviare il corpo dei blocchi (Chunk) senza conoscere in anticipo la lunghezza totale del contenuto. Il precedente approccio presente nell' HTTP 1.0 risultava limitante soprattutto nel caso di contenuti dinamici generati progressivamente ad esempio pagine costruite interrogando un database o ricevendo dati da servizi esterni in cui la dimensione finale del contenuto non è nota a priori. Con il **Chunked Transfer Encoding** il server può iniziare immediatamente l'invio dei dati man mano che vengono prodotti. Il messaggio viene quindi inviato in blocchi in modo sequenziale ciascuno dei quali preceduto dalla propria dimensione, permettendo al client di ricostruire correttamente il contenuto.

**Caching** ( in riferimento all'HTTP 1.1)
Con l'Http 1.1 viene migliorato l'utilizzo della Cache in proporzione all'Http 1.0. 
Se bene in Http 1.0 esistessero meccanismi basilari come **Expires** e **If Modify Since** il controllo risultava limitato e basato sul **Timestamp**.
Con Http 1.1 vengono introdotti header più avanzati, come il **Cache Control** che definisce in modo preciso le politiche di caching (ad esempio durata, visibilità e validità della risorsa).

L' **ETag** è un indentificatore univoco definitivo della versione della risorsa.

Il Client può successivamente utilizzare **If None Match** per chiedere al server se la versione in Cache è ancora valida, in caso affermativo il server risponde con il codice 304 ( **Not Modified** ), senza rinviare il contenuto. Questo consente una gestione più efficiente riducendo traffici e latenze,

**HTTP 2.0**
Standardizzato nel 2015 introduce un'architettura binaria basata su frame e un multiplexer applicativo che consente di utilizzare più stream logici indipendenti sulla stessa connessione.
Integra la **compressione degli header**, la **prioritizzazione degli stream**, queste sono le caratteristiche macroscopiche alterate.
In Http 2.0 i messaggi non vengono trasmessi come testo ASCII leggibile ma come dati binari strutturati in frame, ogni frame contiene campi predefiniti come:

| Lunghezza | Stream Id | Tipo | Flag | ... Payload ... |
| --------- | --------- | ---- | ---- | --------------- |

Il formato binario utilizzato elimina la necessità di interpretare righe di testo rendendo il parsing più rapido e meno soggetto di ambiguità. All'interno di questa struttura binaria anche gli header non sono più inviati come stringhe ma vengono codificati e compressi tramite il meccanismo **HPack**.

In http il multiplexing è realizzato tramite un meccanismo di framing che suddivide la comunicazione in unità elementari ciascuna associata allo **Stream Id**.
Una singola connessione TCP trasporterà quindi una sequenza continua di frame binari; ogni frame conterrà nel proprio header l'identificativo che consentirà al destinatario di demultiplexare i dati e quindi ricostruire i flussi logici indipendenti.