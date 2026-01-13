Il numero di porta è un numero associato ad un processo ( spesso coincide con il pid del processo stesso).
Il numero di porta varia da 0 a $2^{16}$ - 1 e serve ad identificare una particolare estremità di un canale di comunicazione ricavato nel collegamento logico esistente tra due host in comunicazione.

Sono classificati in 3 categorie:
- Da 0 a $2^{10}$ - 1 sono riservati per applicazioni particolari che sono definite nel layer applicazione ( esempi -> 80: http, 110: POP3, 20: [[Protocollo TCP]], 21: [[Protocollo TCP]] e FTP, 53: [[Protocollo UDP]] e DNS, 443: [[Protocollo TCP]] e https).
- Da $2^{10}$ a $2^{15}$ + $2^{14}$ -1 sono porte registrate. Cioè usate da alcuni [[Servizi]] offerti da applicazioni commerciali. Queste porte possono comunque essere utilizzate da applicazioni utente considerando però la possibilità reale di creare conflitti tra processi che utilizzano la stessa porta. 
- Da $2^{15}$ + $2^{14}$ a $2^{16}$ - 1 sono porte libere che ciascun utente può utilizzare liberamente. Nessuna applicazione commerciale utilizzerà una di queste porte.