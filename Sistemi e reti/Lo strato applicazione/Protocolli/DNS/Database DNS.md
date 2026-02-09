
Esistono 4 tipi di record [[DNS]] contraddistinti da valori differenti del campo type. 

**I valori plausibili per il campo type:**
- A ( autoritativo ),
- NS (name server ),
- C name ( canonical name server ),
- MX ( mail sever ).

**Il generico record è composto da 4 campi:**
- name
- value
- type
- TTL.

**Ogni record assume caratteristiche differenti a seconda del contenuto del campo type. **
- Type = A, allora name contiene un indirizzo simbolico e value contiene l'indirizzo ip e TTL il tempo di vita del record. Se il server è autoritativo per quel dominio allora TTL vale infinito. Se invece il record è salvato temporaneamente nella cache di un DNS locale allora il TTL avrà un valore finito.
- Type = NS, nel campo value trovo l'indirizzo simbolico (dominio) del server che potrebbe essere in grado di risolvere il dominio posto nel campo name. Questo è il tipico record di un DNS competente. 
- Type = C name, nel campo value si trova il nome simbolico reale associato ad un nome simbolico alternativo presente nel campo name 
- Type = MX, nel campo value si trova il nome simbolico del mail server il cui dominio di posta elettronica è scritto nel campo name.

| Name                         | Value                                                        | Type | TTL                                 |
| ---------------------------- | ------------------------------------------------------------ | ---- | ----------------------------------- |
| indirizzo simbolico          | indirizzo ip                                                 | *A*    | tempo di vita del record (infinito) |
| indirizzo simbolico          | dominio del server competente per l'indirizzo nel campo name | *NS*   | tempo di vita del record            |
| nome simbolico               | nome simbolico reale associato al nome del campo name        | *C*    | tempo di vita del record            |
| dominio di posta elettronica | nome simbolico mail server                                   | *MX*   | tempo di vita del record            |
