# Funzioni di due variabili e Linearità

Il valore di **y** dipende dalla coppia **(x₁, x₂)**. Per ogni coppia appartenente a **ℝ²** esiste un unico valore di **y**.

Definizione \(f: \mathbb{R}^2 \to \mathbb{R}\)  
$$
y = f(x_1, x_2), \qquad \forall x_1, x_2 \in \mathbb{R}, \; \exists! \, y
$$

**Esempio di funzione:**  
$$
y = \frac{e^{x_1} + \sin(x_1 \cdot x_2)}{3x_1}
$$

---

# Funzioni lineari

Una funzione \(y = f(x_1, x_2)\) è **lineare** se è del tipo:  
$$
y = A x_1 + B x_2
$$  
con \(A, B \in \mathbb{R}\) (coefficienti indipendenti da \(x_1, x_2\)).

---

## Proprietà 1: Combinazione lineare

La combinazione lineare di due funzioni lineari è ancora una funzione lineare.

**Definizione:**  
Siano \(y_1\) e \(y_2\) due funzioni lineari. Si definisce combinazione lineare di coefficienti \(\lambda_1\) e \(\lambda_2\) la funzione:  
\(y = \lambda_1 y_1 + \lambda_2 y_2\).

**Dimostrazione:**  
Siano \(y_1 = A x_1 + B x_2\) e \(y_2 = C x_1 + D x_2\).  
$$
\begin{aligned}
y &= \lambda_1 (A x_1 + B x_2) + \lambda_2 (C x_1 + D x_2) \\
  &= \lambda_1 A x_1 + \lambda_1 B x_2 + \lambda_2 C x_1 + \lambda_2 D x_2 \\
  &= (\lambda_1 A + \lambda_2 C) x_1 + (\lambda_1 B + \lambda_2 D) x_2 \\
  &= E x_1 + F x_2
\end{aligned}
$$  
(dove \(E\) e \(F\) sono i nuovi coefficienti costanti).

---

## Proprietà 2: Composizione di funzioni lineari

Se \(z\) è funzione lineare di \(x_1\) e \(y\), e \(y\) è funzione lineare di \(x_1\) e \(x_2\), allora la funzione composta \(z = h(x_1, x_2)\) è lineare.

**Definizione:**  
Se \(z = f(x_1, y)\) e \(y = g(x_1, x_2)\), la composizione è:  
\(z = f(x_1, g(x_1, x_2)) = h(x_1, x_2)\).

**Dimostrazione:**

1. Sia \(z\) lineare in \((x_1, y)\): \(z = A x_1 + B y\)
2. Sia \(y\) lineare in \((x_1, x_2)\): \(y = C x_1 + D x_2\)

Sostituendo la seconda nella prima:  
$$
\begin{aligned}
z &= A x_1 + B (C x_1 + D x_2) \\
  &= A x_1 + B C x_1 + B D x_2 \\
  &= (A + B C) x_1 + (B D) x_2 \\
  &= E x_1 + F x_2
\end{aligned}
$$

**Conclusione:**  
La struttura rimane quella di una combinazione lineare di \(x_1\) e \(x_2\); dunque la funzione composta è lineare.

---

# Algoritmo di Euclide e identità di Bézout

Abbiamo dimostrato che, grazie all'[[Algoritmo di Euclide]], con \(r, a, b, d \in \mathbb{Z}\),
$$
\mathrm{MCD}(a,b) = r a + d b.
$$
Due numeri si dicono **primi tra loro** (coprimi) se \(\mathrm{MCD}(a,b) = 1\).

Supponiamo che \(a\) e \(b\) siano primi tra loro:
$$
\mathrm{MCD}(a,b) = 1 \quad \Longrightarrow \quad r a + d b = 1.
$$
Da cui:
$$
d b - 1 = r a \quad \Longrightarrow \quad d b \bmod a = 1.
$$
Questa relazione è vera se \(a\) e \(b\) sono primi tra loro.

Ci aspettiamo di trovare due chiavi (una pubblica e una privata):
- La **chiave pubblica** è costituita da due numeri: \((e, n)\);
- La **chiave privata** è costituita da due numeri: \((d, n)\).

Dunque \(n\) è un elemento comune.

Le chiavi pubblica e privata sono generate:
- dal **destinatario** per conseguire la **segretezza**;
- dal **mittente** per conseguire l'**affidabilità** del documento.

---

# Procedura per la generazione delle chiavi (RSA)

Si generano due numeri primi \(p\) e \(q\) di circa 512 bit ciascuno.  
Si definisce \(n = p \cdot q\), che risulta un numero di 1024 bit.

Si cerca quindi un esponente pubblico \(e\) tale che:
$$e < (p-1)(q-1)$$
$$(mathrm{MCD}\big((p-1)(q-1),\, e\big) = 1) (cioè (e) è coprimo con ((p-1)(q-1))).$$

Una volta trovato un \(e\) che soddisfa queste condizioni, la **chiave pubblica** è costituita dalla coppia \((n, e)\).

Poiché \(e\) è coprimo con \((p-1)(q-1)\), per l'identità di Bézout esistono interi \(r\) e \(d\) tali che:
$$
r \cdot (p-1)(q-1) + d \cdot e = 1, \qquad r, d \in \mathbb{Z}.
$$
Da questa relazione segue immediatamente che:
$$
d \cdot e \equiv 1 \pmod{(p-1)(q-1)}.
$$

Per ricavare esplicitamente l'esponente privato \(d\) (che deve essere positivo), si può riscrivere l'equazione come:
$$
d e = 1 - r (p-1)(q-1) = 1 + k (p-1)(q-1),
$$
con \(k\) intero opportuno (in pratica si sceglie \(k\) in modo che \(d\) sia intero positivo). Infine:
$$
d = \frac{1 + k (p-1)(q-1)}{e}, \qquad d, k \in \mathbb{N}.
$$
Si determina \(d\) per tentativi incrementando il valore di \(k\) e arrestando la procedura non appena si ottiene un valore intero per \(d\). A questo punto si forma la **chiave privata** \((d, n)\).

---

# Algoritmo di cifratura/decifratura

Trasformo la sequenza di bit da cifrare in blocchi tali che, interpretando il blocco come un numero intero, esso risulti **minore di \(n\)**. Sia \(m\) tale numero.

Per cifrare (m):
$$
c = m^e \bmod n 
$$
Per decifrare \(m\):
$$
m = c^d \bmod n
$$

