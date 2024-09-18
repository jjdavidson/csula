# Math 5021: Functional Analysis

**Professor**: Dan da Silva
**Office:** Simpson Tower 217
**Office Hours:** Tu/Th 11-11:50
**Email**: ddasilva4@calstatela.edu

**Textbook**: Linear Functional Analysis by Bryan P. Rynne and Martin A. Youngson.

**Grade:**
- Homework: 50%
- Midterm Exam: 25%
- Final Exam: 25%

**Prerequisites:**
- Linear Algebra
- Real Analysis
- $L^P$ spaces


# Chapter 1: Preliminaries

## 1.1 Linear Algebra

### Notation

We use uppercase letters $X,Y,Z$ to denote sets, and use lowercase letters $x,y,z$ to denote elements of sets.

Here is standard notation for special sets:
- $\N$ denotes natural numbers
- $\Z$ denotes integers
- $\Q$ denotes rational numbers
- $\R$ denotes real numbers
- $\C$ denotes complex numbers

Set operations:
- $\subset$ subset
- $\in$ element of
- $\not \in$ does not belong to
- $A\times B$ Cartesian product
- $A \cup B$ union
- $A \cap B$ intersection
- $X - Y = \{x \in X: x \notin Y\}$

**Definition.**
A *field* is an algebraic object consisting of a set with addition and multiplication defined on it. 

**Definition.**
Let $X,Y$ be sets. Then a *mapping* takes objects in $X$ and assigns objects in $Y$. We denote this by $f:X \to Y$.

If $f:X \to Y$, $A \subset X$, $B \subset Y$ then 
- $f(A) := \{f(x): x \in A\} $ 
- $f^{-1}(B) := \{x \in X: f(x) \in B\} $

We say
- $f$ is *injective* if $f(x)=f(y)$ implies $x=y$.
- $f$ is *surjective* if $\forall y \in Y$, $\exist x \in X$ such that $f(x) = y$
- $f$ is *bijective* if it is injective and surjective.

### Definition of a Vector Space

**Definition.**
A vector space over a field $\F$ is a non-empty set $V$ with two functions, $+: V \times V \to V$ and $\cdot: \F \times V \to V$ such that
1. $x+y = y+x$, for all $x,y \in V$
2. $(x+y)+z = x+(y+z)$, for all $x,y,z \in V$
3. $\exists 0 \in V$ such that $x+0 = x$, for all $x \in X$
4. For each $x \in V$, $\exists -x \in V$ such that $x+-x=0$
5. $\exists 1 \in V$ such that $1\cdot x = x$, for all $x \in X$
6. $(\alpha \beta) x = \alpha(\beta x)$,  for all $\alpha,\beta \in \F$, for all $x \in V$
7. $(\alpha+\beta)x = \alpha x + \beta x$, for all $\alpha,\beta \in \F$, for all $x \in V$
8. $\alpha(x+y) = \alpha x + \alpha y$, for all $\alpha,\beta \in \F$, for all $x \in V$

If $V$ is a vector space, $A,B \subset V$, and $x \in X$ then we define 
$$ 
\begin{aligned}
    x+A &:= \{x+a:a \in A\} \\
    A+B &:= \{a+b: a \in A, b \in B\} 
\end{aligned}
$$

### Subspaces

**Definition.**
Let $V$ be a vector space and let $U \subset V$. We say $U$ is a *linear subspace* if it is a vector space satisfying 1-8 in the definition of a vector space using the same binary operations as in $V$

**Proposition.**
Let $V$ be a vector space and let $U \subset V$. Then $U$ is a linear subspace if 
- $0 \in U$
- $U$ is closed under vector addition
- $U$ is closed under scalar multiplication

**Definition.**
Let $V$ be a vector space, let $v_1,\dots, v_k$ be a finite set, and let $A$ be an arbitrary subset of $V$.
- A *linear combination* of the vectors $v_1,\dots,v_k$ is a sum of the form $$\alpha_1 v_1 + \dots + \alpha_k v_k$$ for some $\alpha_1,\dots,\alpha_k \in \F$.
- A finite set $\{v_1,\dots,v_k\}$ is *linearly independent* if $$\alpha_1v_1 + \dots + \alpha_kv_k = 0$$ implies $\alpha_i=0$, $i = 1,\dots,k$
- The arbitrary set $A$ is *linearly independent* if every finite subset of $A$ is linearly independent.
- The *span* of $A$ is the set of all linear combinations of all finite subsets.
- If $\{v_1,\dots,v_k\}$ is linearly independent and $\linspan\{v_1,\dots,v_k\} = V$, we say the set is a *basis* for $V$. In this case, we say $V$ has *dimension* $k$.
- If $V$ is not spanned by any finite set, we say it is *infinite dimensional*.

### Cartesian Product of Vector Spaces

Let $V,W$ be vector spaces over $\F$. The *cartesian product* $V \times W$ is a vector space with operations defined by:
- $(v_1,w_1)+(v_2,w_2) = (v_1+w_1,v_2+w_2)$
- $\alpha (v,w) = (\alpha v, \alpha w) $

**Definition.**
Let $S$ be a set, let $V$ be a vector space over $\F$. We denote the set of functions $f: S \to V$ by $F(S,V)$.

**Definition.**
We define vector addition and scalar multiplication on $F(S,V)$ by 
- $(f+g)(x) = f(x)+g(x)$
- $(\alpha f)(x) = \alpha f(x)$

### Linear Transformations

**Definition.**
Let $V,W$ be vector spaces over $\F$. A function $T:V \to W$ is called a *linear transformation* if 
$$T(\alpha x+ \beta y) = \alpha T(x) + \beta T(y)$$ 
for all $\alpha,\beta \in \F$ and all $x,y \in V$.

**Notation.**
The set of all linear maps $T: V \to W$ is denoted $L(V,W)$. If $V=W$, we write $L(V)$.

**Definition.** 
Let $V,W,X$ be vector spaces over $\F$. Let $T \in L(V,W)$, and $S \in L(W,X)$. We define the composition $S \circ T$ by 
$$(S \circ T)(v) = S(T(v))$$ 
for all $v \in X$.

**Lemma.**
Let $V$ be a vector space over $\F$. Let $R,S,T \in L(V)$, $\alpha \in \F$, and let $I$ denote the identity transformations. Then,
1. $R \circ (S \circ T) = (R \circ S) \circ T$
2. $R \circ (S+T) = R\circ S + R \circ T$
3. $(R+S) \circ T = R \circ T + S \circ T$
4. $ I \circ T = T \circ I = T$
5. $(\alpha S) \circ T = \alpha (S \circ T) = S \circ (\alpha T)$

