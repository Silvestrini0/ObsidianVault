**Il passaggi del protocollo Base64:**
- La sequenza di byte qualsiasi viene raggruppata in blocchi da 3 byte.
- Ciascun blocco da 3 byte viene suddiviso in 4 blocchi da 6 bit. 
- Questi 6 bit sono messi in relazione con 64 caratteri ( 2^6 = 64 ) 
- Di questi, 24 lettere minuscole e 24 maiuscole e pochi altri caratteri.
- Ciascuno di questi caratteri viene espresso nella codifica ASCII standard con 8 bit
- Il risultato finale è che ogni 3 byte qualsiasi si ottengono 4 byte con MSB = 0.

Se il server [[SMTP]] richiede l'autenticazione allora anche la password e il nome utente per il login devono subire la transcodifica prima di essere spediti al server