(Multipurpose Internet Mail Extensions)
Il protocollo [[SMTP]] è molto datato (1980).
L'unica sequenza di byte che è in grado di elaborare sono quelle con MSB ( most significant bit )=0

I messaggi SMTP che si scambiano client e server sono essenziali e composti da 4 caratteri, in modo da risultare più efficiente nella trasmissione Lo scopo iniziale del servizio email era trasferire messaggi testuali di conseguenza i messaggi potevano essere codificati in ASCII standard (MSB sempre = 0). Da quando è stato necessario allegare file binari qualsiasi (con MSB non necessariamente = 0) è stato nec[[POP3]]essario introdurre un sistema di TransCodifica (MIME).
Esso permette di creare sequenze di byte con MSB = 0 partendo da qualsiasi sequenza binaria.

Utilizza il protocollo Base64:
- La sequenza di byte qualsiasi viene raggruppata in blocchi da 3 byte.
- Ciascun blocco da 3 byte viene suddiviso in 4 blocchi da 6 bit. 
- Questi 6 bit sono messi in relazione con 64 caratteri ( 2 alla 6 = 64 ) 
- 24 lettere minuscole e 24 maiuscole e pochi altri caratteri.
- ciascuno di questi caratteri viene espresso nella codifica ASCII standard con 8 bit
- Il risultato finale è che ogni 3 byte qualsiasi si ottengono 4 byte con MSB = 0.




