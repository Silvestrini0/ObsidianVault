### Algoritmo di Euclide

Si applica l'algoritmo delle divisioni successive:

6086 = xn
1765 = xn-1

| 6086 | 1765 | 791 | 183 | 59  | 6   | 5   | 1   | 0   |
| ---- | ---- | --- | --- | --- | --- | --- | --- | --- |
|      | 3    | 2   | 4   | 3   | 9   | 1   | 5   |     |
- **Prima riga**: valori dei dividendi, divisori e resti (a partire da `6086` e `1765`).
- **Seconda riga**: quozienti di ogni divisione.
---
**Passaggi**:
1. 6086=1765×3+7916086=1765×3+791
2. 1765=791×2+1831765=791×2+183
3. 791=183×4+59791=183×4+59
4. 183=59×3+6183=59×3+6
5. 59=6×9+559=6×9+5
6. 6=5×1+16=5×1+1
7. 5=1×5+05=1×5+0

L'ultimo resto non nullo è **1**, quindi
$$
MCD⁡(6086,1765)=1
$$
Due numeri con MCD uguale a 1 si dicono **primi tra loro** (o coprimi).

---

### Identità di Bézout

Poiché MCD⁡(a,b)=1, esistono interi x,y tali che:
$$
6086⋅x+1765⋅y=1
$$
Dalla sostituzione all'indietro dei resti si ottiene:
$$
6086⋅(−299)+1765⋅1031=1
$$
ovvero:
$$
x=−299,y=1031
$$
---

### Generalizzazione

Dati due interi A e B, l'algoritmo di Euclide permette di trovare MCD(A,B) e, tramite la procedura inversa, anche i coefficienti r,a,d,b,c  tali che:
$$
MCD⁡(A,B)=A⋅r+B⋅d 
$$
(identità di Bézout).

---

Dimostriamo che l'algoritmo di Euclide converge verso il massimo comun divisore
Si vuole dimostrare che il MCD(a,b) = MCD(b,R).

| a   | b   | R   |
| --- | --- | --- |
|     | q   |     |
$$
a = qb + R
$$
Supponiamo che esista un divisore comune tra a e b chiamato d.
$$
a-qb = R
$$
$$
(a- qb) mod(d) = R mod(d)
$$
$$
(a+(-qb))mod(d) = Rmod(d)
$$$$
(amod(d)+(-qb)mod(d))mod(d) = Rmod(d)
$$
$$
(0+0)mod(d) = Rmod(d)
$$
Abbiamo appena dimostrato quindi che se a e b hanno come divisore comune d, allora d è divisore anche di R.

Supponiamo che d* sia un divisore comune tra b e R e dimostriamo che d* è divisore anche di a.
$$
a = qb + R
$$
Suppongo che d* sia divisore comune di R e b.
$$
qb + R = a
$$
$$
(qb +R) mod(d*) = a mod(d*)
$$
$$
((qd)mod(d*)+Rmod(d*)) = amod(d*)
$$$$
(0+0)mod(d*) = amod(d*)
$$
$$
amod(d*) = 0
$$
Se b e R hanno come divisore comune d* allora d* p divisore anche di a  ( e anche di b ).

L'insieme di tutti i divisori comuni di a e b sono divisori comuni anche per b e R.
Inoltre l'insieme di tutti i divisori comuni di b e R sono divisori comuni anche per a e b quindi
$$
MCD(a,b) = MCD(b,R)
$$
