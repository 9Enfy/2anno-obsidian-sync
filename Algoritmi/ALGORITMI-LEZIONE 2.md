---
share: true  
--- 
[[ALGORITMI-INDICE]]

Complessità : misura del tempo che ci mette un algoritmo a finire
___
Dobbiamo confrontare algoritmi in base al tempo che ci impiegano per terminare un compito.

A noi ci interessa sapere se un algoritmo è più veloce di un altro, NON il tempo esatto di esecuzione.
___
Un conteggio indipendente dal tipo di processore è quello di contare le istruzioni  (ipotizziamo che un istruzione viene eseguita con lo stesso tempo).
___
La complessità di un problema dipende da quanto è grande il problema
___
E necessario definire la dimensione di un problema. In ogni singolo contesto siamo noi a decidere quanto è grande il problema.
___
Dimensione del problema è un numero.
La complessità è una **funzione N -> R^>=0**

| Simbolo | Significato               |
| ------- | ------------------------- |
| N       | Numero Naturale           |
| R       | Numero Reale Non Negativo |

Per noi R rappresenta sempre il tempo

___
## ALGORITMO SEARCH ARRAY
Dato un array, cercare se c'è un determinato numero

```c linenos title:"Search array C style" collapse
//CODICE SIMILE AL C
Search (A,x)
for(i = 0; i<= length(A);i++)
{
	if( A[i] == x)
		return true;
}
return false;
```
```pseudocodice linenos title:"Search array pseudocodice" collapse
//CODICE COME VERRA SCRITTO NEL CORSO
Search (A,x)
per ogni indice i di A
IF A[i] == x
	return true
return false
```
Non è importante come viene scritto, basta solo che sia comprensibile (per esempio al posto di == si potrebbe tranquillamente scrivere = , è pseudocodice)
___
### ANALISI ALGORITMO SCRITTO SOPRA
- **Dimensione problema** (m): numero di elementi nell'array A
- Quante volte viene eseguita l'istruzione "return false"?
- - Caso migliore: 0 volte (trovato x)
- - Caso pegigore: 1 volta (sono stati analizzati tutti gli elementi di A)

Il tempo di esecuzione di questo algoritmo varia a seconda dell'input.
___
Siamo più interessati al caso pessimo (tempo massimo di esecuzione) {possiamo anche analizzare il caso migliore e il caso medio}.

Dobbiamo analizzare il comportamento dell'algoritmo nel caso peggiore.
___
### ALGORITMO SEARCH Array
- Nel caso migliore il numero di istruzioni eseguite è costante c (x si trova nel primo indice dell'array). Non dipende da m.
- Nel caso peggiore il numero di istruzioni eseguite è <= cm+d
- c = totale di istruzione (indicizzazione dell'array, i++, controllo dell'if...) (costante), poco importante perchè:
- - è difficile contare quante istruzioni effettivamente ci sono
- - influisce poco sul tempo finale dell'algoritmo
- m = totale di elementi dell'array
- d = una costante
___
## ALGORITMO PRODOTTO TRA DUE MATRICI 
Serve per far capire che è complicato determinare esattamente il valore delle costanti 
```pseudocodice linenos title:"Prodotto tra due matrici" collapse
MULT (A,B)
	for i <- 1 to ROWS(A)
		for j <- 1 to COLS(B)
			C[i][j] <- 0
			for( n <- 1 to COLS(A))
				C[i][j] <- c[i][j] + A[i][n]*B[n][j]
return C
```
Perchè indicizziamo gli array da 1? Per convenzione faremo così per questo corso, tranne quando indicizziamo da 0.
Guardare la videolezione (1:00:00) per spiegazione di numero totale di istruzioni per il prodotto tra 2 matrici.
Risultato = 5lmn + 4ln + 3n +4, dove lmn sono le dimensioni delle matrici
___
## NOTAZIONE ASINTOTICA
A me interessa studiare le funzioni di complessità in termini di quanto crescono al crescere dell'input (sono inutili le costante e i termini di ordine inferiore)
$f \in O(g)$
f non cresce più velocemente di g (ignorando le costanti)
$\exists n \exists  c \forall$






