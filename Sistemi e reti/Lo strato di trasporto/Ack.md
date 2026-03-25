# Ack Number
E' il numero d'ordine del primo byte che ci si aspetta di ricevere alla prossima ricezione. 
Viene considerato sono se il FLag ACK = 1.
# Flag Ack
Se il flag ACK all'interno della Intestazione [[TCP]] è posto uguale a 1, allora il segmento diventa un 
segmento di risposta o segmento di ACK. 
Il caso tipico è che un host mittente invia un segmento ad un host destinatario e l'host destinatario riscontra il segmento inviando un segmento di ACK all'host mittente.