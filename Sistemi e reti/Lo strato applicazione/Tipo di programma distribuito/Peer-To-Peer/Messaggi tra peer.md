I messaggi che possono scambiarsi i peer all'interno dell'architettura [[Peer-To-Peer]] sono cinque:
- **ping**, è un messaggio di discover dei nodi
- **pong**, è la risposta ad un ping e contiene un socket di conferma
- **query**, è un messaggio per localizzare una risorsa
- **query hit**, è un messaggio di risposta ad una query e contiene le informazioni per ottenere la risposta
- **push**, è un messaggio che permette il download del file utilizzando il protocollo http
La propagazione dei messaggi di query tra le varie overlay network si chiama flooding. 
