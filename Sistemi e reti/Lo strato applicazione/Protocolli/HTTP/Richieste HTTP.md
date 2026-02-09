**Esistono diversi metodi utilizzabili nelle richieste HTTP i più famosi sono :**
- metodo **get**, che richiede semplicemente la risorsa.
- metodo **head**, è una richiesta al server in modo che la risposta contenga solo l'intestazione senza il body.
- metodo **post**, si possono inviare parametri di input al server organizzati in coppie del tipo nomeParametro = valoreParametro, si utilizza per esempio quando bisogna comunicare delle credenziali al server.
- metodo **put**, si utilizza per fare l'upload su server in un percorso specificato.
2- metodo **delete**, che permette di cancellare una risorsa.

**Alcuni servizi offerti dal DNS:**
- mappa gli ip con il nome simbolico
- host aliasing, cioè quando possono esserci più nomi simbolici equivalenti tra loro e il [[DNS]] associa ad essi il dominio del server corretto
- load distribution nel caso in cui più cloni dello stesso servizio sono in esecuzione su macchine differenti, il DNS dirotta il traffico sul server meno occupato.