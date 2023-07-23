### [[DIVIDE ET IMPERA]]
Se devo tenere organizzato qualcosa di molto grande è difficile, ma se lo si divide in tante parti che faccio gestire in maniera semi-autonama e coordino le attività le cose dovrebbero funzionare meglio.

Noi, per esempio, ci riferiamo a questo metodo quando dividiamo un array in 2 parti, si ordinano indipendentemente i due risultati e li si mettono assieme


## [[MERGE SORT]]
```pseudocodice linenos title:"Merge Sort" collapse
MergeSort(A,p,r) 
if p<r 
	q = app_diffetto((p+r)/2) //indice che sta in mezzo tra p e r
	MergeSort(a,p,q)  //ordina la prima metà
	MergeSort(a,q+1,r)//ordina la seconda metà
	Merge(A,p,q,r)
```
Spiegazione:
1) riceve 3 parametri: l'array da ordinare, l'indice del primo elemento (p) e l'indice dell'ultimo elemento(r)
2) Quando la condizione fallisce?
>Se p>r, allora significa che c'è stato un errore nell'inserimento dei parametri
>Se p=r, allora significa che la dimensione dell'array è 1, è già ordinato

3) Calcola q come la mediana tra p e r. Dobbiamo gestire il caso se (p+r)\2 da un numero con la virgola, per fare questo usiamo una funzione per approssimare per difetto
4) Richiama il MergeSort nella prima metà
5) Richiama il MergeSort nella seconda metà
6) Chiama una funzione Merge (spiegata sotto) che prende come parametri l'Array, l'indice del valore finale, la mediana e l'indice del valore finale

```pseudocodice linenos title:"Merge" collapse
Merge(A,p,q,r)
i=1
j=p
k=q+1
while(j<=q OR k<=r)
	IF (j<=q AND (k>r OR A[j]<=A[k]))
		B[i] = A[j]
		j = j+1
	ELSE
		B[i] = A[k]
		k = k+1
	i = i+1
for i =1 to r-p+1
	A[p+i-1] = B[i]
		
	

```
Spiegazione:

5.  Il ciclo while continua finchè ci sono elementi da copiare in almeno una delle due metà. Quando una metà è finita, il valore del suo indice sarà superiore al valore del suo indice massimo
6. j deve puntare ad un elemento valido (j<=q) E (o l'altro canditato non è valido (k>r) o l'altro candidato A[k] è più grande di A[j])
7. B è un nuovo array (alla fine sarà l'array ordinato)
8. 
9.  L'ELSE non ha nessuna condizione di controllo per controllare se effettivamente il valore indicizzato nella seconda metà. Perchè?
> Sappiamo che se dobbiamo predere un elemento della prima metà, allora non lo dobbiamo prendere dalla seconda nello stesso ciclo. Di conseguenza, se non dobbiamo prendere l'elemento della prima metà, allora dovremo prendere l'elemento della seconda.
> Siamo dentro al ciclo while, quindi sappiamo che c'è un elemento da inserire. (in altre parole, sappiamo che l'indice della seconda metà non ha superato il suo indice massimo se siamo dentro il while e l'elemento puntato dall'indice della prima metà non è valido)
>
10. 
11. 
12. 
13. Abbiamo l'array ordinato in B, non in A, quindi dobbiamo copiare tutti gli elementi di B in A. Perchè c'è r-p+1?
> Stiamo ordinando una parte dell'array, non tutto l'array. Per esempio se l'array originale è ha 8 elementi, noi abbiamo in B i valori o dei primi 4 elementi (ordinati) o i valori degli ultimi 4 elementi (ordinati).L' r-p+1 si può quindi tradurre in: la differenza tra l'indice massimo del sottoarray(r) e l'indice minimo (p) sommata a 1 perchè noi indicizziamo gli array ad 1, non a 0. Questo rappresenta la dimensione del sottoarray

 14. Perchè andiamo a copiare l'elemento di B[i] in A[p+i-1]?
 > Discorso simile al punto 13. B è una sottostringa di A, quindi dobbiamo trovare il modo di convertire la posizione dell'indice B nella posizione corretta dell'indice A. p+i-1 quindi equivale a (indice minimo della sottostringa+i-1 (il -1 è perchè noi indicizziamo gli array da 1))
 
### ESEMPIO
In questo esempio gli esponenti stanno per l'indice di posizione e il pedice sta ad indicare la posizione originaria nell'array

