## RTT e RTO

Associata all'invio di un segmento è un **timer** che viene usato per calcolare il tempo che intercorre tra l'invio di un segmento e la ricezione del segmento di ACK di riscontro.
### RTT (Round Trip Time)
Tempo che intercorre tra l'invio di un segmento da un processo sorgente verso un processo di destinazione e la ricezione del relativo riscontro.
### RTT Medio
L'RTT medio è il valor medio dell'RTT calcolato in un certo intervallo di tempo. Siccome l'RTT varia a seconda della congestione della rete, il valor medio indica quanto tempo in media il mittente deve attendere per ottenere un riscontro a un segmento. Anche l'RTT medio varia nel tempo ma con fluttuazioni di valori meno casuali rispetto all'RTT.

Sulla base dell'RTT medio viene definito un intervallo fondamentale per il [[TCP]] detto **RTO**.
### RTO (Retransmission TimeOut)
L'RTO rappresenta il **tempo limite** entro il quale deve giungere un segmento di riscontro (Flag [[ACK]]) ad un segmento inviato. Trascorso questo tempo senza riscontro, il mittente invia nuovamente il segmento non riscontrato.

![[Pasted image 20251109205156.png]]

#### Importanza del valore di RTO
Il valore dell'RTO è fondamentale per le prestazioni offerte dalla rete:
- Se l'RTO è **troppo piccolo**, si avranno spesso ritrasmissioni dei segmenti perché il mittente li considera persi. A causa delle duplicazioni il traffico raddoppia, costringendo i router a smaltire il doppio dei pacchetti, compromettendone l'efficienza.
- Se l'RTO è **troppo grande**, viene ritrasmesso con eccessivo ritardo un segmento che potrebbe essere perso, rallentando il bit‑rate di trasmissione.

### Reset del timer di ritrasmissione
Il timer di ritrasmissione viene resettato in **4 casi**:

1. **Quando la coda dei segmenti in trasmissione è vuota** e comincia a riempirsi con i dati prodotti dal processo che li vuole mandare nel canale logico. In questo caso il flusso viene diviso in segmenti; se il buffer del destinatario è disponibile a riceverli, i segmenti vengono inviati in sequenza nel canale logico e può partire il timer di ritrasmissione associato al più vecchio segmento inviato e mai riscontrato.

2. **Quando si riceve un segmento non duplicato** a conferma che il più vecchio segmento inviato non è ancora stato ricevuto dal destinatario. In questo caso si può procedere con l'invio di nuovi segmenti se il buffer del destinatario può raccoglierli.

3. **Quando si raggiunge il tempo limite RTO**: in questo caso si invia nuovamente il più vecchio segmento inviato ma non ancora riscontrato.

4. **Nel caso dell'invio veloce** (Fast Retransmit).

### Invio veloce (Fast Retransmit)
Se nel periodo che intercorre tra l'azzeramento del timer e il raggiungimento del tempo limite RTO si ricevono **3 duplicati dello stesso segmento di ACK**, allora viene resettato il timer e inviato il segmento richiesto.

![[Pasted image 20251109215420.png]]