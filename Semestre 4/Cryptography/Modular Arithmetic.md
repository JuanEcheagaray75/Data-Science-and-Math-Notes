# Modular Arithmetic

---

## Introduction

### Divisibility

> Let $a, b, c \in \mathbf{Z}$, then $a\mid b \iff \exists \ c: ac = b$

In human words: let both $a$ and $b$ be integers, (with $a \neq 0$), we say that $a$ divides $b$ if there is an _integer_ $c$ such that be can be expressed as the multiplication of $a$ and $c$

#### Following proofs

> 1. if $a \mid b$ and $a \mid c$, then $a \mid (b+c)$

$$\begin{gather*}
	ak = b \\
 	aj = c \\
 	b + c = m
 	ak + aj = n \\
 	an = m \equiv a \mid m = a \mid (b + c)
\end{gather*}$$

> 2. if $a \mid b$ and $b \mid c$ then $a \mid c$

$$\begin{gather*}
 	a \mid b \equiv ak = b \\
 	b \mid c \equiv bj = c \\
 	c = (ak) j \\
 	c = a (kj) \equiv a \mid c
\end{gather*}$$

We can conclude that $a$ divides $c$ since $kj$ is still a positive whole number.

> 3. if $a \mid b$ and $b \mid a$, then $a = \pm \ b$

$$\begin{gather*}
 	am = b \\
 	bn = a \\
 	bnm = b \\
 	nm = 1 \\
 	n = m = 1 \\
 	n = m = -1 \\
 	a = \pm \ b
\end{gather*}$$

> 4. if $a \mid 1$, then $a = \pm \ 1$

$$\begin{gather*}
 	an = 1 \\
 	a = n = 1 \\
 	a = n = -1 \\
 	a = \pm \ 1
\end{gather*}$$

> 5. if $b \mid g$ and $b \mid h$, then $b \mid (mg + nh)$ for arbitrary integers $m$ and $n$

$$\begin{gather*}
 	b \mid g \equiv bj = g \\
 	b \mid h \equiv bl = h \\
 	mg + nh = bjg + bln \\
 	mg + nh = b (jg + ln) \Rightarrow b \mid (mg + nh)
\end{gather*}$$

Since $(jg + ln)$ is still an integer, we can conclude that $b$ divides $(mg + nh)$

### The division algorithm

> Theorem. For all $a, b \in \mathbf{Z}$, with $b > 0$, there exists unique $q, r \in \mathbf{Z}$ such that:
	> $a = bq + r$
	> $0 \leq r \leq b$

**Example**:

$$\begin{gather*}
	a = 21, b = 2 \\
	21 = 2 \cdot 10 + 1
\end{gather*}$$

## Fermat's little theorem

## Binary modular exponentiation

## Extended Euclidean algorithm
