Ci sono coppie di host di pari importanza che scambiano risorse nei 2 sensi. le risorse non sono concentrate su un unico host ma sono distribuite tra i peer.

Con peer to peer ci si riferisce ad una classe di sistemi che utilizzano un sistema di risorse distribuite una funzionalità in modo decentralizzato.

**Sotto casi di peer to peer:**
- [[Peer-To-Peer centralizzato]], esiste un processo server che contiene il mapping tra risorse e socket presso cui si trova la risorsa.
- [[Peer-To-Peer decentralizzato]], non esiste un server centrale che contiene il mapping delle risorse, ma esiste un server di host caching che raccoglie i socket dei processi remoti che sono attivi sulla rete in quel momento.

**Svantaggi del peer to [[Peer-To-Peer decentralizzato]]:**
- Il flooding, congestiona la rete con un numero di segmenti che cresce esponenzialmente ad ogni nuovo inoltro. Per questo è necessario inserire un TTL.
- I tempi di ricerca sono imprevedibili.
- Il raggio di ricerca è limitato dal TTL, cioè non si sonda tutta la rete.
- Esistono una serie di messaggi di query che non producono query hit che congestionano inutilmente la rete.

**Vantaggi del [[Peer-To-Peer decentralizzato]]:**
- Il server di host caching non cataloga contenuti e quindi non può infrangere nessuna norma di copyright: la responsabilità è del singolo peer.
- Viene incrementata la privacy e l'anonimato delle operazioni svolte.
- Il sistema è fortemente scalabile, cioè l'aggiunta o la rimozione di un nuovo processo è molto semplice. 
- La stessa risorsa può trovarsi su più peer garantendo download paralleli.