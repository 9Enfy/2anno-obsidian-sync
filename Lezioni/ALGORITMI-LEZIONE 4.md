## RISULUZIONE DI [[Equazione di ricorrenza|EQUAZIONI DI RICORRENZA]]
___

### [[Equazione di ricorrenza_metodo di sostituzione | METODO DI SOSTITUZIONE]]
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
$$\Upgamma(n) = \Upgamma(\lfloor \frac{n}{2}\rfloor)+\Upgamma(\lceil \frac{n}{2}\rceil)+1 \qquad \Upgamma(n) \in \theta(n)$$
A cosa si riferisce l'equazione? Per esempio un algoritmo che prende un array, lo divide a metà, e invoca sè stessa nella prima metà e nella seconda metà. Infine fa qualche lavoro costante per mettere assieme i risultati. 
Ho diminuito la dimensione dei sottoproblemi, ma la dimensione del problema rimane la stessa.
> $\Upgamma(n) \le cn$
> $\Upgamma(n) \le c\lfloor \frac{n}{2} \rfloor + c\lceil \frac{n}{2} \rceil +1$
> $c(\lfloor)