**Lemma.** 
Let $V,W$ be vector space over $\F$, let $T \in L(V,W)$. Then, 
1. $T(0) = 0$
2. If $U$ is a linear subspace of $V$, then $ T(U)$ is a linear subspace of $W$. Moreover, $$\dim T(U) \leq \dim U$$
3. If $X$ is a linear subspace of $W$, then $T^{-1}(X)$ is a linear subspace of $V$. 

### Rank and Nullity

**Definition.** Let $V,W$ be vector spaces over the same field $\F$ and let $T \in L(V,W)$. 
1. The *image* of $T$ is the subspace $T(V)$.
2. The *rank* of $T$ is $$r(T) = \dim T(V)$$
3. The *kernel* of $T$ is the subspace $$\ker T = T^{-1}(0)$$
4. The *nullity* of $T$ is $$n(T) =\dim\ker T$$

**Lemma.** Let $V,W$ be vector spaces over the same field $\mathbb{F}$ and let $T \in L(V,W)$.
1. $T$ is injective iff $T(x) = 0$ has only the solution $x=0$
2. $T$ is surjective iff $T(V) = W$. If $\dim W$ is finite, this is equivalent to $r(T) = \dim W$
3. $T$ is bijective iff there exists $S \in L(W,V)$ such that $$S \circ T =I \quad \text{and} \quad T \circ S = I$$

**Theorem.** (Rank-Nullity Theorem)
Let $V,W$ be vector spaces over the same field $\F$ and let $T \in L(V,W)$. If $V$ is finite dimensional, then 
$$\dim V = r(T) + n(T)$$

### Eigenvalues and Eigenvectors

**Definition.** Let $V$ be a vector space and $T \in L(V)$. We say $\lambda$ is an *eigenvalue* if there exists a nonzero $v \in V$ such that $$T(v) = \lambda v$$ In this case, $v$ is called an *eigenvector*. The subspace $$\operatorname{Ker}(T-\lambda I) \subset V$$ is called the eigenspace corresponding to $\lambda$. The *multiplicity* of $\lambda$ is $$m_\lambda = n(T-\lambda I)$$

**Lemma.** Let $V$ be a vector space, let $T \in L(V)$, and let $\left\{\lambda_1,\dots,\lambda_k\right\}$ be a set of distinct eigenvalues of $T$. For $i = 1,\dots,k$ let $x_i$ be the eigenvector corresponding to $\lambda_i$. Then, $\{x_1,\dots,x_k\}$ is linear independent.

## 1.2 Metric Spaces
### Definition of a Metric Space

**Definition.** 
A *metric* on a set $M$ is a function $d:M \times M \to \operatorname{R}$ with the following properties:
For all $x,y \in M$
1. $d(x,y) \geq 0$
2. $d(x,y) = 0$ iff $x=y$
3. $d(x,y) = d(y,x)$
4. $d(x,y) \leq d(x,z) + d(z,y)$ for all $z \in M$

**Definition.** 
A set $M$ with a metric $d$ defined on it is called a *metric space*. We denote the metric space with $(M,d)$.

**Example.** 
$(\mathbb{R},|\cdot|)$ is a metric space.

**Example.**
If $\F = \R$ or $\F = \C$, then for $x,y \in \F^n$ 
$$d(x,y) = \left( \sum_{i=1}^{n} |x_i-x_j|^2 \right)^{1/2}$$
is a metric on $\F^n$. 

**Example.**
If $\F = \R$ or $\F = \C$, then for $x,y \in \F^n$
$$d(x,y) = \sum_{i=1}^{n} |x_i-x_j|$$
is a metric on $\F^n$.

**Definition.**
Let $(m,d)$ be a metric space. let $N \subset M$. Then, the function $d_N: N \times N \to \R$ defined by 
$$d_N(x,y) = d(x,y)\Big|_n$$ 
is called the metric induced by $d$ on $N$. 

### Sequences in Metric Spaces

**Definition.**
A *sequence* in a metric space $(M,d)$ is a function $f:\mathbb{N} \to M$. A sequence will be denoted $x_n$.

**Definition.**
Let $x_n$ be a sequence in a metric space $M$. We say $x_n$ *converges* to $x \in M$ if for each $\epsilon>0$, there exists a $N \in \mathbb{N}$ such that $$d(x_n,x) <\epsilon$$ whenever $n \geq N$. If $x_n$ converges to $x$ we say that $\lim x_n = x$.

**Definition.**
Let $(M,d)$ be a metric space. Let $x_n$ be a sequence in the metric space. We say the sequence is *Cauchy* if for each $\epsilon>0$, there exists a natural number $N$ such that $$d(x_n-x_m) < \epsilon$$ whenever $n,m \geq N$.

**Note.**
In $\mathbb{R}$, Cauchy sequences converge and convergent sequences are Cauchy. This was due to the completeness of $\mathbb{R}$. In $\mathbb{R}$, complete means that every bounded set has a least upper bound. We also showed in real analysis that completeness in $\mathbb{R}$ is equivalent to all Cauchy sequences being convergent.

**Definition.**
In a metric space $(M,d)$. We say that the metric space $(M,d)$ is *complete* if every Cauchy sequence in $M$ converges to an element of $M$.

**Theorem.**
Suppose $(M,d)$ is a metric space and $x_n$ is a convergent sequence in $M$. Then,
1. The limit of the sequence is unique.
2. The limit of any subsequence converges to the limit of the sequence
3. The sequence $x_n$ is Cauchy.

*proof.* (1.)
Suppose that $\lim x_n = x$ and $\lim x_n = y$. Fix $\epsilon > 0$. Since $x_n \to x$, there exists a natural number $N_1$ such that $$d(x,x_n) < \epsilon/2$$ whenever $n \geq N_1$. Similarly, since $x_n \to y$, there exists a natural number $N_2$ such that $$d(y,x_n) < \epsilon/2$$ whenever $n \geq N_2$. If $n \geq \max{N_1,N_2}$, then the triangle inequality implies
$$d(x,y) \leq d(x,x_n)+ d(x_n,y) < \epsilon$$
Since this holds for any $\epsilon>0$, it follows that $d(x,y) = 0$. This means that $x = y$, i.e. limits are unique.

