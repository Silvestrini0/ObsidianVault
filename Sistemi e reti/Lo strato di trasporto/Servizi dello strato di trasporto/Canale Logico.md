E' un collegamento virtuale dedicato e diretto tra i processi in comunicazione in esecuzione su host remoti.
In realtà l'unità informativa viene spezzata in più segmenti e ciascuno di questi può giungere a destinazione attraverso percorsi fisici differenti e può giungere a destinazione con un'ordine di arrivo differente da quello di invio.

*immagine*

Per definire univocamente il canale logico si utilizzano i due socket di estremità, ciascuna socket è formata dalla coppia di indirizzo IP e della scheda di rete della macchina in cui è in esecuzione un processo e dal [[Numero di porta]] che viene associato a quel processo, se esistono più canali logici che partono da uno stesso host e terminano su un'altro host, allora è possibile considerare il raggruppamento dei canali logici che vanno ad individuare i collegamento logico.

Il collegamento logico è multiplexato, utilizzando i numeri di porta.