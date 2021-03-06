# Introduzione #
Il programma vuole simulare una comunicazione radio effettuata con il codice Morse (riferito anche come c.m. in seguito). Al posto delle radiofrequenze viene utilizzata la suite di protocolli TCP/IP. In un modello reale, il destinatario riceve solo i suoni che sono stati digitati dal mittente; il programma, al fine di semplificare la conversione, riproduce i suoni relativi e visualizza anche la loro rappresentazione in lettere dall'alfabeto, convertendoli.

Il linguaggio utilizzato è il C#, con piattaforma .NET.


# Architettura #

Gli elementi utilizzati dal c.m. sono, fondamentalmente, il punto (".") ed il trattino ("-"). Il c.m. prevede che il trattino abbia una durata tripla rispetto a quella del punto semplice, considerato come unità temporale minima; è però lasciato alla comunicazione stabilire quanto questo valga nella stessa.
Non c'è distinzione tra client e server: entrambi i comunicanti possono inviare/ricevere, ma non parallelamente poiché la connessione è trattata come half-duplex.


## Protocollo ##
La comunicazione è basata sul modello TCP/IP, utilizzando socket (classe System.Net.Sockets) asincroni affinché il processo principale non venga bloccato da una delle primitive di I/O.  
Ottenuto l'input (vedi §Input), che è stato già validato affinché contella solamente combinazioni valide nell'alfabeto Morse, si procede all'invio al ricevente.  

Il mittente invia al ricevente quanto letto in input. Affinché sia in grado di distinguere le lettere ricevute, è inserito un `\` tra esse. Esempio:
`....\.\.-..\.-..\---` ossia "h\e\l\l\o".



# Input # 
[...]  
L'alfabeto Morse utilizzato è quello internazionale, visualizzabile [qui](http://www.itu.int/dms_pubrec/itu-r/rec/m/R-REC-M.1677-1-200910-I!!PDF-E.pdf). Sono supportate le 26 lettere dell'alfabeto Inglese; i numeri 0-9 verrano presi in carico in future release.