### Topology in Metric Spaces

**Definition.**
Let $(M,d)$ be a metric space. For any $x \in M$ and any $r>0$, we define
$$B_x(r) = \{y \in M: d(d,y) < r\}$$
This is called the *open ball* centered at $x$ of radius $r$. Similarly, we define $$\overline{B_x(r)} = \{y \in M: d(d,y) \leq r\}$$
This is called the *closed ball* centered at $x$ of radius $r$.

**Definition.**
Let $(M,d)$ be a metric space and $A \subset M$.
1. We say $A$ is *bounded* if there exists a number $b>0$ such that $d(x,y)<b$ for all $x,y \in A$.
2. We say $A$ is *open* if for each $x \in A$ if there exists an $\epsilon > 0$ such that $B_X(\epsilon) \subset A$.
3. We say $A$ is *closed* if $M-A$ is open.
4. We say $x \in M$ is a *closure point* of $A$ if for each $\epsilon>0$ there exists a $y \in A$ such that $d(x,y) < \epsilon$. 
5. The *closure* of $A$ is the set of all closure points of $A$. The closure of $A$ will be denoted $\overline{A}$.
6. We say $A$ is *dense* in $M$ if $\overline{A} = M$.

**Proposition.**
Let $(M,d)$ be a metric space, and let $A \subset M$. Then, $x$ is a closure point of $A$ iff there exists a sequence $x_n$ in $A$ such that $\lim x_n = x$.

*proof.* $(\implies)$
Assume $x$ is a closure point of $A$. For each natural number $n$ there exists $x_n$ in $A$ such that $$d(x_n,x) < \frac{1}{n}$$ This will define a sequence $x_n$. Let $\epsilon > 0$. By the Archimedean property of the natural numbers, there exists a natural number $N$ such that $\frac{1}{N} < \epsilon$. Hence, $$d(x,x_{N}) < \frac{1}{N} < \epsilon$$ Therefore, if $n$ is a natural number such that $n \geq N$, then $$d(x,x_n) < \frac{1}{n} \leq \frac{1}{N} < \epsilon$$
Thus, $x_n \to x$.

*proof.* $(\impliedby)$
Assume that there exists a sequence $x_n$ in $A$ such that $x_n \to x$. Let $\epsilon>0$. SInce $x_n \to x$ there exists a natural number $N$ such that $$d(x,x_n) < \epsilon$$ whenever $n \geq N$. Choose $y = x_N$. Then $y \in A$ and $d(x,y) < \epsilon$. Since $\epsilon$ was arbitrary we can do this for each $\epsilon > 0$. Therefore, $x$ is a closure point of $A$.

**Proposition.**
Let $(M,d)$ be a metric space and $A \subset M$. Then, $\overline{A}$ is closed.

*proof.*
Choose $x \in M - \overline{A}$. Then $x$ is not a closure point. This means that there exists an $\epsilon > 0$ such that $d(x,y) \geq \epsilon$ for all $y \in A$. Hence, if $z \in M$ and $d(x,z)<\epsilon$, then $z \notin \overline{A}$ and $z \in M - \overline{A}$. Since $z$ was arbirary, it follows that $$B_x(\epsilon) \subset M-\overline{A}$$
This means that $M-\overline{A}$ is open, so $\overline{A}$ is closed.

**Proposition.**
Let $(M,d)$ be a metric space, and let $A \subset M$. Then, $A$ is closed if and only if any convergent sequence in $A$ has limit in $A$.

*proof.* $(\implies)$
Assume $A$ is closed and that $x_n$ is a convergent sequence in $A$ with $x_n \to A$. Since $A$ is closed, $M-A$ is open. For the sake of contradiction, suppose $x \notin A$, i.e. $x \in M-A$. Since $M-A$ is open, there exists an $\epsilon>0$ such that $$B_x(\epsilon) \subset M-A$$ However, the sequence $x_n \to x$ so there most be some natural number $N$ such that $d(x,x_n) < \epsilon$ whenever $n \geq N$. This implies that $B_x(\epsilon) \cap A \neq \varnothing$. This contradicts the fact that $B_x(\epsilon) \subset M-A$. Thus, the assumption that $x \notin A$ is false, so $x \in A$.

*proof.* $(\impliedby)$
Assume that if $x_n \to x$, then $x \in A$. We must show that $A$ is closed. For the sake of contradiction, assume $A$ is not closed. Then, $M-A$ is not open. Then, there exists an element $x \in M - A$ such that $B_x(1/n) \cap A \neq \varnothing$ for all natural numbers $n$.

Then, for each natural number $n$, there exists $x_n \in B_x(1/n)$ such that $x_n \in A$. By construction, $x_n$ is a sequence in $A$ that converges to $x$. By assumption, $x \in A$. But this is a contradiction since $x \in M-A$. Thus, our original assumption that $A$ is not closed is false, and it must be the case that $A$ is closed.

**Proposition.**
Let $(M,d)$ be a metric space and let $A \subset M$. Then, $\overline{A}$ is the intersection of all closed subsets of $M$ that contain $A$.

*proof.*
$$K := \bigcap_{\substack{A \subset C \\ C\text{ closed}}}C$$

Let $x \in K$. Then, $x \in C$ for all closed subsets of $M$ that contain $A$. Since $\overline{A}$ is a closed set that contains $A$, Then, $x \in \overline{A}$. This means that $K \subset \overline{A}$.

Now let $x \in \overline{A}$. Then, there exists a sequence $x_n$ in $A$ such that $x_n \to x$. Now let $C$ be any closed subset of $M$ that contains $A$. Then, $x_n$ is a sequence in $C$. Since $C$ is closed, any convergent sequence in $C$ converges in $C$ by the previous proposition. Thus, $x \in C$. SInce $C$ was an arbitrary closed subset containing $A$, it follows that $x \in K$. Thus, $\overline{A} \subset K$.

Together these imply $K = \overline{A}$ which completes the proof.

**Proposition.**
Let $(M,d)$ be a metric space and $A\subset M$. Then, $A$ is closed if and only if $A = \overline{A}$.

*proof.* $(\implies)$
Assume $A$ is closed. By the definition of closure, $A \subset \overline{A}$. By the previous proposition, $\overline{A}$ is the intersection of all closed subsets of $M$ that contain $A$. Since $A$ is closed, contains $A$, and the intersection is a subset of any set in the intersection, it follows that $\overline{A} \subset A$. Therefore, $A = \overline{A}$.

