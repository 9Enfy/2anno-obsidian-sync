[[ALGORITMI-INDICE]]
# COMPITI PER CASA
$\bar{n}$ è un modo per dare un nome ad un valore qualsiasi di n, NON è la negazione logica.
### $$f \in O(g) \implies g \in \Omega(f)$$
> $\exists c \exists \bar n \forall n>\bar{n}  \space \space f(n) \le cg(n)$
> Siano $c$ ed $\bar n$ i due valori che soddisfano la formula soprastante
> Vogliamo dismostare che vale : $\exists c^I \exists \bar{n}^I \forall n>\bar{n} g(n) \ge c^If(n)$
> >$\frac{1}{c} f(n) \le g(n)$
> >$g(n) \ge \frac{1}{c}f(n)$ || Fisso $c^I = \frac{1}{c}$
> >$g(n) \ge c^If(n) \forall n > \bar{n}$ || Fisso $\bar{n}^I = \bar{n}$

### $$f_1 \in O(g) \land f_2 \in(g) \implies f_1+f_2 \in O(g)$$
>$f_1 \in O(g)$ significa:
>> $\exists c_1 \exists \bar{n}_1 \forall n > \bar{n}_1 \space \space f_1(n) \le c_1g(n)$
>
>$f_2 \in O(g)$ significa:
>> $\exists c_2 \exists \bar{n}_2 \forall n > \bar{n}_2 \space \space f_2(n) \le c_2g(n)$
>
>$\exists c_1 \exists c_2 \exists \bar{n}_1 \exists \bar{n}_2 \space (\forall n>\bar{n}_1 f_1(n) \le c_1g(n)) \land (\forall n>\bar{n}_2 f_2(n) \le c_2g(n))$
>
>Prendiamo un valore per ognuna di $c_1$ $c_2$ $\bar{n}_1$ $\bar{n}_2$
>$\exists c \exists \bar{n} \forall n>\bar{n} \space f_1(n)+f_2(n) \le cg(n)$
>>$\bar{n} = \max(\bar{n}_1,\bar{n}_2)$
>
>>$f_1(n) \le c_1g(n)$
>>$f_2(n) \le c_2g(n)$
>>$f_1(n) + f_2(n) \le (c_1+c_2)g(n)$ || $c_1+c_2 = c$
>
>Avendo trovato una $\bar{n}$ e una $c$ abbiamo dimostrato la formula :
>>$\exists c \exists \bar{n} \forall n>\bar{n} \space f_1(n)+f_2(n) \le cg(n)$
>

____

### Teoremi da dimostrare

- $f_1 \in O(g_1) \land f_2 \in O(g_2) \implies f_1 * f_2 \in O(g_1*g_2)$
- $f \in O(g) \leftrightarrow \lim_{n \rightarrow \infty} \frac{f}{g}< \infty$
- $f \in \theta (g) \leftrightarrow \lim_{n \rightarrow \infty} \frac{f}{g} <\infty \space AND >0$

___
## FRASI TIPICHE che si dicono su algoritmi e problemi

Sia $A$ un algoritmo
- $A \in O(f) \implies$ La complessità di $A$ è una funzione $g \in O(f)$. Per esempio l'algoritmo di ricerca array appartiene a $O(n)$ e a $O(n^2)$, ma non a $O(1)
- $A \in \Omega(f) \implies$ Esiste uno [[schema di input]] tale che la complessità di A sullo schema è una funzione $g \in \Omega(f)$. Per esempio l'algoritmo di ricerca array appartiene a $\Omega(n)$, ma non appartiene a $\Omega(n^2)$. In altre parole, misura quanto è accurata la complessità A.
- $A \in \theta(f) \implies A \in \Omega(f) \land O(f)$ 

___
### $\Omega(f) \subseteq  O(f)$ FALSO

