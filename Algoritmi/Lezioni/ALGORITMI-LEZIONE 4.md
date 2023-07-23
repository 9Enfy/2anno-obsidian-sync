## RISULUZIONE DI [[Equazione di ricorrenza|EQUAZIONI DI RICORRENZA]]
___
# AGGIUNGERE DEFINIZIONE INDUZIONE

## [[Equazione di ricorrenza_metodo di sostituzione | METODO DI SOSTITUZIONE]]
$$\Upgamma(n) = 2 \Upgamma(\lfloor \frac{n}{2} \rfloor) +n $$
>$\lfloor x \rfloor$ sta per x approssimato per difetto

Qualcuno ci dice che $\Upgamma(n) \in O(n\log{n})$
>$\exists c \quad T(n) \le c\ n\log{n}$
>$\Upgamma(n) = 2 \Upgamma(\lfloor \frac{n}{2} \rfloor) +n$
>>>$\le 2c \lfloor \frac{n}{2} \rfloor \log{\lfloor \frac{n}{2}\rfloor}+n$
>>>$\le \cancel{2}c\frac{n}{\cancel{2}} \log\frac{n}{2}+n$
>>>$= cn\log{n}-cn\log{2}+n$
>>>$= cn\log{n}-(cn \log{2}-n)$
>>>$?\le cn\log{n}? \quad \text{Vero se: }cn\log{2}\ge0$
>>>>$n(c\log{2}-1)\ge0$
>>>>$c\log{2}-1 \ge 0$
>>>>$c \ge \frac{1}{\log{2}}$

___
### Esempio
$$\Upgamma(n) = \Upgamma(\lfloor \frac{n}{2}\rfloor)+\Upgamma(\lceil \frac{n}{2}\rceil)+1 \qquad \Upgamma(n) \in O(n)$$
A cosa si riferisce l'equazione? Per esempio un algoritmo che prende un array, lo divide a metà, e invoca sè stessa nella prima metà e nella seconda metà. Infine fa qualche lavoro costante per mettere assieme i risultati. 
Ho diminuito la dimensione dei sottoproblemi, ma la dimensione del problema rimane la stessa.
> $\Upgamma(n) \le cn$
> $\Upgamma(n) \le c\lfloor \frac{n}{2} \rfloor + c\lceil \frac{n}{2} \rceil +1$
> >$=c(\lfloor\frac{n}{2}\rfloor+\lceil\frac{n}{2}\rceil)+1$
>> $=cn+1$
> >$cn+1 \le cn$? MAI VERA!!!
> 

Il metodo di sostituzione non ci permette di trovare una c. O non esiste c o bisogna provare con un altro metodo.

Perchè non ha funzionato il metodo di sostituzione? Perchè c'è il +1 finale che rompe. Possiamo però "uccdere" il +1 usando, al posto di $cn$, $cn-b$

> $\Upgamma(n) \le cn-b$
> $\Upgamma(n) \le c\lfloor \frac{n}{2} \rfloor-b + c\lceil \frac{n}{2} \rceil-b +1$
> >$=c(\lfloor\frac{n}{2}\rfloor+\lceil\frac{n}{2}\rceil)+1-b-b$
>> $=(cn-b)+(1-b) \quad \text{Per fa sparire il +1, basta segliere un } b \ge 1$
> >$cn-b \le cn$? SI, dimostrazione completata

Da dove è saltato fuori $-b$?
> Quando applichiamo il metodo induttivo e c'è qualche termine di ordine inferiore che non permette di raggiungere una risposta, possiamo provare a togliere un termine di ordine inferiore dall'ipotesi 

$$\Upgamma(n) \in \theta(n)$$
>Abbiamo già provato per O(n), adesso proviamo per $\Omega(n)$

$$\Upgamma(n) \in \Omega(n)$$
>$\Upgamma(n) \ge cn$
>$\Upgamma(n) = \Upgamma(\lfloor \frac{n}{2}\rfloor)+\Upgamma(\lceil \frac{n}{2}\rceil)+1$
>>$\ge c\lfloor\frac{n}{2}\rfloor+c\lceil\frac{n}{2}\rceil+1$
>>$cn+1 \ge cn$

Abbiamo dimostrato che vale per $\Omega(n)$. Questo ci permette di concludere che:
- $\Upgamma(n) \in \theta(n)$

Come fare in un esercizio? Si va a tentativi, si parte da una approssimazione alta e da una bassa, le dimostro con il metodo di sostituzione e cerco di avvicinarle

Nel caso in cui la tecnica della sostituzione non funziona, bisogna usare altre tecniche.