*proof.* $(\impliedby)$
Suppose $A= \overline{A}$. Since $\overline{A}$ is always closed, it follows that $A$ is closed.

**Proposition.**
Let $(M,d)$ be a metric space and $A\subset M$. We say $A$ is dense in $M$ if and only if for each $x \in M$ and each $\epsilon>0$, there exists $y \in A$ such that $d(x,y)<\epsilon$.

*proof.* (Homework.)

**Example.**
Let $M = \mathbb{R}$ with $d(x,y) = |x-y|$. Let $A = (0,1)$. Show that $\overline{A} = [0,1]$.

It suffices to show that $[0,1] \subset \overline{A}$ and $\overline{A} \subset [0,1]$. Since the closure $\overline{A}$ is the intersection of all closed subsets of $\mathbb{R}$ that contain $(0,1)$, it follows that $(0,1)$ is contained in any closed set that contains $(0,1)$. In particular, $(0,1) \subset [0,1]$ and $[0,1]$ is closed, so $\overline{A} \subset [0,1]$.

Now assume $x \in [0,1]$. If $0 <x < 1$, then $x \in A \subset \overline{A}$. Now we will choose sequences in $(0,1)$ that converge to $0$ and $1$. For example, $\frac{1}{n} \to 0$ and $1-\frac{1}{n} \to 1$. Since the closure of $A$ contains its limit points, it follows that $0,1 \in \overline{A}$. Thus, $[0,1] \subset \overline{A}$. 

Hence, $\overline{(0,1)} = [0,1]$.

**Definition.**
A subset $A$ of a metric space $(M,d)$ is complete in $(M,d)$ if every Cauchy sequence in $A$ converges to an element of $A$.

### Continuity in Metric Spaces

**Definition.**
Let $(M,d_M)$ and $(N,d_N)$ be metric spaces and $f:M \to N$. We say $f$ is **continuous** at $c \in M$ if for each $\epsilon > 0$, there exists a $\delta >0$ such that $$d_N(f(x),f(c)) < \epsilon \ \text{whenever} \ d_M(x,c) < \delta$$

**Definition.**
Let $(M,d_M)$ and $(N,d_N)$ be metric spaces and $f:M \to N$. We say $f$ is **uniformly continuous** on $M$ if for all $\epsilon > 0$, there exists $\delta > 0$ such that $$d_N(f(x),f(y)) < \epsilon \text{ whenever } d_M(x,y) < \delta$$

**Note.**
The difference between continuous and uniformly continuous is subtle. Uniform continuity does not depend on the location of the points $x$ and $y$, only their relative distance.

**Proposition.**
Suppose $(M,d_M)$ and $(N,d_N)$ are metric spaces and $f: M \to N$. $f$ is continuous at $x \in M$ if and only if for every sequence $x_n \to x$ in $M$, then $f(x_n) \to f(x)$ in $N$.

**Proposition.**
Suppose $(M,d_M)$ and $(N,d_N)$ are metric spaces and $f: M \to N$. $f$ is continuous at $x \in M$ if and only if 
- the pre-image of an open set is open
- the pre-image of a closed set is closed

**Corrollary.**
Suppose $(M,d_M)$ and $(N,d_N)$ are metric spaces and $f: M \to N$. $f$ is continuous. Assume $f(x) = g(x)$ for all $x \in A$, where $A$ is dense in $M$. Then, $f=g$.

### Completeness of Subsets

**Definition.**
A metric space $(M,d)$ is **complete** if every Cauchy sequence converges to an element of $M$.

**Definition.**
A subset $A \subset M$ of a metric space $(M,d)$ is **complete** if every Cauchy sequence in $A$ converges to an element of $A$.

**Definition.**
Let $(M,d)$ be a metric space. We say a subset $A \subset M$ is **compact** if every sequence $x_n$ in $A$ has a convergent subsequence that converges to an element of $A$. We say $A$ is **relatively compact** if $\overline{A}$ is compact. If $M$ is compact, we say it is a **compact metric space**.

**Theorem.**
Suppose $(M,d)$ is a metric space and $A \subset M$.
- If $A$ is complete, then $A$ is closed.
- If $M$ is complete, then $A$ is complete if and only if $A$ is closed.
- If $A$ is compact, then it is closed and bounded.

**Theorem.**
Let $(M,d)$ be a compact metric space. Let $f: M \to \mathbb{F})$ be continuous. Then, there exists a constant $b$ such that $|f(x)| \leq b$ for all $x \in M$. Furthermore, there exist $x_0,y_0 \in M$ such that $$\inf{f} = f(x_0), \qquad \sup{f} = f(y_0)$$

**Definition.**
Let $(M,d_M)$ be a compact metric space. We define $C(M)$ to be the set of $\mathbb{F}$-valued continuous functions on the metric space $M$. We define a metric on $C(M)$ by $$d(f,g) := \sup|f-g|$$ 

**Definition.**
Suppose $(M,d)$ is a compact metric space. Let $f_n$ be a sequence in $C(M)$. Let $f$ be an $\mathbb{F}$-valued function on $M$.
- We say $f_n$ **converges pointwise** to $f$ if $$|f_n(x)-f(x)| \to 0$$ for all $x \in M$.
- We say $f_n$ **converges uniformly** to $f$ if $$\sup|f_n - f| \to 0$$

**Theorem.**
The metric space $C(M)$ is complete.

**Theorem.** (Stone-Weierstrass Theorem)
For any compact $M \subset \mathbb{R}$, the set $P(\mathbb{R})$ is dense in $C_{\mathbb{R}}(M)$.

**Definition.**
We say that $X$ is **countable** if it is finite, or their exists a bijection $f: X \mathbb{N}$. If neither is true, we $X$ is **uncountable**.

**Definition.**
A metric space is **separable** if it contains a countable dense subset. To avoid technicalities, we say that the empty set is separable.

**Theorem.**
Suppose $(M,d)$ is a metric space, $A \subset M$
- If $A$ is compact, then $A$ is separable.
- If $A$ is separable, $B \subset A$, then $B$ is also separable.

## 1.2 Lebesgue Integration

