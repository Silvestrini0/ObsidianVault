## Transmission Control Protocol (TCP)

Il TCP è un [[Protocollo]] **orientato alla connessione** che offre:
- Controllo di integrità
- Verifica automatica di consegna dei segmenti
- Ritrasmissione dei segmenti corrotti

### Affidabilità
Lo strato di rete (IP) non è affidabile: possono verificarsi perdite di pacchetti ed errori di trasmissione. Lo scopo del livello di trasporto (TCP) è eliminare queste incertezze garantendo una consegna affidabile al processo di destinazione.

Per “affidabile” si intende:
- Tutti i messaggi sono recapitati **privi di errori**.
- **Nessun duplicato**.
- I messaggi sono consegnati **nello stesso ordine** in cui sono stati trasmessi.

### Strategie del TCP
Per offrire il servizio di connessione affidabile, il TCP adotta tre strategie:
1. **Numerazione** dei segmenti trasmessi e dei riscontri.
2. **Timer di ritrasmissione** (RTO): alla scadenza viene spedito il più vecchio segmento non ancora riscontrato.
3. **Finestre scorrevoli** (in trasmissione e ricezione) per controllare il flusso.

### Stabilimento della connessione (Handshake)
Prima di trasferire dati, mittente e destinatario stabiliscono i parametri di connessione tramite una fase di handshake. Tra questi:
- **ISN** (Initial Sequence Number): numero di sequenza iniziale generato casualmente; il primo byte inviato avrà numero `ISN + 1`.
- **WS** (Window Scale, opzionale): ampiezza in byte della finestra di trasmissione; il destinatario la comunica dinamicamente in base allo stato del buffer di ricezione.

La connessione logica viene instaurata tramite la **stretta di mano a 3 vie** (3‑way handshake). Successivamente avviene la comunicazione bidirezionale affidabile.

### Intestazione TCP
![[Pasted image 20251109225305.png]]

#### Dimensioni e MSS
- MTU massimo di IP: $2^{16}$ byte.
- Intestazione IP: 20 byte.
- Intestazione TCP: 20 byte.
- **MSS** (Maximum Segment Size) massimo teorico: $2^{16} - 40$ byte.
- In Ethernet (MTU 1500 byte): MSS = $1500 - 40 = 1460$ byte.

#### Campi principali dell'intestazione
- **Lunghezza intestazione TCP**: espressa in parole da 32 bit (4 bit).
- **CWR** (Congestion Window Reduced): =1 se l’host sorgente ha ridotto la velocità per alleviare la congestione.
- **ECE** (Explicit Congestion Echo): usato per segnalare congestione imminente (insieme al campo TOS di IP).
- **URG** (Urgent): =1 → il campo **Urgent Pointer** è valido.
- **ACK** (Acknowledgment): =1 → il campo **Ack Number** è valido.
- **PSH** (Push): forza l’invio immediato del segmento senza attendere il riempimento del buffer.
- **RST** (Reset): =1 → indica il rifiuto della connessione o la richiesta di ripristino.
- **SYN** (Synchronize): =1 nelle fasi di handshake per sincronizzare i numeri di sequenza.
- **FIN** (Finish): =1 → indica la volontà di chiudere la connessione in una direzione.