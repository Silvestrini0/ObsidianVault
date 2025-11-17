( Transmition Control Protocol )
Il TCP è un [[Protocollo]] orientato alla connessione, consente il controllo d'integrità e dispone di un sistema automatico per la verifica di consegna di un segmento e un sistema che richiede la trasmissione dei segmenti corrotti.

Lo strato di rete (IP) implementa un protocollo che non è affidabile. Cioè si possono perdere pacchetti e si possono verificare errori di trasmissione. Il protocollo IP è sicuramente in grado di recapitare i suoi dati ad una qualsiasi interfaccia di rete ma essere in grado non significa riuscirci sempre.

Lo scopo del livello di trasporto è quello di eliminare queste incertezze e garantire una consegna affidabile al processo di destinazione ( [[Protocollo]] [[Protocollo TCP]]).
Per affidabile s'intende:
- Tutti i messaggi sono recapitati al processo di destinazione privi di errori,
- Non vengono consegnati duplicati,
- I messaggi sono consegnati nello stesso ordine con cui sono stati trasmessi.

Per offrire il servizio di connessione affidabile il TCP adotta 3 strategie:
- Numerazione dei segmenti trasmessi e ritrasmissione di riscontri anch'essi numerati,
- Impiego di un timer di ritrasmissione ([[RTO]]) scaduto il quale viene spedito il più vecchio segmento inviato non ancora riscontrato.
- impiego di finestre scorrevoli sia in trasmissione sia in ricezione che indicano quanti byte il destinatario può ricevere senza saturare il buffer di ricezione.

Prima di iniziare un inserimento di dati è necessario stabilire una serie di parametri utilizzati nel collegamento. Esiste quindi una fase di " hand shake" nella quale mittente e destinatario stabiliscono parametri di connessione. Tra questi c'è l'[[ISN]] e il numero d'ordine del primo byte inviato sarà pari a [[ISN]] + 1.

Un'altro parametro che viene stabilito è il [[WS]].

In particolare prima di trasferire i dati è necessario instaurare la connessione logica, e questo viene fatto con la stretta di mano a 3 vie (3WHS). Dopo l'instaurazione della connessione logica avviene la comunicazione informativa affidabile e bidirezionale.