### Riemann Integral
1. Define a partition $\mathcal{P}$ of $[a,b]$: $$a = x_0 < x_1 < x_2 < \dots < x_{n-1} < x_n = b$$ These define subintervals $[x_i,x_{i+1}]$ with $[a,b] = \bigcup_{k=1}^n [x_{k-1},x_k]$.
2. In each subinterval $[x_{k-1},x_k]$ choose a point $x_k^*$.
3. Define the Riemann Sum $$S(f,\mathcal{P},\sigma) = \sum_{k=1}^n f(x_k^*)(x_k-x_{k-1})$$
4. We say $f$ is **Riemann Integrable** if there exists a number $I$ such that for each $\epsilon > 0$, there exists a $\delta > 0$ such that $$|D(f,\mathcal{P},\sigma) - I| < \epsilon$$ whenever $\max|x_k-x_{k-1}| < \delta$.

When this definition fails, we turn to a new method based on measure theory. In Lebesgue integration, we separate theinterval $[a,b]$ into arbitrary subsets $A_i$ such that $$[a,b] = \bigsqcup_{i=1}^{n} A_i$$ However, these sets may not be intervals, so may not know how to compute the size of these sets. If we cannot measure these sets, we cannot define the Riemann integral.

The solution is to replace the length of $A_i$ with some "measure" of $A_i$.

### $\sigma$-algebras
Let $X$ be a set. A $\sigma$-algebra on $X$ is a colloetion of subsets $\mathcal{M} \subset \mathcal{P}(x)$ of $X$ such that
1. $\varnothing, X \in \mathcal{M}$
2. $\mathcal{M}$ is closed under complements.
3. $\mathcal{M}$ is closed under countable unions.

We call the sets in $\mathcal{M}$ **measureable sets**.

### Measures
Given a set $X$ and a $\sigma$-algebra $\mathcal{M}$ on $X$, a measure on $\mathcal{M}$ is a function $\mu:\mathcal{M} \to \mathbb{R}$ such that
1. $\mu(\varnothing) = 0$.
2. $\mu(S) \geq 0$.
3. If $S_i$ is a sequence of sets in $\mathcal{M}$ that are pairwise disjoint, then $$\mu\left(\bigcup_{i=1}^{\infty} S_i\right) = \sum_{i=1}^n \mu(S_i)$$

### Integrals of Simple Functions

**Definition.**
A function $f(x)$ is **simple** if it takes a finite number of values.

**Example.**
$f(x) = \chi_{\mathbb{Q}}(x)$ is a simple function that is not a step function.

**Definition.**
The integral of a simple non-negative function defined on a **measure space** $(X,\mathcal{M},\mu)$ is then defined as $$\int fd\mu = \sum_{i=1}^n a_i \mu(A_i)$$
where the $a_i$ are the different values of $f$ and $A_i$ are the sets on which $f = a_i$.

**Example.**
Let $X = \mathbb{R}$, $\mathcal{M}$ Lebesgue Measureable sets, and  $\mu$ the Lebesgue measure. Compute $$\int_{[0,1]} \chi_{\mathbb{Q}}d\mu$$
Step 1: Patition $[0,1]$ into sets $A_i$ on which $\chi_{\mathbb{Q}}$ takes the same $y$-value.
- $\chi{\mathbb{Q}} = 1$ on $A_1 = \mathbb{Q} \cap [0,1]$
- $\chi{\mathbb{Q}} = 0$ on $A_0 = [0,1] \setminus \mathbb{Q}$.

We will need the following facts: $\mu(A_1) = 0$ and $\mu(A_0) = 1$. Then, $$\int_{[0,1]} \chi_{\mathbb{Q}}d\mu = \sum_{i=1}^n a_i\mu(A_i) = 1 \cdot \mu(A_1) + 0 \cdot \mu(A_0) = 0$$


**Example.**
Let $X = \mathbb{N}$, $\mathcal{M} = 2^{\mathbb{N}}$, and define $\mu(A) = |A|$. Let $f: \mathbb{N} \to \mathbb{R}$ be defined by
$$
f(x) = \begin{cases}
1 & 0 \leq x \leq 5 \\
0 & \text{otherwise}
\end{cases}
$$

Observe that $f(x) = 1$ for $x = 1,2,3,4,5$, and $f(x) = 0$ for all other natural numbers. Thus, $A_1 = \{1,2,3,4,5\}$ and $A_0 = \mathbb{N} \setminus A_1$. Therefore, $$\int_{\mathbb{N}} fd\mu = 1\cdot \mu(A_1) + 0\cdot \mu(A_0) = 1\cdot 5 + 0 \cdot \infty = 5$$

### Integrals of Non-negative Measureable Functions

**Definition.**
Let $(X,\mathcal{M},\mu)$ be a measure space. We say $f: X \to \mathbb{R}$ is **measureable** if $$\{x \in X:f(x) > \alpha\}$$ is measureable for all $\alpha \in \mathbb{R}$

If $f$ is measureable and non-negative, we define $$\int fd\mu = \sup\left\{\int \varphi d\mu : 0 \leq \varphi \leq f,\ \text{$\varphi$ is simple}\right\}$$

### Integrals of Measureable Functions

**Lemma.**
If $f$ is a measureable functions, then so are
- $|f|$
- $f^{+} = \max(f,0)$
- $f^{-} = \max(-f,0)$

**Definition.**
Since $f^{+}$ and $f^{-}$ are non-negative, then $\int f^{+}d\mu$ and $\int f^{-}d\mu$ both exist. We define $$\int f d\mu = \int f^{+}d\mu - \int f^{-} d\mu$$

**Note.**
If $f$ is complex valued, then just do the real and imaginary parts separately

### The Space $L^p(X)$

**Definition.**
A function $f: X \to \mathbb{F}$ is called integrable if $\int |f| d\mu < \infty$. Define $$\mathcal{L}^1(X) := \{f:X \to \mathbb{F}: \text{$f$ is integrable}\}$$

**Definition.**
Suppose that $P(x)$ is a statement about the element $x \in X$. We say that the statement $P(x)$ **almost everwhere** (a.e.) if does not hold on a set of measure $0$.

**Lemma.**
Suppose $f,g \in \mathcal{L}^1(X)$ and $f=g\ a.e.$ Then, $\int fd\mu = \int g d\mu$

**Example.**
Let $f = \chi_{\mathbb{Q}}$ and $g = 0$. Since $\{x:f(x) \neq g(x)\} = \mathbb{Q}$ and $\mu(\mathbb{Q}) = 0$, it follows that $f = g \ a.e$.

**Lemma.**
If $\alpha \in \mathbb{F}$ an $f,g \in \mathcal{L}^1(X)$, then
- $\int \alpha f d\mu = \alpha \int fd\mu$
- $\int (f+g) d\mu = \int f d\mu + \int g d\mu$

