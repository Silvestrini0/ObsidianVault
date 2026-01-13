(file transfer protocol) 
Si appoggia alla porta TCP 20/21.
Download e upload di file binari su server FTP.

![[Pasted image 20260113174050.png]]

Il protocollo FTP si usa per trasferire file e si appoggia al protocollo TCP.
Usa 2 connessioni TCP separate:
- Una di controllo/comando
- Una di trasferimento dati
Il server FTP è in ascolto sulla porta 20 e 21.
- La porta 21 individua l'estremità del canale logico di controllo
- La porta 20 individua l'estremità del canale logico dati

FTP usa il modello architetturale [[Client-Server]], quindi c'è un processo client in esecuzione sull'host che vuole ricevere il file e un processo server FTP in esecuzione sulla macchina che vuole ricevere il file, e un processo server FTP in esecuzione sulla macchina che contiene il file da distribuire.

Il software FTP del server deve poter garantire:
- Il download e l'upload di file.
- Il Resume (Ripristino) dei trasferimenti interrotti,
- L'eliminazione e la rinomina dei file.
- La creazione di Directory.
- La possibilità per un'utente di autenticarsi.

Il software FTP client ha due componenti:
- Interfaccia grafica,
- Motore FTP che permette la comunicazione tra client e server.
Il software deve garantire:
- La connessione al server FTP remoto.
- La possibilità di richiedere un upload o un download.
- La possibilità di navigare ( il file system del server ) come se fosse in locale.
- Permettere la lettura del contenuto della Work Directory del server.
- Deve poter interrompere la comunicazione unilateralmente col server.

Esistono due modi di funzionamento, ATTIVA e PASSIVA.
