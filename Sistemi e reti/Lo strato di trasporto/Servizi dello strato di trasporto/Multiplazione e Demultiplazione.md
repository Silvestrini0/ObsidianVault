## Multiplazione (Multiplexing)
I dati prodotti da un processo mittente vengono suddivisi in segmenti nella cui intestazione viene inserito il [[Numero di porta]] sorgente e il [[Numero di porta]] di destinazione; in questo modo è univoco quale sia il [[Canale Logico]] su cui deve essere spedito il segmento.

Questa tecnica di inserire il numero di porta sorgente e di destinazione permette di generare un flusso multiplato.

## Demultiplazione (Demultiplexing)
Lo strato di trasporto del destinatario è in grado di distribuire i segmenti ai processi a cui sono destinati utilizzando il [[Numero di porta]] di destinazione come discrimine.