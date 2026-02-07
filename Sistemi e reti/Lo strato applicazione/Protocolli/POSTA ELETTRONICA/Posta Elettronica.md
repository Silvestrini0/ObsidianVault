Gli indirizzi hanno la seguente forma:
- nomeUtente@dominio
Il dominio è un nome simbolico del server che ospita il servizio di posta elettronica, il nome utente è una stringa univoca per il dominio scelta dall'utente.
Ogni utente può avere più indirizzi email.

**Le modalità di accesso al servizio di posta sono 2:**
- Una utilizza il protocollo [[POP3]] e si chiama per questo Pop Mail. (Outlook) (Thunderbird)
- L'altra utilizza una connessione a un sito web dedicato utilizzando il protocollo [[HTTPS]] e si chiama per questo Web Mail. (Gmail)

**Se si segue l'iter di una email dal mittente al destinatario si osservano i seguenti passaggi:**
- Si scrive l'email sul client di posta elettronica e la si inoltra.
- La mail raggiunge la casella di posta elettronica del mittente, cioè un'area di memoria presente in un server [[SMTP]] che ha in carico la casella di posta elettronica del mittente.
- Il server SMTP del mittente invia al server SMTP del destinatario l'email che raggiunge la casella di posta elettronica del destinatario. I protocolli di comunicazione tra client e server SMTP e tra due server SMTP è il protocollo SMTP.
- Il destinatario si collega quando vuole al server SMTP che ha in carico la propria casella utilizzando il protocollo [[POP3]] o [[IMAP4]] e scarica dal server l'email.

**I sottosistemi che gestiscono l'invio e il recapito delle email sono:**
- Il **MUA ( mail user agent )**, è il programma di gestione della posta presente sull' host mittente e su quello di destinazione. Presenta un'interfaccia grafica amichevole (user friendly ) per facilitare la scrittura, la modifica e l'invio della email. Per esempio Outlook, Gmail, Thunderbird.
- L' **MTA ( mail transfer agent )**, è il server che ha in carico le caselle di posta elettronica. 
Il MUA spedisce i messaggi all' MTA, l' MTA si occupa di rilevare i messaggi e del trasferimento ad altri MTA.


