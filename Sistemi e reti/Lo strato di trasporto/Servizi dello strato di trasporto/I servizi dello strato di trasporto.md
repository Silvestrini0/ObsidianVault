## Servizi

Un **servizio** è un insieme di funzioni e procedure che un livello mette a disposizione per il livello superiore.

Ecco i principali servizi dello [[Strato di Trasporto]]:

1. **Trasferimento affidabile**  
   Garantisce la consegna di tutti i segmenti nell'ordine corretto; in caso contrario il destinatario segnala l'anomalia al mittente. I segmenti vengono consegnati nello stesso ordine con cui sono usciti dalla sorgente, senza errori e senza duplicazioni. Il [[Protocollo]] che rende il trasferimento affidabile è il [[TCP]].

2. **Trasferimento non affidabile**  
   Il trasporto non affidabile garantisce solo l'indirizzamento (il mittente non saprà mai se ciò che ha spedito arriva a destinazione). Per questo tipo di trasferimento viene utilizzato l'[[UDP]].

Per entrambi è garantito il servizio di **[[Multiplazione e Demultiplazione]]** e un controllo sui bit trasportati.

### Multiplazione/Demultiplazione e SAP
Il multiplexing e il demultiplexing avvengono grazie al **SAP** (Service Access Point):
- È un'interfaccia logica tra un'[[Entità di rete]] di livello *n* e un'Entità di rete di livello *n-1*.
- Il SAP tra il livello applicativo e quello di trasporto (nel modello TCP/IP) è il [[Numero di porta]].

Attraverso l'Intestazione TCP (o UDP) vengono specificati:
- Numero di porta del processo mittente
- Numero di porta del processo destinatario

In questo modo è possibile instaurare contemporaneamente più comunicazioni tra processi in esecuzione su host remoti.

---

## Servizi specifici offerti da UDP e TCP

### Servizi offerti dal protocollo UDP
L'UDP fornisce solo:
1. **Multiplazione/Demultiplazione**:  
   - Nell'host sorgente, lo strato di trasporto prende i messaggi prodotti dai processi in esecuzione, li spezza e li ordina in una sequenza di segmenti, includendo in ognuno la porta sorgente e la porta di destinazione (multiplazione).  
   - Nell'host di destinazione, lo strato di trasporto riceve il flusso di segmenti e li smista tra i diversi processi di destinazione usando il numero di porta di destinazione come discrimine (demultiplazione).
1. **Controllo di integrità**:  
   Il mittente, prima di inviare il segmento, inserisce nell'intestazione una sequenza di **checksum** calcolata sull'insieme dati e intestazione del segmento. Il destinatario, quando riceve il segmento, ricalcola con lo stesso algoritmo il checksum: se il risultato è zero, il segmento è privo di errori.

### Servizi offerti dal protocollo TCP
Il TCP fornisce tutti i servizi seguenti (oltre a multiplazione/demultiplazione e controllo di integrità):

3. **Gestione della connessione**:  
   Lo strato di trasporto offre il servizio di instaurazione, gestione e chiusura della connessione tra i processi in comunicazione sul canale logico (3‑way handshake).

4. **Trasferimento affidabile dei segmenti**:  
   Lo strato di trasporto adotta una serie di meccanismi per rendere affidabile il canale logico creato tra i processi in comunicazione: eliminazione dei segmenti corrotti, compensazione delle perdite tramite ritrasmissione, ed eliminazione delle duplicazioni.

5. **Controllo del flusso dei segmenti**:  
   Viene gestito il flusso dei segmenti inviati dal mittente per evitare che lo strato di trasporto del destinatario si saturi; il numero di segmenti in volo deve essere minore dello spazio libero nel buffer di ricezione.

6. **Controllo di congestione dei router**:  
   Serve per evitare la congestione dei router intermedi che devono gestire lo smistamento dei pacchetti. Questo servizio è offerto con la collaborazione del campo TOS del livello IP.

**Riassunto**:  
- **UDP** offre esclusivamente i servizi di multiplazione/demultiplazione e controllo di integrità.  
- **TCP** fornisce tutti i servizi elencati.