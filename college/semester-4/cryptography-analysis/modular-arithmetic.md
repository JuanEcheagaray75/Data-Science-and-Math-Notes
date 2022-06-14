# Modular Arithmetic

- [Modular Arithmetic](#modular-arithmetic)
  - [Introduction](#introduction)
    - [Properties](#properties)
    - [Galois Fields (GF)](#galois-fields-gf)
    - [Multiplicative inverse](#multiplicative-inverse)
      - [Euler's totient function](#eulers-totient-function)
      - [Fermat's little theorem](#fermats-little-theorem)
    - [Divisibility](#divisibility)
    - [Fermat's small theorem](#fermats-small-theorem)
      - [Following proofs](#following-proofs)
    - [The division algorithm](#the-division-algorithm)
  - [Binary modular exponentiation](#binary-modular-exponentiation)
  - [Extended Euclidean algorithm](#extended-euclidean-algorithm)

## Introduction

A lot of the operations performed in cryptography deal with _modulus_ operations, that broadly speaking, deal with the remainder of a division. For example, consider $a = 25$ and $p = 23$, we can then define $b$ as:

$$ 2 \equiv 25 \bmod 23 $$

Or in a more general fashion:

$$ b \equiv a \bmod p $$

### Properties

As it occurs with operations in $\mathbf{R}$, we can define a set of rules of operations centered around the usage of remainders through the whole numbers $\mathbf{Z}$. Here are some of the properties of modular arithmetic:

- **Reflexivity**: $a \equiv a \bmod p \quad \forall a \in \mathbf{Z}$
- **Transitivity**: $a \equiv b \bmod p, b \equiv c \bmod p \Rightarrow a \equiv c \bmod p \quad \forall a, b, c \in \mathbf{Z}$
- **Symmetry**: $a \equiv b \bmod p \Rightarrow b \equiv a \bmod p \quad \forall a, b \in \mathbf{Z}$
- **Associativity**: $[a + (b + c)] \bmod p \equiv [(a + b) + c] \bmod p$
- **Commutativity**: $(a + b) \bmod p \equiv (b + a) \bmod p, ab \bmod p \equiv ba \bmod p$
- **Distributivity**: $a (b + c) \bmod p \equiv (ab + ac) \bmod p$
- **Identity**: $(a + 0) \bmod p \equiv a \bmod p, a (1) \bmod p \equiv a \bmod p$
- **Inverses**: $a + (-a) \bmod p \equiv 0 \bmod p, a (a^{-1}) \bmod p \equiv 1 \bmod p$

In modular arithmetic one of the most useful operations when dealing with remainders is the reducibility operation. Consider $a, b \in \mathbf{Z}$, then:

$$\begin{gather*}
    (a + b) \bmod p \equiv (a \bmod p + b \bmod p) \bmod p \\
    (ab) \bmod p \equiv [(a \bmod p) (b \bmod p)] \bmod p
\end{gather*}$$

### Galois Fields (GF)

> A field that contains a finite number of elements. As with any field, a finite field is a set on which the operations of multiplication, addition, subtraction and division are defined and satisfy certain basic rules

In modular arithmetic, $a, b, c, d \in \mathbf{Z}$, but also $b, d \in GF(p) = \{0, 1, \ldots, p-2, p-1\}$. With this in mind we then have:

$$\begin{gather*}
    b \equiv a \bmod p; b < p \\
    d \equiv c \bmod p; d < p
\end{gather*}$$

To put it simply, the remainders $b, d$ must be less than the modulus $p$.

### Multiplicative inverse

#### Euler's totient function

Euler's totient function counts the positive integers up to a given number $n$ that are _relatively prime_ to $n$. In other words, it is the number of integers $k$ in the range $1 \leq k \leq n$ such that $k$ for which the greatest common divisor $gcd(n,k) = 1$. The integers $k$ are sometimes referred to as totatives of n.

For example, the totatives of 9 are the six numbers 1, 2, 4, 5, 7 and 8, making $\phi(9) = 6$.

Here are some interesting properties:

- If $n$ is a prime number, then $\phi(n) = n - 1$
- With a product $x = pq$, where $p, q$ are prime numbers, $\phi(pq) = (p-1)(q-1)$
- With a number of the form $x = p^{k}$, being $p$ a prime number, $\phi(p^{k}) = p^{k-1}(p-1)$

#### Fermat's little theorem

> if $p$ is a prime number, then for each number $a \in \mathbf{N}$ we have $a^{p} \equiv a \bmod p$

Fermat's little theorem is a special case of **Euler's theorem** which states that:

> $a^{\phi(n)} \equiv 1 \bmod n$

For $n$ being a prime number we have $\phi(n) = n - 1$, which then gives $a^{n-1} \equiv 1 \bmod n$. We can just multiply both sides by $a$ to obtain the first expression.

We can then calculate the inverse of $a$ as:

> $a^{-1} \bmod p \equiv a^{p-2} \bmod p$

### Divisibility

> Let $a, b, c \in \mathbf{Z}$, then $a\mid b \iff \exists \ c: ac = b$

In human words: let both $a$ and $b$ be integers, (with $a \neq 0$), we say that $a$ divides $b$ if there is an _integer_ $c$ such that be can be expressed as the multiplication of $a$ and $c$.

### Fermat's small theorem

Fermat little's theorem tells us that if $p$ is a prime number, then for each number $a \in \mathbf{N}$ we have $a^{p} \equiv a \bmod p$. Using $\phi(p) = p-1$:

$$1 \bmod p \equiv a^{p-1} \bmod p$$

We can then calculate the inverse of $a$ as:

$$a^{-1} \bmod p \equiv a{p-2} \bmod p$$

#### Following proofs

> if $a \mid b$ and $a \mid c$, then $a \mid (b+c)$

$$\begin{gather*}
    ak = b \\
    aj = c \\
    b + c = m
    ak + aj = n \\
    an = m \equiv a \mid m = a \mid (b + c)
\end{gather*}$$

> if $a \mid b$ and $b \mid c$ then $a \mid c$

$$\begin{gather*}
    a \mid b \equiv ak = b \\
    b \mid c \equiv bj = c \\
    c = (ak) j \\
    c = a (kj) \equiv a \mid c
\end{gather*}$$

We can conclude that $a$ divides $c$ since $kj$ is still a positive whole number.

> if $a \mid b$ and $b \mid a$, then $a = \pm \ b$

$$\begin{gather*}
    am = b \\
    bn = a \\
    bnm = b \\
    nm = 1 \\
    n = m = 1 \\
    n = m = -1 \\
    a = \pm \ b
\end{gather*}$$

> if $a \mid 1$, then $a = \pm \ 1$

$$\begin{gather*}
    an = 1 \\
    a = n = 1 \\
    a = n = -1 \\
    a = \pm \ 1
\end{gather*}$$

> if $b \mid g$ and $b \mid h$, then $b \mid (mg + nh)$ for arbitrary integers $m$ and $n$

$$\begin{gather*}
    b \mid g \equiv bj = g \\
    b \mid h \equiv bl = h \\
    mg + nh = bjg + bln \\
    mg + nh = b (jg + ln) \Rightarrow b \mid (mg + nh)
\end{gather*}$$

Since $(jg + ln)$ is still an integer, we can conclude that $b$ divides $(mg + nh)$

### The division algorithm

> Theorem. For all $a, b \in \mathbf{Z}$, with $b > 0$, there exists unique $q, r \in \mathbf{Z}$ such that:
$$\begin{gather*}
    a = bq + r \\
    0 \leq r \leq b
\end{gather*}$$

**Example**:

$$\begin{gather*}
    a = 21, b = 2 \\
    21 = 2 \cdot 10 + 1
\end{gather*}$$

## Binary modular exponentiation



## Extended Euclidean algorithm


