Le pagine dinamiche sono pagine il cui contenuto è costruito in maniera differente a seconda del client che fa la richiesta. Le pagine web dinamiche possono essere sia lato client, sia lato server.

**Lato client**
La pagina web dinamica lato client contiene oltre al codice html anche del codice java script incapsulato dentro del codice html.
Se apro una pagina web dinamica lato client con un'editor di testi trovo sia codice html sia codice java script.

Quando questa pagina arriva al browser, il motore js del browser interpreta il codice js.
L'esecuzione del codice produce il codice html, che viene sostituito al codice js.
Il browser può finalmente interpretare tutto il codice html e visualizzare la pagina

**Lato server**
Se la pagina web dinamica è lato server significa che incapsulato nel codice HTML della pagina c’è un programma scritto in un linguaggio eseguibile dal server( ad es. PHP). 
L’esecuzione di questo codice produce istruzioni HTML che vengono sostituite al codice del programma. La pagina diventa una pagina che contiene solo codice HTML e può essere inviata a browser. 

Spesso l’esecuzione PHP prevede un collegamento ad un database che si trova nella rete del server. Con le informazioni recuperate dal database è possibile costruire dei contenuti formattati in HTML in funzione dello specifico client che ha fatto la richiesta.
