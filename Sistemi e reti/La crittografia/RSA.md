**Funzioni di due variabili e Linearità**

Il valore di **y** dipende dalla coppia **(x₁, x₂)**. Per ogni coppia appartenente a **ℝ²** esiste un unico valore di **y**.

Definizione f: ℝ² → ℝ
$$
y = f(x₁, x₂)  
∀ x₁, x₂ ∈ ℝ, ∃! y
$$

**Esempio di funzione:**  
$$
y = (eˣ¹ + sin(x₁ · x₂)) / 3x₁
$$

---

Funzioni lineari

Una funzione **y = f(x₁, x₂)** è lineare se è del tipo:  
$$
y = Ax₁ + Bx₂  
$$
con **A, B ∈ ℝ** (coefficienti indipendenti da x₁, x₂).

---

Proprietà 1: Combinazione lineare

La combinazione lineare di due funzioni lineari è ancora una funzione lineare.

**Definizione:**  
Siano **y₁** e **y₂** due funzioni lineari. Si definisce combinazione lineare di coefficienti **λ₁** e **λ₂** la funzione:  
**y = λ₁y₁ + λ₂y₂**

**Dimostrazione:**  
Siano y₁ = Ax₁ + Bx₂ e y₂ = Cx₁ + Dx₂.  
$$y = λ₁(Ax₁ + Bx₂) + λ₂(Cx₁ + Dx₂) $$
$$y = λ₁Ax₁ + λ₁Bx₂ + λ₂Cx₁ + λ₂Dx₂ $$
$$y = (λ₁A + λ₂C)x₁ + (λ₁B + λ₂D)x₂  $$
$$y = Ex₁ + Fx₂$$  
_(Dove E e F sono i nuovi coefficienti costanti)._

---

Proprietà 2: Composizione di funzioni lineari

Se **z** è funzione lineare di **x₁** e **y**, e **y** è funzione lineare di **x₁** e **x₂**, allora la funzione composta **z = h(x₁, x₂)** è lineare.

**Definizione:**  
Se z = f(x₁, y) e y = g(x₁, x₂), la composizione è:  
$$z = f(x₁, g(x₁, x₂)) = h(x₁, x₂)$$

**Dimostrazione:**

1. Sia z lineare in (x₁, y): **z = Ax₁ + By**
2. Sia y lineare in (x₁, x₂): **y = Cx₁ + Dx₂**

Sostituendo la seconda nella prima:  
$$z = Ax₁ + B(Cx₁ + Dx₂)  $$
$$z = Ax₁ + BCx₁ + BDx₂  $$
$$z = (A + BC)x₁ + (BD)x₂  $$
$$z = Ex₁ + Fx₂$$

**Conclusione:**  
La struttura rimane quella di una combinazione lineare di x₁ e x₂, dunque la funzione composta è lineare.

---
