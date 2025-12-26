Ecco i principali [[Servizi]] dello [[Strato di Trasporto]] :
- [[Il trasferimento affidabile]]
- [[Il trasferimento non affidabile]].

Per entrambi è garantito il servizio di  [[Multiplazione]] e [[Demultiplazione]] un controllo sui bit trasportati. Il multiplexing e il demultiplexing avviene grazie al [[SAP ( service access point )]] di trasporto ([[Numero di porta]] processo mittente, [[Numero di porta]] processo di destinazione).
[[Intestazione TCP]]
In questo modo è possibile instaurare contemporaneamente più comunicazioni tra più processi in esecuzione su host remoti.

-- da sistemare 
SERVIZI DELLO STRATO DI TRASPORTO:
UDP:
1. Multiplazione de multiplazione: host sorgente lo strato di trasporto
prende I messa 61 prodotti dai processi in esecuzione li spezza e 21
ordina in una sequenza di segmenti includendo in ogni uno di essi la
porta sorgente e la porta di destinazione (multiplazione);
- Nell'host di destinazione lo strato di trasporto riceve un flusso scomposi
di segmenti che vengono smistati;
- E riordinati tra I diversi processi di destinazione usando il numero di
porta di destinazione come discrimine;
2. Gestione della connessione: lo strato di trasporto offre il servizio di
instaurazione, gestione e chiusura della connessione dei processi in
comunicazione sul canale logico( 3 WH );
3. Controllo di integrità il mittente prima di inviare il segmento inserisce
nell'intestazione una sequenza al checksum calcolata sull'insieme dati e
intestazione del segmento. Il destinatario quando riceve il segmento
ricalcola con lo stesso algoritmo di checksum se il risultato sono tutti
allora il segmento è privo di errori;
4. Trasferimento affidabile dei segmenti lo strato di trasporto adotta una
serie di meccanismi per rendere affidabile a casale logico creato tra I
processi in comunicazione eliminando I segmenti corrotti e compensano
le perdite ion richiesta di ritrasmissione ed eliminando le duplicazioni;
5. Controllo del flusso dei segmenti viene gestito il flusso dei segmenti inviati dal
mittente per evitare che lo strato di trasporto del destinatario si saturi cioè il
numero dei segmenti in volo deve essere minore dello spazio libero nel buffer
di ricezione;
6. Controllo di congestione dei router: serve per evitare la congestione del
buffer di ricezione di tutti I rovi intermedi che devono gestire lo smistamentodei pacchetti. Testo servizio è offerto con la collaborazione del campo TOS
del layer ip;

Il protocollo UDP offre esclusivamente il servizio di multiplazione/ demultiplazione
il controllo di integrità, Il tcp li fornisce tutti.