Se, per esempio, al posto di $O(n)$ c'era $O(\log{n}$), non importa quale metodo si utilizzi, non ci verrà mai fuori un risultato. La dimostrazione è il fatto che abbiamo già dimostrato che $\Upgamma(n) \in \Omega(n)$ 

___
## [[Equazione di ricorrenza_metodo iterativo| METODO ITERATIVO]]
$$\Upgamma(n) = n+ 3 \Upgamma(\lfloor \frac{n}{4}\rfloor)$$
Prendo l'argomento di $\Upgamma$ della parte di destra ($\lfloor \frac{n}{4}\rfloor$) e lo metto come argomento della parte di sinistra
$$\begin{align}
= n+3 & \left(\lfloor \frac{n}{4}\rfloor+3\Upgamma (\lfloor \frac{\lfloor \frac{n}{4}\rfloor}{4}\rfloor )\right)
\end{align}
$$

$$
\begin{align}
=n+3\lfloor \frac{n}{4}\rfloor+3^2\Upgamma(\lfloor \frac{n}{4^2}\rfloor)
\end{align}
$$
$$
= n+3\lfloor \frac{n}{4}\rfloor + 3^2(\lfloor \frac{n}{4^2}\rfloor+3\Upgamma(\frac{\lfloor \frac{n}{4^2}\rfloor}{4}))
$$
$$
= n+3\lfloor \frac{n}{4}\rfloor+3^2\lfloor \frac{n}{4^2}\rfloor+3^3\Upgamma(\lfloor \frac{n}{4^3}\rfloor)
$$
$$
= n+3\lfloor \frac{n}{4}\rfloor+3^2\lfloor \frac{n}{4^2}\rfloor+...+3^{i-1}\lfloor \frac{n}{4^{i-1}}\rfloor+ 3^i\Upgamma(\lfloor \frac{n}{4^i}\rfloor)
$$
Quando $3^i\Upgamma(\lfloor \frac{n}{4^i}\rfloor)$ è il caso base?
> Quando $\lfloor \frac{n}{4^i}\rfloor \le x$ con x un numero che fisso (ipotizziamo da adesso in poi che x = 1)
> >$\lfloor \frac{n}{4^i}\rfloor \le 1$
> >$\frac{n}{4^i}\le x$
> >$4^i \ge n$
> >$i \ge \log_4{n
> 
> $\le n + 3\lfloor \frac{n}{4} \rfloor+...+3^{\lceil\log_4{n}\rceil}\lfloor \frac{n}{4^{\lceil\log_4{n}\rceil}}\rfloor+ 3^{\lceil \log_4{n}\rceil+1}\Upgamma(\frac{n}{\lceil4^{\log{4}{n}}\rceil})$
> >Per semplificare, possiamo considerare $\Upgamma(\frac{n}{\lceil4^{\log{4}{n}}\rceil})$ come una costante  c (1)
> 
> Lavorando con il $\le$, possiamo rimuovere le approsimazioni per difetto
>>$\le n+3\frac{n}{4}+...+3^{\lceil\log_4{n}\rceil} \frac{n}{4^{\lceil\log_4{n}\rceil}}+3^{\lceil \log_4{n} \rceil+1}$
>>$= 3^{\lceil \log_4{n} \rceil+1}+ n(\sum_{i=0}^{\lceil\log_4{n}\rceil}(\frac{3}{4})^i)$
>>>Abbiamo 2 termini: $3^{\lceil \log_4{n} \rceil+1}$ e $n(\sum_{i=0}^{\lceil\log_4{n}\rceil}(\frac{3}{4})^i)$. L'ordine di grandezza del risultato equivale all'ordine di grandezza del più grande dei 2
>>>$$n(\sum_{i=0}^{\lceil\log_4{n}\rceil}(\frac{3}{4})^i) \le n \sum_{i=0}^\infty(\frac{3}{4})^i = n \frac{1}{1-\frac{3}{4}}=4n$$
>>>___
>>>$$3^{\lceil \log_4{n} \rceil+1} = 3^{log_4{n}+2} = 3^2*3^{log_4{n}}$$ 
>>>$$3^{log_4{n}} = n^{log_n{3^{log_4{n}}}} =n^{\log_4{n}\log_n{3}} = n^{log_4{3}}$$
>>>Perchè è venuto fuori $log_4{3}$ come esponente?
>>>>Formula del cambio base di un logaritmo : $log_a{b} = log_a{c}*log_c{b}*$
>>
>>$\le n^{\log_4{3}}+4n = O(n)$ 



 




