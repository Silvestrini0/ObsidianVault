(Multipurpose Internet Mail Extensions)
Il protocollo [[SMTP]] è molto datato (1980).
L'unica sequenza di byte che è in grado di elaborare sono quelle con MSB ( most significant bit )=0

I messaggi SMTP che si scambiano client e server sono essenziali e composti da 4 caratteri, in modo da risultare più efficiente nella trasmissione Lo scopo iniziale del servizio email era trasferire messaggi testuali di conseguenza i messaggi potevano essere codificati in ASCII standard (MSB sempre = 0). Da quando è stato necessario allegare file binari qualsiasi (con MSB non necessariamente = 0) è stato necessario introdurre un sistema di transcodifica (MIME).
Esso permette di creare sequenze di byte con MSB = 0 partendo da qualsiasi sequenza binaria.

**Utilizza il protocollo [[BASE 64]].**