Abbiamo l'array ($5^1_1$,$2^2_2$,$4^3_3$,$6^4_4$,$1^5_5$,$3^6_6$,$2^7_7$,$6^8_8$). Al merge sort passiamo l'array, indice minimo (1) e l'indice massimo (8).Calcoliamo q, la mediana, che è uguale a 4.
Chiamiamo il MergeSort nella prima metà dell'array, mettendo come parametri l'array stesso, l'indice minimo (1) e l'indice massimo raggiungibile dal sottoarray (4) 
>Abbiamo l'array ($5^1_1$,$2^2_2$,$4^3_3$,$6^4_4$). q = 2. Chiamiamo il MergeSort nella prima metà dell'array, mettendo come parametri l'array stesso, l'indice minimo (1) e l'indice massimo raggiungibile dal sottoarray (2)
>> Abbiamo l'array ($5^1_1$,$2^2_2$). q=1. Chiamiamo il MergeSort nella prima metà dell'array, mettendo come parametri l'array stesso, l'indice minimo (1) e l'indice massimo raggiungibile dal sottoarray(1).
>>>Abbiamo l'array ($5^1_1$),  p e r sono uguali, l'array è ordinato perchè composto da un solo elemento.
>>
>>>Abbiamo l'array($2^2_2$),  p e r sono uguali, l'array è ordinato perchè composto da un solo elemento.
>>
>>Abbiamo stabilito che le due metà sono ordinate. Chiamiamo il Merge con parametri l'array stesso, l'indice minimo raggiungibile dal primo sottoarray, l'indice massimo ragigungibile dal primo sottoarray e l'indice massimo raggiungibile dal secondo sottoarray
>>- Inzia la funzione Merge. 
>>- Calcoliamo il valore di k come 2. Visto che 1<=1 e che 2<=2, entriamo nel  ciclo while. L'if non viene eseguito perchè, anche se 1<=1, A[k=1]=5 è più grande di A[j=2]=2. Viene eseguito l'else, in cui diamo a B[i=1] il valore di A[j=2]. Aggiungiamo 1 a j. Prima di iniziare il nuovo ciclo, aggiungiamo 1 ad i
>>- 2 ciclo while, 1<=1 ma 3!<=!2. Tuttavia la condizione è un OR, quindi si può entrare comunque nel ciclo. L'IF viene eseguito perchè 1<=1 e k=3>r=2. Salviamo in B[i=2]  A[k=1]=5. Aggiungiamo 1 a k. Prima di iniziare il nuovo ciclo, aggiungiamo 1 ad i.
>>- 3 ciclo while 2!<=!1 e 3!<=!2. Non si entra nel ciclo while.
>>
>>Abbiamo finito con il ciclo while, adesso dobbiamo eseguire il for.
>>- Il for inzierà da i=1 e finirà con i = r(2)-p(1)+1=2
>>- Al primo ciclo A[p(1)+i(1)-1=1] sarà uguale a B[i=1]=2
>>- Al secondo ciclo A[p(1)+i(2)-1=2] sarà uguale a B[i=2]=5
>>
>>Abbiamo finito di ordinare questo sottoarray, l'array complessivo sarà 
>>($2^1_2$,$5^2_1$,$4^3_3$,$6^4_4$,$1^5_5$,$3^6_6$,$2^7_7$,$6^8_8$)
>
>Abbiamo l'array ($4^3_3$,$6^4_4$). Seguendo il ragionamento descritto precedentemente, l'array complessivo sarà ($2^1_2$,$4^2_3$,$5^3_1$,$6^4_4$,$1^5_5$,$3^6_6$,$2^7_7$,$6^8_8$)

