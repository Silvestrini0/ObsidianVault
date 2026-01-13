Non c'è un server centrale che indicizza le risorse ma solo un server che raccoglie i socket dei processi che in un dato istante sono collegati alla rete e che possiedono il software peer to peer installato ( [[Server di Host caching]] ).

Un generico processo ( A ) si collega in background il [[Server di Host caching]] e comunica il proprio socket. Nel contempo richiede al server una decina di socket di processi remoti già accreditati presso il server.

Il processo ( A ) una volta ottenuto il socket tenta di instaurare connessioni tcp con tale socket e mantiene aperto il canale logico fino alla sua disconnessione. 

Ciascun processo si ritrova a partecipare ad una piccola rete logica chiamata overlay network con il vincolo che alcuni processi devono appartenere a reti overlay distinte, in modo che esistano intersezioni non vuote tra le overlay network.

Se ( B ) cerca una risorsa inoltra una richiesta ( query ) a tutti i processi della sua overlay network. Se uno di questi processi possiede la risorsa risponde direttamente al mittente della query con un messaggio query hit allegando le informazioni per richiedere la risorsa.

Ogni processo che non possiede la risorsa  inoltra la query agli altri processi della sua overlay network. In questo modo la richiesta diffonde tra tutte le overlay network. 

Le query hanno un identificativo ( descrittor ) nella loro intestazione così se un processo riceve una query che ha già inoltrato la scarta. 

Ogni query ha un TTL ( time to leave ) per impedire che la query diffonda incontrollata.