> Sia $f = n^2$ || $n \in$ $O(f)$ $ \space n \notin \Omega(f)$
___
##
Sia P un problema 
>$P \in O(f)$ 
>>$\exists A \in O(f)$ che risolve P
>>> C'è un algoritmo che risolve P in f
>
>$P \in \Omega(f)$
>>$\forall A$ che risolve P, $A \in \Omega(f)$
>>>Prendendo un qualsiasi algoritmo che risolve P, nel caso pessimo l'algoritmo NON può fare meno di f
>
>$P \in \theta(f)$
>> $P \in \Omega(f) \land P \in O(f)$
>>> Esiste un algoritmo che risolve il problema P in f ma non esiste un algoritmo migliore

___
## RICERCA BINARIA
//inserire pseudocodice
La ricerca binaria ha complessità $\log{n,}$, tuttavia da quel che è stato scritto precedentemente, la ricerca in un array ha complessità n. Perchè questa differenza?
> Nell'algoritmo ricerca semplice abbiamo immaginato un qualsiasi array, NON un array ordinato.La ricerca binaria fa la ricerca su un **array ordinato**. 

___
## FATTORIALE DI UN NUMERO
```pseudocodice linenos title:"Fattoriale" collapse
IF n == 0
	return 1
ELSE
	return n*FATT(n-1)
```
>Dimensione del problema: n
>$\Upgamma(n)$ = stima del tempo di esecuzione del programma
$$
\begin{equation}
\Upgamma(n)=
\begin{cases}
1,\theta(c) & SE & n = 0\\
1+\Upgamma(n-1) & SE & n >0\\
\end{cases}
\end{equation}
$$
___
### [[Equazione di ricorrenza]]

Si trovano nei problemi più piccoli. L'equazione descritta sopra è una equazione di ricorrenza. Posso vedere la complessità del mio problema come il costo che devo fare per ricondurmi ai problemi più piccoli + il costo per risolvere i problemi più piccoli.
___
#### Esempio [[equazione di ricorrenza]] (METODO ITERATIVO)
>$\Upgamma(n) = 1 + \Upgamma(n-1)$
>$= 1 + 1 + \Upgamma(n-2)$
>$= 1+1+1+\Upgamma(n-3)$
>:
>:
>= $1+1+1+....+1+T(n-i)$
>Smetto quando $n-i = 0 \space \space \space n=i$
>= $1+1+...+1+\Upgamma(n-n)$
>=n+1
>>Risulta che la complessità algoritmica del fattoriale è n+1, ma è facilmente dimostrabile che il fattoriale non ha complessità n+1. Perchè?
>>>Stiamo ipotizzando di lavorare con registri e che il costo di una moltiplicazione sia sempre lo stesso (indifferente dal numero di bit dei numeri da moltiplicare).
>>>Nella realtà più grande è il numero da moltiplicare, più la complessità della operazione aumenta.
>>
>>Quando parliamo di algoritmi dobbiamo stare attenti alle ipotesi che si fanno. Per esempio possiamo ipotizzare che il tempo che serve per effettuare una moltiplicazione sia costante se i numeri da moltiplicare sono piccoli.
___
## RISOLUZIONE DI EQUAZIONI DI RICORRENZA
$$
\begin{equation}
\Upgamma(n) =
\begin{cases}
c &n<b\\
F(\Upgamma,n)& n \ge b & \text{F è una funzione}
\end{cases}
\end{equation}
$$
- Non tutte le equazioni di ricorrenza hanno soluzione univoca
- Se il funzionale $F$ usa $\Upgamma$ su valori più piccoli di n allora riusciamo a trovare funzioni univoche
- Di come è fatto il caso base, non ci interessa sapere quanto vale $b$ e quanto vale $c$. Sapremo solo che esiste un caso base tale per cui quando $n$ è sufficientemente piccolo il risultato è una costante e quando $n$ è grande il risultato è dato dal funzionale $F$

Noi rappresenteremo le equazioni di ricorrenza in questo modo:
$\Upgamma(n) = F(\Upgamma,n)$
>$\Upgamma(n) = \Upgamma(\frac{n}{2}) + f(n)$
>$\Upgamma(n) = \Upgamma(n-1) + \Upgamma(\frac{n}{4})+2n$
>> Notare che in $\Upgamma$ c'è sempre, come argomento, un valore più piccolo di $n$. In questo modo l'approccio interattivo funziona.











