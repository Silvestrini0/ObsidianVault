Gli host sono collegati allo stesso canale di comunicazione tramite connettori vampiro. Se un host vuole inviare un messaggio deve controllare prima se il canale di comunicazione è libro. Questo non esclude una collisione tra frame.

![[Pasted image 20260305102227.png]]

Se viene rilevata una collisione, una stazione smette trasmettere la sequenza d bit originale e allega in coda una sequenza di disturbo chiamata **Jam** composta da 48 bit di alterni 0 e 1. 
La sequenza originale di bit seguita dal Jam, si chiama frame di collisione . 
Terminato l'invio del frame di collisione, la stazione che ha rilevato la collisione si mette in silenzio radio per un tempo stabilito casualmente. 
Si spera che tutt le stazioni che hanno rilevato la collisione generino tempi di silenzio radio differenti.