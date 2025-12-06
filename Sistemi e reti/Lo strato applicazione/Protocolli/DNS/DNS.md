(domain name system)
Si appoggia alla porta **UDP 53**.

Sistema che permette di determinare un'indirizzo ip partendo da un'indirizzo simbolico 
(www.scuola.it)

Per identificare l'interfaccia di rete di un dispositivo connesso ad una rete è necessario conosce il suo indirizzo ip.
Anche un sito internet è caricato in un server e per accedervi serve il suo indirizzo ip.
Gli esseri umani ricordano meglio un indirizzo simbolico per indicare un sito e le barra di ricerca del browser accettano tali tipi di indirizzi simbolici ([[URL]]).
I protocolli di trasporto accettano soltanto indirizzi ip.
Serve quindi un sistema che permetta di convertire un indirizzo simbolico nel rispettivo indirizzo ip.
In internet la risoluzione degli indirizzi simbolici in indirizzi ip è offerto dal DNS.

**Con DNS  si intendono due cose:**
- Un database distribuito che associa indirizzo simbolico con ip.
- Protocollo del layer applicazione che regola la comunicazione tra host e name server.

Es. 
Se apro il browser e inserisco un [[URL]] il protocollo [[HTTP]] estrae l'indirizzo simbolico e invoca il protocollo DNS a cui passa l'indirizzo simbolico.
Il protocollo DNS interroga il sistema dei server DNS partendo da quello locale a seguito dell'interrogazione si ottiene l'ip corrispondente all'indirizzo simbolico che passa al protocollo [[HTTP]]
Il protocollo invoca un protocollo di trasporto a cui passa indirizzo ip e porta

**Esistono 2 tipologie di server DNS:**
- Server Autoritativi, Sono i responsabili legali dell'associazione tra ip e indirizzo simbolico e sono i server che sono in grado di dare una risposta alle query DNS
- Server Competenti, non risolvono direttamente la query DNS ma sono in grado di indicare server più competenti di loro che forse sono in grado di risolvere la query DNS.

I server DNS sono collegati tra loro in modo da formare una struttura ad albero, alla sommità troviamo i server radice, tredici cloni distribuiti in tutto il mondo, il server radice è competente per tutti i domini di primo livello cioè conosce gli indirizzi ip dei server competenti per .com, .it eccetera, che si trovano gerarchicamente al livello inferiore.
Questi server inferiori ai server radice si chiamano TLD (Top Level Domain).

Prima di contattare un server radice, il browser interroga il proprio DNS locale.
Può essere un server della propria rete o un servizio attivato sul router di confine. se il server DNS locale non riesce a risolvere la query DNS allora comincia ad interrogare il DNS radice.

![[Pasted image 20251202120120.png]]

Es. di funzionamento del DNS nel caso peggiore

immagine

La modalità classica di interrogazione del sistema DNS è definita iterativa. In questo approccio il server radice è contattato dal DNS locale a cui spedisce direttamente l'indirizzo ip del server TLD competente per quella query. In questo modo la comunicazione con i DNS radice è la più breve possibile e il server radice viene liberato subito. 

Esiste anche una modalità ricorsiva per interrogare il sistema dei DNS. In questo caso il server DNS locale interroga il server radice, il server radice interroga il server TLD e il server TLD interroga l'ultimo server DNS che risulta autoritativo. La risposta alla query procede in senso inverso: dal server autoritativo la risposta giunge al server TLD, e dal server TLD arriva al server radice, che invia tutto al DNS locale.

Questa modalità occupa risorse elaborative del server radice in maniera eccessiva. 










