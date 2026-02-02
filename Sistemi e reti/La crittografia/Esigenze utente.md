Le reti per loro stessa natura non sono ambienti sicuri nel senso che qualsiasi canale di comunicazione condiviso può portare informazioni a chiunque anche a quelle stazioni a cui l'informazione non è diretta.

Es. 
Reti a bus, reti a stella con hub, reti wlan con chiave di accesso condivisa, sono tutti esempi di condivisione del canale di comunicazione. 

Le esigenze di un'utente che vuole scambiare informazioni in modo sicuro attraverso la rete sono 3:
- Segretezza,
- Autenticazione dell'utente,
- Affidabilità del documento.

Con **segretezza** si intende la possibilità di trasferire informazioni che siano comprensibili solo a chi ha i diritti, cioè solo alle persone autorizzate.

Con **autenticazione** si intende il processo di riconoscimento delle credenziali di un utente in modo che sia impossibile che qualcuno finga di essere qualcun' altro (è utile quando si deve autenticare il mittente di un messaggio o quando un server ha la necessità di conoscere l'identità del client).

Con **affidabilità** si intende la garanzia di poter stabilire l'originalità o meno di un documento cioè, che questo non sia stato modificato nel transito attraverso il canale di comunicazione insicuro.

E' possibile mettere in alto delle strategie per garantire la sicurezza a diversi livelli della pila protocollare.
Es. Layer fisico --> crea una linea dedicata --> isolamento (il più efficacie)
ES Layer Datalink --> è possibile cifrare il campo DATI PAD questo implica che la comunicazione deve avvenire all'interno dello stesso dominio di broadcast. Perché il routing non sarebbe possibile, dal momento che gli indirizzi ip verrebbero cifrati
E' solo a livelli superiori al livello di trasporto possono essere garantiti tutte le esigenze di sicurezza attraverso la [[Crittografia]].