**Lemma.**
If $f,g \in \mathcal{L}^1(X)$ and $f(x) \leq g(x)$, then $$\int f d\mu \leq \int g d\mu$$

**Definition.**
Let $f,g \in \mathcal{L}^1(X)$. We write $f \equiv g$ if $f=g\ a.e.$. 

**Definition.**
Define the *Lebesgue Space* 
$$L^1(X) = \mathcal{L}(X)/\equiv$$

**Definition.**
Similarly we can define: 
$$\mathcal{L}^p(X):= \{f:X \to \mathbb{F}:f\text{ is integrable}\}$$

**Definition.**
Define the *Lebesgue Space* 
$$L^p(X) = \mathcal{L}^p(X)/\equiv$$

### The Space $L^{\infty}$

**Definition.**
Let $f$ be a measurable function. We define the essential supremum of $f$ by
$$\operatorname{ess}\sup = \inf\{b:f(x) \leq b\ a.e.\}$$

**Example.**
$$
f(x) = \begin{cases}
0, & x \in \Q \\
n, & x = \frac{m}{n} \text{ in simplest form}
\end{cases}
$$
Then $\sup f  =\infty$, but $\operatorname{ess}\sup f = 0$. To see why, note that $f(x) \neq 0$ only on subsets of $\Q$. Since $\Q$ is countable it has measusure 0 and any subset of $\Q$ has measure 0.

**Note.**
The essential supremum of $|f-g|$ can equal 0 even if $f \neq g$. We define $f \equiv g$ if $f = g\ a.e.$. Then 
$$
\mathcal{L}^{\infty}(X) = \{f:X \to \mathbb{F}: \operatorname{ess}\sup |f| < \infty\}
$$
Then we define 
$$
L^{\infty}(X) = \mathcal{L}(X)/ \equiv
$$

So we can now define if $f,g \in L^p(X)$ for $1\leq p \leq \infty$, we define
$$
d(f,g) = \begin{cases}
\left( \int |f-g|^p d\mu \right)^{1/p} & 1 \leq p < \infty \\
\operatorname{f}\sup |f-g| & p=\infty
\end{cases}
$$
This is a metric on $L^p(X)$

