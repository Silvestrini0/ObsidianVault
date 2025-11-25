(hyper text transfer protocol )
Si appoggia alla porta TCP 80.
Trasferimento di pagine web

Serve per i dati ipertestuali formattati in un file html e utilizza un'architettura client server.
Il segmento di trasporto utilizzato è TCP nel cui campo dati viene incapsulato il protocollo HTTP, che si chiama Messaggio HTTP. 
I messaggi HTTP sono di due tipi e sono codificati in ASCII:
- Richieste dal server
- Risposte dal server
Il principio di funzionamento è il seguente:
- Si apre un collegamento tcp tra browser e server (3WH) 
- Il browser richiede la risorsa (richiesta HTTP)
- Il server risponde inviando la pagina voluta (risposta HTTP)
- Il server, chiude la connessione TCP unilateralmente nella versione 1.0, mentre dalla 1.1 in avanti il server mantiene aperta la connessione per un certo lasso di tempo.
Nello specifico: 
- Il browser analizza l'[[URL]] e recupera l'indirizzo simbolico (informazioni sul dominio).
- Interroga il servizio [[DNS]] per recuperare l'id del server.
- Si apre una connessione TCP verso il server utilizzando come numero di porta 80 per il server e come ip quello fornito dal DNS.
- Il client invia una richiesta HTTP ( in cui viene utilizzato il comando/metodo get) attraverso il socket associato alla connessione. Nella richiesta viene specificato il percorso per giungere al file e il dominio del server, recuperandolo dall'URL. E' importante includere il dominio del server perchè in uno stesso server in esecuzione su una macchina avente un'assegnato id possono essere registrati più domini e il protocollo HTTP deve capire per quale dominio è stata fatta la richiesta.
- Il server incapsula la risorsa richiesta nella risposta HTTP e la invia al socket del client (file.html).
- A seconda delle versioni del protocollo il server chiede la chiusura unilaterale della connessione.


N.B. nel caso venisse richiesta una [[Pagina web Dinamica]] lato server , il punto 5 è leggermente differente.
La risorsa richiesta contiene codice php che deve essere eseguito dal server prima di inviare la pagina. 
Spesso il codice php prevede un collegamento al DBMS ( data base management system ) per richiedere informazioni relative al client che ha fatto la richiesta HTTP. In questo modo è possibile costruire un contenuto personalizzato con informazioni del client memorizzate però sul database gestito dal DBMS.


Il protocollo HTTP è definito stateless, significa che non è in grado di memorizzare sul client informazioni riguardo alle connessioni precedenti HTTP; esiste la possibilità deprecata.