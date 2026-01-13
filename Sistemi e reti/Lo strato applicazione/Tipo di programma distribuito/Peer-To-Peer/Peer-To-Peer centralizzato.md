Es.
( A ) che ha installato il programma peer to peer centralizzato con cadenza regolare comunica al server peer to peer di cui conosce l'ip la lista dei file che ( A ) vuole condividere e il socket su cui il processo ( A ) resta in ascolto.

Tutti gli altri dispositivi che hanno installato lo stesso programma peer to peer fanno la stessa cosa.

In questo modo il server centrale costruisce un database aggiornato con l'associazione  ( risorse ) : ( socket a cui richiede la risorsa ).

Un generico utente ( B ) che necessita di una risorsa interroga il database il quale comunica il socket del processo presso cui è possibile reperire la risorsa.

( B ) contatta quindi direttamente ( A ) e richiede la risorsa 