### Facts about $L^p$ Spaces
1. $\left( \int |f+g|^p d\mu \right)^{1/p} \leq \left( \int |f|^p d\mu \right)^{1/p} + \left( \int |g|^p d\mu \right)^{1/p}$ (Minkowski Inequality)
2. $\operatorname{ess}\sup |f+g| \leq \operatorname{ess}\sup |f| + \operatorname{ess}\sup |g|$ 
3. $\int |fg| d\mu \leq \left( \int |f|^p d\mu \right)^{1/p} \cdot \left( \int |g|^q d\mu \right)^{1/q}$ where $\frac{1}{p}+\frac{1}{q} = 1$ (Holder's Inequality)
4. $\int |fg| d\mu \leq \operatorname{ess}\sup |f|\cdot \left( \int |g|d\mu \right)$ 

Consequences
1. $L^p(X)$ is a vector space.
2. $L^p(X)$ is a metric space with $d(f,g)$ defined before.
3. $L^p(X)$ is a complete space.

# Chapter 2: Normed Spaces
## 2.1 Definitions

**Definition.**
Let $X$ be a vectors space over the field $\mathbb{F}$. A norm on $X$ is a function $\|\cdot\|:X \to \R$ such that
1. $\|x\| \geq 0$ for all $x \in X$.
2. $\|x\| = 0$ iff $x = 0$.
3. $\|\alpha x\| = |\alpha| \|x\|$ for all $x \in X$ and all $\alpha \in \mathbb{F}$
4. $\|x+y\| \leq \|x\| + \|y\|$ for all $x,y \in X$.

**Example.**
Let $X = \mathbb{F}^k = \{(x_1,x_2,\dots,x_k):x_i \in \mathbb{F}\}$. Define
$$
\|(x_1,x_2,\dots,x_k)\| = \left(\sum_{i=1}^k |x_i|^2\right)^{1/2}
$$
This is a norm on $\mathbb{F}^k$.

**Example.**
Let $X = \mathbb{F}^k$. Define 
$$
\|(x_1,x_2,\dots,x_k)\| = \sum_{i=1}^k |x_i|
$$
This is also a norm on $X$.

**Example.**
Let $X$ be any vector space of dimension $k$. Let $\{e_1,\dots, e_k\}$ be a basis. Then, if $x \in X$ we have 
$$
x = \lambda_1e_1 + \dots \lambda_ke_k
$$
for some $\lambda_i \in \mathbb{F}$. Then, we can define a norm on $X$ by
$$
\|x\| = \left(\sum_{i=1}^k |\lambda_i|^2\right)^{1/2}
$$

**Example.**
Let $X = L^p(X)$ for $1 \leq p < \infty$. Then, we can define
$$
\|f\|_{L^p} = \left( \int_X |f|^p \right)^{1/p}
$$
This is a norm on $L^p$ called the $L^p$-norm.

**Example.**
The $L^{\infty}$-norm on $L^{\infty}$ is
$$
\|f\|_{L^{\infty}} = \operatorname{ess}\sup |f|
$$

**Example.**
Let $X$ and $Y$ are both normed vector spaces with norms $\|\cdot\|_X$ and $\|\cdot\|_Y$ respectively. We define a norm $\| \cdot \|_{X \times Y}$ on $X \times Y$ by 
$$
\|(x,y)\|_{X\times Y} = \|x\|_X + \|y\|_Y
$$

**Proposition.**
Let $X$ b a normed space, and let $\|\cdot\|$ be the norm on $X$. Then,
$$
d(x,y) = \|x-y\|
$$
defines a metric on $X$.

*proof.*
1. $d(x,y) = \|x-y\| \geq 0$ by definition of a norm.
2. $d(x,x) = \|x-x\| = 0$. Conversely, suppose $d(x,y) = 0$. Then, $\|x-y\|=0$. By the definition of norms, it follows that $x-y = 0$. Hence, $x = y$.
3. $d(x,y) = \|x-y\| = \|(-1)(y-x)\| = \|y-x\| = d(y,x)$
4. $d(x,y) = \|x-y\| = \|(x-z)+z-y\| = \|x-z\| + \|z-y\| = d(x,z)+d(z,y)$

**Lemma.** (Reverse Triangle Inequality)
Let $X$ be a vector space over $\F$. Let $x,y \in X$. Then, $$|\|x\|-\|y\|| \leq \|x-y\|$$

**Proposition.**
Let $X$ be a normed space over $\F$ with norm $\|\cdot\|$. Let $x_n$ and $y_n$ be sequences in $X$ such that $x_n \to x$ and $y_n \to y$. Let $\alpha_n$ be a sequence in $\F$ such that $\alpha_n \to \alpha$. Then,
1. $\lim \|x_n\| = \|x\|$
2. $\lim x_n+y_n = x+y$
3. $\lim \alpha_nx_n = \alpha x$

*proof.* (1)

Let $\epsilon>0$. We must find a $N \in \N$ such that
$$
|\|x_n\| - \|x\| < \epsilon
$$
whenever $n \geq N$. Since $x_n \to x$ it follows that there exists $N \in \N$ such that $\|x_n-x\| < \epsilon$ whenever $n\geq N$. By the reverse triangle inequality,
$$
|\|x_n\|-\|x\|| \leq \|x_n-x\| < \epsilon
$$

## 2.2 Finite Dimensional Normed Spaces
Let $X = \R^2$. For $(x,y)\in \R^2$,
$$
\|(x,y)\| = \sqrt{x^2+y^2}
$$

We can also think of $\R^2 = \R \times \R$. We can use the standard norm on $\R$, $|\cdot |$, and the product norm to define another norm on $\R^2$ by
$$
\|(x,y)\|_{\R \times \R} = |x|+|y|
$$

The upshot is that there are multiple ways to define norms on $\R$.
- What is the connection between these norms?

**Definition.**
Let $X$ be a vector space. Suppose $\|\cdot \|_1$ and $\|\cdot\|_2$ are norms on $X$. We say $\|\cdot\|_1$ and $\|\cdot\|_2$ are equivalent if there exists constants $c,C>0$ such that 
$$
c\|x\|_1 \leq \|x\|_2 \leq C\|x\|_1
$$
We use the notation $\|x\|_1 \approx \|x\|_2$. 

### Equivalent Norms

**Proposition.**
The symbol $\approx$ defines an equivalence relation on the set of norms on $X$.

*proof.*
- (Reflexive) Let $c,C = 1$. Then, $c\|x\|_1 \leq \|x\|_1 \leq C\|x\|_1$
- (Symmetric) Suppose $\|x\|_1 \approx \|x\|_2$. Then there exist $c,C >0$ such that $c\|x\|_1 \leq \|x\|_2$ and $\|x\|_2 \leq C\|x\|_1$ This means that $\|x\|_1 \leq \frac{1}{c}\|x\|_2$ and $\frac{1}{C}\|x\|_2 \leq \|x\|_1$. Hence, $$\frac{1}{C}\|x\|_2 \leq \|x\|_1 \leq \frac{1}{c}\|x\|_2$$
- (Transitive) Homework.

**Proposition.**
Let $X$ be a vector space, and $\|\cdot\|_1$ and $\|\cdot\|_2$ are norms on $X$. Let $d_1$ and $d_2$ be the metrics induced by $\|\cdot\|_1$ and $\|\cdot\|_2$ respectively. If $\|x\|_1 \approx \|x\|_2$, then
1. The sequence $x_n$ converges to $x$ in $(X,d_1)$ if and only if it converges to $x$ in $(X,d_2)$.
2. The sequence $x_n$ is Cauchy in $(X,d_1)$ if and only if it is Cauchy in $(X,d_2)$.
3. $(X,d_1)$ is complete if and only if $(X,d_2)$ is complete.

*proof.*
1. Suppose $x_n \to x$ in $(X,d_1)$. Then for each $\epsilon >0$, there exists $N \in \N$ such that $\|x_n-x\| < \epsilon/C$ whenever $n \geq N$. Then, $\|x_n-x\|_2 \leq C \|x_n-x\|_1 < \epsilon$ whenever $n \geq N$. Hence, $x_n \to x$ in $(X,d_2)$. The reverse direction is similar.
2. Rewrite the proof in 1. with $x$ replaced with $x_m$ and $m \geq N$,
3. Use 1. and 2.

### Equivalent Norms in Finite Dimensional Vector Spaces

**Definition.**
Let $X$ be a finite dimensional vector space with dimension $k$. Let $\|\cdot\|_2$ be defined by
$$
\|x\|_2 = \left(\sum_{k=1}^n |\lambda_k|^2 \right)^{1/2}
$$
where $x = \lambda_1 e_1 + \dots + \lambda_k e_k$ and $\{e_1,\dots,e_k\}$ are basis vectors.

**Lemma.**
Let $S^k := \{(x_1,x_2,\dots,x_k): |x_1|^2+|x_2|^2+\dots+|x_k|^2 =1\}$. Then, $S^k$ is compact.

**Lemma.** (Cauchy Schwarz)
Let $a_1,\dots,a_k, b_1,\dots,b_k \in \R$. Then,
$$
\left|\sum a_nb_n \right| \leq \left(\sum a_n^2\right)^{1/2}\left(\sum b_n^2\right)^{1/2}
$$

**Theorem.**
Let $X$ be a finite dimensional vector space with norm $\|\cdot\|$. Then, $\|x\| \approx \|x\|_2$

*proof.*

Let ${e_1,\dots,e_k}$ be a basis for $X$. Define
$$
M := \left(\sum_{n=1}^k \|e_n\|^2\right)^{1/2}
$$

Since the $e_n$ is a basis vector for each $i = 1,\dots, k$, it follows that $\|e_n\| \neq 0$. Hence, $M \geq 0$. Let $x \in X$. Then there exist scalars $\lambda_1,\dots,\lambda_k$ such that $x = \lambda_1 e_1 + \dots + \lambda_k e_k$. Then,
$$
\begin{align*}
\|x\| &= \|\lambda_1 e_1 + \dots + \lambda_k e_k\| \\
&\leq \sum |\lambda_n|\|e_n\| \\
&\leq \left(\sum |\lambda_n|^2\right)^{1/2}\left(\sum \|e_n\|^2\right)^{1/2} \\
& = M\|x\|_2
\end{align*}
$$

Define $f: \F^k \to \F$ by 
$$
f(\lambda_1,\dots,\lambda_k) = \left\| \sum \lambda_ne_n \right\|
$$

This function is continuous. Since $S^k$ is compact, it attains its maximum and minimum on $S^k$. Let $(\mu_1,\dots,\mu_k) \in S_k$ be the point at which $f$ attains its minimum. 

Define $f(\mu_1,\dots,\mu_k) = m$. Note that $m$ cannot be $0$ otherwise,
$$
\norm{\sum \mu_n e_n} = 0 \implies (\mu_1,\dots,\mu_k) = 0
$$
contradicting the assumption that $(\mu_1,\dots,\mu_k) \in S^k$.

Choose $x \in X$ such that $\norm{x}_1 = 1$. Then, 
$$\norm{x} \geq m$$
If $x$ is not on the unit sphere, let 
$$y=\frac{1}{\norm{x}_1}x$$
Then, $y$ is on the unit sphere so that
$$m \leq \norm{y}  = \norm{\frac{1}{\norm{x}_1}x} = \frac{\norm{x}}{\norm{x}_1}$$

This means that $m\norm{x}_1 \leq \norm{x} \leq M \norm{x}_1$.

**Corollary**
All norms on finite dimensional vector spaces are equivalent.

### Finite Dimensional Spaces are Well Behaved

**Proposition.**
Let $X$ be a finite dimensional vector space with basis $\braces{e_1,\dots,e_k}$. If
$$\norm{x} := \paren{\sum |\lambda_n|^2}^{1/2}$$
and $d$ is the metric induced by the norm $\norm{\cdot}$, then $(X,d)$ is complete.

*proof.*

Assume $x_n$ is a Cauchy sequence in $X$. Assume 
$$x_n = \lambda_{1,n}e_1 + \dots + \lambda_{k,n} e_k$$
Then, for each $\epsilon >0$ there exists $N \in \N$ such that $\norm{x_n-x_m} < \epsilon$ if $m,n \geq \N$. But,
$$\norm{x_n-x_m} = \paren{\sum_{j=1}^k |\lambda_{j,n}-\lambda_{j,m}}^{1/2} < \epsilon$$
whenever $n,m \geq N$. Take the sequence $\mu_{j,n} := \lambda_{j,m}$ where $1 \leq j \leq k$ is fixed. Since this is a Cauchy sequnce in $\F$ it follows that $\mu_{j,n}$ is convergent with limit $\mu_j$.

Define $x = \mu_1 e_1 + \dots + \mu_k e_k$. For each $\epsilon > 0$ there exist $N_j \in \N$ such that
$$|\mu_{j,n}-\mu_j| < \frac{\epsilon}{\sqrt{k}}$$
whenever $n \geq N_j$. Choose $N = \max(N_j)$. If $n \geq N$ we will have 
$$\norm{x_n-x} = \paren{\sum |\mu_{j,n}-\mu_j|^2}^{1/2} < \paren{\sum \paren{\frac{\epsilon}{\sqrt{k}}}^2}^{1/2} < \epsilon$$

**Corollary**
If $Y$ is a finite dimensional subspace of a normed vector space $X$, then $Y$ is closed.

## 2.3 Banach Spaces

### Infinite Dimensional Vector Spaces have Problems

**Example.**
Let $\mathcal{P}$ be the vector space of all polynomials defined on $[0,1]$. Note that $\mathcal{P} \subset C[0,1]$. Define
$$\norm{p}_1 = \sup_{[0,1]} p(x) \quad \norm{p}_2 = \int_0^1 |p(x)|\ dx$$

We will show that $\|x\|_1 \not \approx \|x\|_2$. Set $p(x) = x^n$. Then,
$$\norm{p}_1 = 1 \quad \norm{p}_2 = \frac{1}{n+1}$$
If these norms were equivalent, then there would exist $c>0$ such that
$$c\norm{p}_1 \leq \norm{p}_2 = \frac{1}{n+1}$$
But $c$ is fixed, so we can choose $n$ large enough sich that $c> \frac{1}{n+1}$.

**Example.**
Let $X = F(\N,\F)$. Recall that this is th set of sequences in $\F$. Define 
$$\norm{\braces{x_n}}_{\ell^{\infty}} = \sup \braces{|x_n|:n \in \N}$$
This norm induces a metric on $X$. We will state without proof that $(X,d)$ is a complete metric space.

**Proposition.**
Define $X = \ell^{\infty} := \braces{x \in F(\N,\F): \norm{\braces{x_n}}_{\ell^{\infty}} < \infty}$. Let $Y$ be the subspace of sequences which contain only finitely many non-zero terms. Then, $Y$ is not closed.

*proof.*

Consider the sequence $\braces{x_n} = \braces{\frac{1}{n}}$. Define the sequence of sequences 
$$
x_{n,m} = \begin{cases}
\frac{1}{n} & n \leq m \\ 0 & \text{otherwise}
\end{cases}
$$ 
Since $x_{n,m} \in Y$ and $x_{n,m} \to x_n$, but $x_n \notin Y$ it follows that $Y$ is not closed.

### Fixing Problems with Infinite Dimensional Vector Spaces

**Proposition.**
Let $X$ be a normed space, and let $Y$ be a subspace. Then $Y$ is also a subspace.

*proof.*
1. If $Y$ is a subspace then $0 \in Y$. Moreover, since $Y \subset \clos{Y}$ it follows that $0 \in \clos{Y}$.
2. Let $x,y \in \clos{Y}$. Then there exist sequences $x_n$ and $y_n$ such that $x_n \to x$ and $y_n \to y$. The sequence $x_n+y_n$ is a sequence in $Y$ with limit point $x+y$. Therefore, $x+y \in \clos{Y}$.
3. Let $x \in \clos{Y}$ and $\alpha \in \F$. Then there exists a sequence $x_n$ in $Y$ such that $x_n \to x$. Then, $\alpha x_n$ is a sequence in $Y$ that converges to $\alpha x$. Thus, $\alpha x \in \clos{Y}$.

By the subspace criterion, $\clos{Y}$ is a subspace of $X$.

**Lemma.**
Let $(X,d)$ be a metric space. Then, if $Y \subset X$, then $x \in \clos{Y}$ if and only if 
$$\inf \braces{d(x,y): y \in Y} = 0$$

**Lemma.** (Riesz Lemma)
Suppose $X$ is a normed space and $Y$ is a proper closed subspace. Let $0 < \alpha < 1$. Then, there exists $x_{\alpha} \in X$ such that 
$$\norm{x_{\alpha}-y}>\alpha$$ 
for $y \in Y$.