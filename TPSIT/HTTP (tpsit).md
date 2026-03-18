# Evoluzione di HTTP

## HTTP/1.0
- **Modello non persistente**: per ogni richiesta il client apre una nuova connessione TCP, che viene chiusa al termine della risposta.
- **Problema**: scaricare una pagina composta da molte risorse (es. immagini, CSS) richiede l'apertura di numerose connessioni TCP indipendenti, aumentando la latenza e il carico sul server.

## HTTP/1.1

### Connessioni persistenti
- Consente di inviare più richieste e ricevere più risposte sulla stessa connessione TCP.
- La connessione non viene chiusa immediatamente, riducendo il numero di handshake TCP.

### Header Host
- Obbligatorio in HTTP/1.1.
- Permette il **virtual hosting**: più domini possono condividere lo stesso indirizzo IP. Il server legge l'header `Host` per determinare quale sito web servire.

### Pipelining
- Il client può inviare più richieste senza attendere le relative risposte.
- **Problema**: il server è obbligato a rispondere nello stesso ordine in cui sono arrivate le richieste (modello sequenziale).
- Una risposta lenta blocca tutte quelle successive → **Head‑of‑Line blocking a livello applicativo**.
- Il pipelining è stato poco utilizzato a causa di problemi di compatibilità con proxy intermedi e del rischio di blocco.

### Chunked transfer encoding
- Il server può inviare la risposta in blocchi (chunk) senza conoscere la lunghezza totale del contenuto in anticipo.
- Utile per contenuti generati dinamicamente (es. pagine che interrogano un database o ricevono dati da servizi esterni).
- Ogni chunk è preceduto dalla propria dimensione; il client ricostruisce il contenuto man mano che arriva.

### Caching migliorato
- In HTTP/1.0 esistevano meccanismi basilari come `Expires` e `If-Modified-Since`, basati sul timestamp.
- **HTTP/1.1** introduce:
  - `Cache-Control`: definisce politiche di caching precise (durata, visibilità, validità).
  - `ETag` (Entity Tag): identificatore univoco per una specifica versione di una risorsa.
  - Il client può usare `If-None-Match` con l'ETag per chiedere al server se la copia in cache è ancora valida.
  - Se la risorsa non è modificata, il server risponde con `304 Not Modified` (senza corpo), riducendo il traffico.

## HTTP/2.0 (2015)

### Architettura binaria
- I messaggi non sono più testo ASCII, ma vengono suddivisi in **frame** binari.
- Ogni frame contiene campi predefiniti: **Lunghezza**, **Tipo**, **Flag**, **Stream Identifier**, e il **Payload**.
- Il formato binario semplifica il parsing e riduce le ambiguità.
- Gli header non sono più inviati come stringhe: vengono codificati e compressi con **HPACK**.

### Multiplexing
- Una singola connessione TCP trasporta più **stream logici indipendenti**, ciascuno identificato da uno **Stream ID**.
- I frame dei diversi stream vengono interlacciati e inviati sulla stessa connessione.
- Il destinatario usa lo Stream ID per demultiplexare i dati e ricostruire i flussi originali.
- Elimina l'Head‑of‑Line blocking a livello applicativo (una risposta lenta non blocca le altre), ma permane il **blocco a livello TCP** (un pacchetto perso ferma tutti gli stream).

### Altre caratteristiche
- **Prioritizzazione degli stream**: il client può indicare l'importanza relativa di ogni stream.
- **Server push** (opzionale): il server può inviare risorse aggiuntive prima che il client le richieda esplicitamente.

## HTTP/3.0 (2022)

### Panoramica
- Standardizzato nella **RFC 9114**.
- Mantiene il modello a stream e l'architettura a frame di HTTP/2, ma sostituisce TCP con **QUIC** (basato su UDP).

### Vantaggi principali
- **Nessun Head‑of‑Line blocking a livello di trasporto**: la perdita di un pacchetto riguarda solo lo stream a cui appartiene, gli altri continuano a funzionare.
- **Handshake più rapido**: spesso 0‑RTT (zero round trip time) per connessioni ripetute grazie a QUIC.
- **Cifratura integrata**: TLS 1.3 è parte integrante di QUIC, non un livello separato.
- **Migrazione della connessione**: la connessione può sopravvivere a cambi di indirizzo IP (es. da Wi‑Fi a rete mobile).

### Compressione degli header
- Viene utilizzato **QPACK**, un adattamento di HPACK pensato per funzionare con il multiplexing di QUIC.

## QUIC (Quick UDP Internet Connections)

### Generalità
- Protocollo di trasporto sviluppato da Google, standardizzato nella **RFC 9000**.
- Opera sopra **UDP**, ma implementa al suo interno funzionalità di affidabilità, controllo della congestione e multiplexing.
- Obiettivo: superare i limiti di TCP nelle comunicazioni moderne.

### Affidabilità e controllo della congestione
- **Numeri di pacchetto** (Packet Number): ogni pacchetto QUIC ha un numero univoco che permette di:
  - Rilevare pacchetti persi.
  - Identificare duplicati.
  - Ricostruire l'ordine corretto.
- **Ack frame**: le conferme di ricezione non sono nell'header ma vengono trasportate come frame all'interno del payload dei pacchetti QUIC.
- Il mittente ritrasmette un pacchetto se non riceve l'Ack corrispondente.
- **Controllo della congestione**: implementato tramite algoritmi interni (simili a quelli TCP) che regolano dinamicamente la velocità di invio in base alle condizioni di rete.

### Multiplexing a livello di trasporto
- I dati vengono suddivisi in **frame** associati a **stream indipendenti**.
- Ogni stream è gestito separatamente, con il proprio meccanismo di affidabilità e controllo di flusso.
- I frame di stream diversi vengono interlacciati nei pacchetti QUIC, consentendo una comunicazione parallela e senza blocchi tra flussi.

### Sicurezza
- QUIC integra **TLS 1.3** direttamente, garantendo crittografia e autenticazione end‑to‑end fin dall'inizio della connessione.