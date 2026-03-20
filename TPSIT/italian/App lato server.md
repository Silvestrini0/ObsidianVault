## Introduzione
Quando si parla di applicazioni lato server si fa riferimento a programmi che vengono eseguiti su server web e che hanno il compito di elaborare richieste provenienti da un client, tipicamente prodotte dal browser. Nel modello [[Client-Server]] web, il client invia una richiesta http con il browser, mentre il server risponde con una risposta http. 
## Pagine statiche/dinamiche 
Se il server restituisce un semplice file html si parla di contenuto statico.
Tuttavia molte applicazioni richiedono un comportamento dinamico, cioè la capacità di generare una risposta in funzione dei dati ricevuti dal client o dallo stato dell'applicazione.
Per realizzare questo tipo di funzionalità è necessario eseguire un codice lato server.
### CGI
Il CGI ( Common Gateway Interface ) è uno standard introdotto nei primi anni 90, che definisce un meccanismo attraverso il quale un server web riesce ad usufruire di programmi esterni per generare contenuti dinamici.

Prima delle diffusione delle tecnologie server side moderne il web server erano progettati principalmente per servire file statici. 

Il CGI nasce per superare questo limite, permettendo al server di delegare l'elaborazione delle richieste a programmi eseguibili in grado di produrre una risposta generata dinamicamente.

### Funzionamento 
Fasi di processo:
1. Il browser invia una richiesta HTTP,
2. Il server analizza l'[[URL]] richiesto e identifica che la risorsa corrisponde a uno script o un programma CGI,
3. Il server crea un nuovo processo nel sistema operativo,
4. All'interno di questo processo viene inserito il programma CGI,
5. Il server passa al programma le informazioni della richiesta tra cui:
	- Parametri della query string.
	- Dati inviati tramite form.
	- Header HTTP.
	- Variabili di ambiente, contenti informazioni sulla richiesta.
6. Il programma CGI elabora i dati ricevuti ed esegue la logica applicativa.
7. Il programma genera una risposta HTTP.
8. Il server accoglie l'output e lo invia al browser del client come risposta HTTP.
9. Il processo CGI viene chiuso.
Il server web trasmette le informazioni della richiesta al programma attraverso due meccanismi principali:
- #### Variabili d'ambiente:
	-  Request method, Indica il metodo HTTP utilizzato dal browser ( GET, POST ecc. ).
	-  Query string, contiene i parametri presenti nell'[[URL]], server per recuperare i dati 
	- Content length, indica il numero di byte presenti nel body della richiesta http e permette al programma CGI di conoscere la lunghezza dello standard input quando la richiesta utilizza il metodo post.
	- Content type.
	Queste variabili forniscono le info necessarie per interpretare le richieste HTTP necessarie per elaborare i dati inviati dal client.
- #### Standard Input:
	Quando una richiesta HTTP utilizza il metodo post i dati inviati dal client non vengono inseriti nell'[[URL]] ma nel body della richiesta http.