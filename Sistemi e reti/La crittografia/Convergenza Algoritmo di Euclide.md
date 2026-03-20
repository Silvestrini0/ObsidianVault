# Convergenza dell'algoritmo di Euclide

Si vuole dimostrare che il massimo comun divisore di due numeri interi non cambia sostituendo la coppia $(a, b)$ con $(b, R)$, dove $R$ è il resto della divisione euclidea:
$$
a = q \cdot b + R, \qquad 0 \le R < b.
$$
In altre parole:
$$
\mathrm{MCD}(a, b) = \mathrm{MCD}(b, R).
$$

## Dimostrazione

### 1. Ogni divisore comune di $a$ e $b$ divide anche $R$

Sia $d$ un divisore comune di $a$ e $b$, cioè:
$$
a \equiv 0 \pmod{d}, \qquad b \equiv 0 \pmod{d}.
$$
Dalla relazione $a = qb + R$ ricaviamo $R = a - qb$.  
Consideriamo $R$ modulo $d$:
$$
R \equiv a - qb \pmod{d}.
$$
Poiché $a \equiv 0 \pmod{d}$ e $b \equiv 0 \pmod{d}$, si ha:
$$
R \equiv 0 - q \cdot 0 \equiv 0 \pmod{d}.
$$
Quindi $d$ divide $R$.

### 2. Ogni divisore comune di $b$ e $R$ divide anche $a$

Sia $d^*$ un divisore comune di $b$ e $R$, cioè:
$$
b \equiv 0 \pmod{d^*}, \qquad R \equiv 0 \pmod{d^*}.
$$
Dalla stessa uguaglianza $a = qb + R$, valutiamo $a$ modulo $d^*$:
$$
a \equiv qb + R \pmod{d^*}.
$$
Sostituendo le congruenze nulle:
$$
a \equiv q \cdot 0 + 0 \equiv 0 \pmod{d^*}.
$$
Pertanto $d^*$ divide $a$.

### 3. Conclusione

Abbiamo dimostrato che:
- L'insieme dei divisori comuni di $a$ e $b$ è uguale all'insieme dei divisori comuni di $b$ e $R$.
- Di conseguenza, il **massimo** divisore comune delle due coppie coincide:
$$
\mathrm{MCD}(a, b) = \mathrm{MCD}(b, R).
$$

Questo fatto garantisce che, iterando l'algoritmo di Euclide (sostituendo ogni volta la coppia con il divisore e il resto), si arriva infine a una coppia in cui il resto è zero, e l'ultimo resto non nullo è proprio il massimo comun divisore iniziale.