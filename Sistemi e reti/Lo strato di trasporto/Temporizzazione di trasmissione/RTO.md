(retrasmition time out)

L' RTO rappresenta il tempo limite entro il quale deve giungere un segmento di riscontro ([[FLag ACK]]) ad un segmento inviato. Trascorso questo tempo senza riscontro il mittente invia nuovamente il segmento non riscontrato.

![[Pasted image 20251109205156.png]]

Il valore dell'RTO è fondamentale per le prestazioni offerte dalla rete. Se l'RTO è troppo piccolo si avranno spesso ritrasmissioni dei segmenti perchè il mittente li considera persi.
A causa delle duplicazioni il traffico raddoppia costringendo i router a smaltire il doppio dei pacchetti, compromettendone l'efficienza.

Se l'RTO è troppo grande viene ritrasmesso con eccessivo ritardo un segmento che potrebbe essere perso rallentando il bit-rate di trasmissione.












