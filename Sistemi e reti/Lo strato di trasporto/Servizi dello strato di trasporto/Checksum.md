Il checksum è calcolato sull'insieme di intestazione e dati ma l'intestazione non è quella dell'[[Intestazione UDP]] ma è una pseudo intestazione formata da alcuni campi dell'[[Intestazione TCP]] e alcuni campi dell'[[Intestazione IP]].

![[Pasted image 20251109202855.png]]

CALCOLO DEL CHECKSUM
- Si prende tutto il segmento UDP; preceduto dalla pseudo intestazione;
- Si suddivide l'insieme di dati più pseudo intestazione in blocchi da 16 bit;
- Si inizializza il campo checksum con 16 zeri;
- Si esegue la somma bit a bit in colonna modulo 2;
- Si complementa il risultato finale e si inserisce nel campo checksum;
N.B. Se provassi a ricalcolare il checksum con la stessa procedura senza inizializzare a 0, il checksum ma inserendo il valore calcolato in precedenza otterrei una stringa di 0.

Il destinatario esegue le stesse operazioni del mittente però al punto 3 utilizza direttamente la sequenza di check sua inviata dal mittente. 
Se il risultato è una sequenza di 16 zeri significa che il segmento è arrivato integro.

Nel [[Protocollo UDP]] se il destinatario rileva un errore non viene richiesta la ritrasmissione.

![[Pasted image 20251109202928.png]]

