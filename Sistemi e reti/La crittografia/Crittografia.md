Insieme delle tecniche che consentono di realizzare la cifratura di un testo in chiaro e la decifratura di un crittogramma.

La cifratura è un metodo grazie al quale un messaggio viene reso incomprensibile agli estranei. Per fare questo viene usato un algoritmo di cifratura che stabilisce una corrispondenza tra simboli in chiaro e i simboli cifrati ( la corrispondenza non è necessariamente biunivoca, cioè la cifratura può essere irreversibile Es. memorizzazione delle password nei server).

I simboli in chiaro si utilizzano per costruire un messaggio che si chiama PLAIN TEXT e una volta cifrato si ottiene il messaggio cifrato CIPHER TEXT.

Le regole della cifratura devono essere note ad entrambi gli estremi del canale di comunicazione. 

Esiste una differenza tra cifratura e codifica:

Con codifica s'intende un'algoritmo che mette in corrispondenza gli elementi di un'alfabeto sorgente con stringhe di opportuna lunghezza formate da simboli di un'alfabeto di codifica quindi si trasformano stringhe in altre stringhe senza la presenza di una chiave. Ad esempio è possibile associare ad una parola la stessa parola in un'altra lingua. 
Es. 8 bit associati al carattere ASCII.


Con cifratura si intende un' algoritmo di crittografia che prevede la sostituzione di ogni lettera con una o più cifre. Per esempio la sostituzione di un carattere con la posizione che occupa nell'alfabeto, ADA --> 141

Ogni algoritmo di cifratura è composto da due elementi la regola e la chiave:
- La regola è l'algoritmo parametrico utilizzato per la cifratura. 
- La chiave sono i valori che permettono di fissare univocamente le fasi dell'algoritmo; la regola è distribuita a chiunque ed è nota a chiunque, la sicurezza è garantita dalla non diffusione della chiave.

Esempio di algoritmo --> sostituire ogni carattere di una parola con il carattere che occupa n posizioni più avanti nell'usuale ordine alfabetico. La chiave è il valore di n che indica qual è la distanza tra la lettera in chiaro e quella che si vuole sostituire al posto di quella in chiaro nell'usuale ordine alfabetico. Se n vale 1 e la parola è ADA diventa BB.

vedi : [[Schemi crittografici]] 




























































