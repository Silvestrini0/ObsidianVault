# Introduzione
Un sistema informativo deve garantire : 
- Riservatezza
- Integrità 
- Disponibilità 
Se una di queste proprietà viene compromessa si verifica un'incidente di sicurezza.
# Principi di Sicurezza (Saltzer e Schroeder)
Sono stati introdotti da Saltzer e Schroeder e rappresentano le linee guida per la progettazione di sistemi informatici, definiscono come gestire privilegi e meccanismi di protezione riducendo vulnerabilità e superfici di attacco.
### 1° Principio : Least Privilege
Secondo questo principio ogni utente, processo, o applicazione deve possedere solo i privilegi necessari a svolgere il lavoro.
### 2° Principio : Fail-safe Defaults
Fa si che il sistema deve essere progettato in modo tale che in assenza di una regola specifica ( esplicita di autorizzazione ).
Questo significa che i permessi devono essere concessi in modo esplicito e consapevole
### 3° Principio : Economy of Mechanism 
I meccanismi di sicurezza devono essere semplici e comprensibili, un sistema complesso è più difficile da configurare e quindi è più facile sbagliarne la configurazione.
### 4° Principio : Complete Mediation 
Ogni richiesta di accesso ad una risorsa deve essere controllata ogni volta.
### 5° Principio : Open Design (progetto aperto)
La sicurezza non deve dipendere dal segreto dell'algoritmo ma solo dalla segretezza della chiave.
### 6° Principio : Separation of Privilege
Il principio stabilisce che per autorizzare un'operazione critica ( importante ) non basta avere un singolo controllo ma deve essere necessario il soddisfacimento di più condizioni indipendenti.
### 7° Principio : Least common Mechanism  
Questo principio stabilisce che le risorse e i percorsi di comunicazione non dovrebbero essere condivisi tra utenti o processi diversi an meno che non sia strettamente necessario.
### 8 Principio : Psychological Acceptability
Le misure di sicurezza devono essere progettate per essere semplici e per quanto possibile il più naturale possibile per l'utente finale. Quindi se una procedura di sicurezza è troppo complessa l'utente cercherà di aggirarla, annullando di fatto ogni protezione 
# Guida alle minacce naturali e alle contromisure 

