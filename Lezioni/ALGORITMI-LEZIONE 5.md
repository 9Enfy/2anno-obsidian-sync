___

Alla lezione 4 ci eravamo fermati con questa formula:
$$\le n^{\log_4{3}}+4n = O(n)$$ 
La lezione 5 continuerà questo esercizio

Equazione di partenza (rimossa l'approssimazione per difetto):
$$\Upgamma(n) = 3\Upgamma(\frac{n}{4})+n$$
Possiamo notare che nell'equazione di partenza compaiono i termini 3 e 4. Essi compaiono anche nell'espressione finale. Inoltre c'è una funzione nota non ricorsiva (n) che appare nell'espressione finale.
Questa osservazione sta alla base di un teorema che viene usato nelle equazioni di ricorrenza. Questo teorema ci permette di risolvere equazioni di ricorrenza senza dover fare quasi nessun calcolo

Nomi del teorema
- Teorema principale (libro)
- Master theorem

## [[TEOREMA PRINCIPALE]]
Siano $a\ge1$ e $b>1$ consideriamo l'equazione di ricorrenza fatta:
$$\Upgamma(n) = a\Upgamma(\frac{n}{b})+f(n)$$
Ci sono 3 casi:
1. $\text{Se }f(n) \in O(n^{log_b{a}-\epsilon}) \quad \text{con}\ \epsilon>0$, allora $\Upgamma(n) \in \theta (n^{log_b{a}})$
2. $\text{Se }f(n)\in \theta(n^{log_b{a}})$ allora $\Upgamma(n) \in\theta(f(n)\log{n})$
3. $\text{Se } f(n) \in \Omega(n^{log_b{a}+\epsilon})\text{ e se }af(\frac{n}{b})\le cf(n) \text{ per qualche }c<1, n>\bar{n}  \quad \text{con}\ \epsilon>0$, allora $\Upgamma(n) \in \theta(f(n))$

Traduzione:
Il risultato è del tipo $1parte +2parte$ (nell'esempio che abbiamo fatto, la prima parte è $n^{\log_4{3}}$, la seconda parte è $4n$)
Quando si risolve una equazione di ricorrenza con il metodo iterattivo, si arriva ad un' espressione finale simile a quella che abbiamo calcolato. 
Il caso 1 e 3 dicono di individuare la parte che ha ordine di grandezza più grande e quello è il risultato. 
Il caso 2 dice che se le due parti hanno lo stesso ordine di grandezza allora la soluzione è una qualunque delle due parti moltiplicata per $\log{n}$
I passaggi che abbiamo fatto noi sono possibili solo quando $f(n)$ e  $n^{\log_b{a}}$ sono sufficientemente distanti ($\epsilon$)
>Per esempio se dovessi confrontare un $n$ e un $n\log{n}$, è vero che $n \in O(n\log{n})$, ma non esiste un $\epsilon>0$ tale che $n\in O(\frac{n\log{n}}{n^\epsilon})$

___
Deve esister un polinomio $n^\epsilon$ con qualche $\epsilon>0$
$$f(n)n^\epsilon \in O(n^{log_b{a}})$$
____
### ESEMPI 
$$\Upgamma(n) = 9\Upgamma(\frac{n}{3})+n$$
$a=9 \quad b=3 \quad f(n)=n$
$n^{log_b{a}} = n^{log_3{9}} = n^2$
$\exists?\epsilon f(n) \in O(n^{\log_b{a}-\epsilon})\rightarrow n \in O(n^{2-\epsilon})?$
>Prendiamo $\epsilon = 0.5,\quad n\in O(n^{1.5})? SI$
>Prendiamo $\epsilon = 1,\quad n\in O(n^{1})? SI$

Siamo nel caso 1, $\Upgamma(n) \in \theta(n^{\log_b{a}})=\theta(n^2)$
___
$$\Upgamma(n)= \Upgamma(\frac{2n}{3})+1$$
$a =1 \quad b=\frac{3}{2} \quad f(n)=1$
>Perchè $b=\frac{3}{2}?$
>>Dobbiamo scrivere $b$ come $\frac{n}{b}$. Sappiamo che $\frac{2}{3}n$, n può essere riscritto come $\frac{n}{\frac{3}{2}}$ 

$n^{\log_b{a}}=n^{\log_\frac{3}{2}1}=n^0=1$
Le due parti hanno lo stesso ordine di grandezza (1=$n^0$)
Siamo nel caso 2
$\Upgamma(n) \in \theta(f(n)\log{n}) = \theta(\log{n})$
___
$$\Upgamma(n)=3\Upgamma(\frac{n}{4})+n\log{n}$$
$a=3 \quad b=4 \quad f(n)=n\log{n}$
$n^{\log_b{a}} =n^{\log_4{3}}$
$n^{\log_4{3}} \in O(n\log{n})$
$n\log{n} \in \Omega(n^{\log_4{3}})$
$\exists?\epsilon: n\log{n} \in \Omega(n^{log_4{3}+\epsilon})$
>Sappiamo che $log_4{3}<1$. Dobbiamo trovare un $\epsilon$ tale che $log_4{3}<log_4{3}+\epsilon<1$
>>Sia $\epsilon = \frac{1-\log_4{3}}{2}$

Siamo nel caso 3, tuttavia dobbiamo ancora fare la verifica.
$af(\frac{n}{b})<cf(n)$ per qualche $c<1$
$3\frac{n}{b}\log{\frac{n}{b}} = 3\frac{n}{4}\log{\frac{n}{4}}<cn\log{n}:c<1$
$\frac{3}{4}n\log{\frac{n}{4}}= \frac{3}{4}n(\log{n}-\log{4})\le \text{questo è c-->}\frac{3}{4}n(\log{n})$
> $c = \frac{3}{4}$

$\Upgamma(n) \in \theta(n\log{n})$

___

$$\Upgamma(n) = 2\Upgamma(\frac{n}{2}) + n \log{n}$$
$a = 2 \quad b=2 \quad f(n)= n\log{n}$
$n^{\log_b{a}}=n^{\log_2{2}}=n$
$n\log{n} \in \Omega(n)$
$\exists? \epsilon\quad n\log{n}\in\Omega(n^{1+\epsilon})$  NO
Qualsiasi sia $\epsilon>0\quad n^{n+\epsilon}\in \Omega(n\log{n})$
>$n^1*n^{\epsilon}\le? \ n\log{n}$
>>Si possono semplificare gli n: $n^{\epsilon}\le?\log{n}$ NO

NON SIAMO IN GRADO DI APPLICARE IL TEOREMA 
___
## [[Equazione di ricorrenza_metodo grafico|METODO GRAFICO]]
$$\Upgamma(n) = \Upgamma(\frac{n}{3})+\Upgamma(\frac{2n}{3})+n$$![[Tree.png]]
I rami stanno per le chiamate ricorsive che l'equazione di ricorrenza fa. Possiamo notare che, indipendentemente dal livello in cui ci si trova, la somma dei nodi che si trovano su uno stesso livello fa sempre $n$
Quanto profondo è l'albero (il ramo più lungo)? Tanto quanto mi serve ad avere costante ogni nodo. In questo caso il ramo più lungo è quello che si sviluppa alla estrema destra $$\frac{2}{3}*\frac{2}{3}*...*\frac{2}{3}$$
Quante volte bisogna moltiplicare $\frac{2}{3}$ per ottenere un valore costante?
>$\log{n}$ volte
>>$n(\frac{2}{3})^i$ MAX numero di nodi al livello i. Quanto deve valere i per arrivare al caso base?
>>>$n(\frac{2}{3})^i \le 1$ (Adesso basta risolvere la disuguaglianza per ottenere $i \ge \log{n}$)


Per $\log{n}$ volte sommo $n$
Risultato finale: $\theta(n\log{n})$

Ogni volta che noi facciamo un lavoro lineare per dividere il problema in 2 parti (a patto che ognuna sia una frazione della precedente), la tecnica funziona
___
## [[ALGORITMI DI ORDINAMENTO]]
INPUT: una sequenza ($a_1,a_2,...,a_n$) di oggetti su cui è definita una relazione di orginamento totale.
- Totale: se prendo una coppia di oggetti, li so confrontare

>Per il momento sappiamo solo che possiamo confrontare due oggetti fra di loro (non sappiamo come sono fatti gli oggetti) . Successivamente sapremo anche come è fatta la relazione di ordinamento (troveremo degli algoritmi più efficienti).

OUTPUT: permutazione (o riordinamento) ($a_1^\prime,a_2^\prime,...,a_n^\prime$) di ($a_1,...,a_n$) tale che ($a_1^\prime \le a_2^\prime\le ... \le a_n^\prime$)


### [[INSERTION SORT]]
Gli indici degli array che useremo da qui in avanti partiranno a 1, non da 0

Abbiamo un array, teniamo a sinistra gli elementi già ordinati, prendiamo un nuovo elemento e lo inseriamo nel posto corretto nella parte già ordinata (la parte ordinata diventa più grande).
Per fare questo salviamo questo elemento in una variabile temporanea (key) e spostiamo a destra tutti gli elementi già ordinati più grandi di key e, alla fine, mettiamo il valore di key nel posto vuoto formatosi. Ripetere questo procedimento per tutti gli elementi dell'array (tranne il primo)

```pseudocodice linenos title:"Insertion Sort" collapse
Insertion_Sort(A)
for(j<-2 to length(A)) //j= indice del primo elemento non ancora ordinato
	key = A[j]
	i = j-1
	while(i>0 AND A[i]>key)
		A[i+1] = A[i] //il buco si trova in posizione A[i]
		i = i-1
	A[i+1] = key
return A
```
##### COMPLESSITA ALGORITMO
Nel caso pessimo il ciclo while ha $O(n)$. Considerando anche il ciclo while, possiamo affermare che l'insertion sort $\in O(n^2)$. Tuttavia è possibile ottenere una stima più accurata: infatti il ciclo while non si ripete per n volte, bensì j volte.
Al più il ciclo while viene eseguito: 1+2+3+...+n= $\frac{n(n+1)}{2}$. E comunque quadratico.

$InsertionSort \in \Omega(n^2)?$
>Prendendo un array inverso (6,5,4,3,2), possiamo notare che il numero minimo di passi da fare è $\frac{n(n+1)}{2}\quad L'InsertionSort \in \Omega(n^2)$


$$InsertionSort \in \theta(n^2)$$

Il problema dell'ordinamento $\in O(n^2)$
Il problema dell'ordinamento $\in \Omega(n^2)$?

Quanta memoria extra usa l'InsertionSort? 
>Memoria per tre variabili(j,i,key). Una quantità costante (indipendente da n)

Quando riusciamo a usare una quantità di memoria costante, allora possiamo dire che l'ordinamento è [[ORDINAMENTO IN LOCO|in loco]].

Cosa succede agli elementi uguali?
> Non vengono scambiati. L'algoritmo è [[ORDINAMENTO STABILE|stabile]] (se al posto di A[i]>key avessimo scritto A[i]$\ge$key, allora l'algoritmo sarebbe instabile)

Cosa succede se applichiamo l'[[INSERTION SORT|insertion sort ]] ad un array già ordinato?
>La complessità diventa lineare

Quando conviene usare l'[[INSERTION SORT|insertion sort ]] ?
>- Quando gli array sono piccoli
>- Quando dobbiamo ordinare un array già a priori ordinato a cui sono stati aggiunti pochi elementi