Dobbiamo fare lo stesso lavoro per la seconda metà. Mi limito a scrivere il risultato
($1^1_5$,$2^2_2$,$2^3_7$,$3^4_6$,$4^5_3$,$5^6_1$,$6^7_4$,$6^8_8$)
___
#### COMPLESSITA ALGORITMO MERGE SORT
Quando invochiamo il MergeSort su un array di dimensione n, nel caso base (Array ha 1 elemento), facciamo un lavoro costante. Nel caso ricorsivo, invece, prima dobbiamo calcolare la mediana, poi effettuiamo MergeSort su un oggetto di dimensione n/2 (approssimato per difetto) e un MergeSort su un oggetto di dimensione n/2 (approssiamto per eccesso). Infine si evoca la Merge. In formula:
$$\Upgamma(n) = \Upgamma(\lfloor\frac{n}{2}\rfloor)+\Upgamma(\lceil\frac{n}{2}\rceil)+ \Upgamma(Merge)$$
Visto che abbiamo già visto che le approssimazioni per eccesso e difetto sono irrilevanti, possiamo riscrivere la formula come:
$$\Upgamma(n) = 2\Upgamma(\frac{n}{2})+\Upgamma(Merge)$$
Dobbiamo calcolare quanto vale $\Upgamma(Merge)$.
>L'IF ha tempo costante di esecuzioni, così come il then e l'else e il i = i+1. Possiamo quindi dire che tutto quello che è all'interno del while è tempo costante.
>Il while viene eseguito in n
>>Sappiamo che il massimo tempo del while è uguale a n (se fosse maggiore allora gli indici uscirebbero fuori dai loro confini). Sappiamo inotre che n è il tempo minimo perchè:
>>>All'inizio gli indici delle due metà possono percorrere massimo $\frac{n}{2}$spazi e sappiamo che al ciclo successivo una delle due metà ha compiuto 1 passo. Di conseguenza per finire il numero di passi che hanno a disposizione, dobbiamo aspettare $\frac{n}{2}+\frac{n}{2}=n$

L'equazione di ricorrenza è quindi:
$$\Upgamma(n) = 2\Upgamma(\frac{n}{2})+n$$
$a=2 \quad b=2, f(n)=n$
$n^{log_b{a}}= n^{log_2{2}}=n^1$
Le due parti (vedere lezione 5 per spiegazione) hanno lo stesso ordine
Siamo nel caso 2
$$\Upgamma(n) \in O(n\log{n})$$
Questo algoritmo impiega sempre lo stesso tempo per eseguire, sia nel caso peggiore, che nel caso migliore.

___
Quanta memoria extra usa il MergeSort? 
>Dobbiamo creare un array B la cui dimensione, alla fine, è la stessa dell'array A. Di conseguenza serve n memoria extra NON costante. L'algoritmo MergeSort [[ORDINAMENTO IN LOCO|non è in loco]].

Cosa succede agli elementi uguali?
> Non vengono scambiati. L'algoritmo è [[ORDINAMENTO STABILE|stabile]]. Perchè non vengono scambiati?
>>Nell'IF della funzione Merge, noi controlliamo se A[j]<=A[k]. Quando sono uguali diamo priorità all'elemento di sinistra, che nell'array originale si trova prima.

Cosa succede se applichiamo il[[MERGE SORT|merge sort]] ad un array già ordinato?
>La complessità rimane la stessa $O(n\log{n})$

Quando conviene usare il[[MERGE SORT|merge sort]] ?

Come è implementato in programmi?
>Si crea una funzione MergeSort con 2 parametri, l'array da ordinare e la lunghezza dell'array (se il linguaggio che si usa permette di ottenere in tempo costante la lunchezza dell'array questo parametro non serve).
>La funzione MergeSort inizializza già l'array B e, al posto di richiamare se stessa, richiama una funzione privata (DoMergeSort) (questa nuova funzione fa la stessa cosa dell'argomento descritto). Alle funzioni DoMergeSort Merge passiamo, oltre ai parametri già discussi, l'array B. Perchè facciamo questo?
>>Con l'algoritmo senza il DoMergeSort, l'array B viene continuamente allocato e distrutto, intasando il garbage collector e rallentando considerevolmente il programma. Usando il DoMergeSort l'array B viene invece creato solo 1 volta e poi riutilizzato senza distruggerlo.

___
#### ESERCIZIO 
Sappiamo che l'[[INSERTION SORT]] è O($n^2$) e che il [[MERGE SORT]] è O($n\log{n}$). Serve sapere il valore delle costanti?

Ordiniamo 1 milione di dati

Caso A:
>Computer potente, 100 milioni di istruzioni al secondo
>Insertion sort efficiente $2n^2$
>t = $\frac{2*(10^6)^2}{10^8}= 2*10^4 =$ 5.56 ore

Caso B:
>Computer scarso, 1 milione di istruzioni al secondo
>Merge sort implementazione inefficiente: $50 n\log{n}$
>t = $\frac{50*10^6*\log_10{10^6}}{10^6}=300$ secondi = 5 minuti
>t = $\frac{50*10^6*\log_2{10^6}}{10^6}=$ 17 minuti

Nonostante le costante del caso B fossero peggiore per la durata totale del calcolo, il tempo di B è nettamente inferiore rispetto al caso A. Questo perchè le costante sono poco significative.

Abbiamo calcolato il caso B con 2 basi per il logaritmo. Quale è quello giusto?
>Non è importante (a meno che vogliamo fare calcoli specifici) visto che la base fa cambiare la costante.



