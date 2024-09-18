# Math 5401: Theory of Groups

**Professor:** Gary Brookfield
**Office Hours:** MW 3:00-4:30pm or by appointment
**Office:** Simpson Tower F202
**Email:** gbrookf@calstatela.edu

**Textbook:** Dummit and Foote, *Abstract Algebra, Theory and Applications*

**Exams:** There will be two midterm exams and the final exam.
- Midterm 1: Wednesday, September 25
- Midterm 2: Wednesday, October 30
- Final Exam: TBD

**Grades:**
- Homework: 20%
- Midterm 1: 20%
- Midterm 2: 20%
- Presentation: 10%
- Final Exam: 30%

# Chapter 1: Groups

**Definition.**
A *group* is an ordered pair $(G,\star)$ where $G$ is a set and $\star$ is a binary operation such that
1) $(a \star b) \star c = a \star (b \star c)$ for all $a,b,c \in G$
2) There exists an element $e \in G$ such that $a \star e = e \star a = a$ for all $a \in G$. $e$ is called the identity.
3) For each $a \in G$, there exist $a^{-1} \in G$ such that $a \star a^{-1} = a^{-1} \star a = e$. The element $a^{-1}$ is called the inverse of $a$.

**Note.**
A *binary operation* is a function $\star:G \times G \to G$. Thus, any binary operation is closed by definition.

**Definition.**
A group $(G,\star)$ is *abelian* if $a \star b = b \star a$ for all $a,b \in G$.

**Definition.**
The number of elements in $G$ is the *order* of $G$, denoted $|G|$. If $|G| < \infty$, we say that $G$ is a finite group.

**Notation.** We will use *multiplicative notation* for general groups.
- parentheses are suppresed, 
- the binary operation is suppressed, 
- the identity element is denoted 1, 
- the inverse of $a$ is denoted $a^{-1}$.
- $a^2 = aa$, $a^3 = aaa$, etc.
- $a^{-2} = a^{-1}a^{-1}$, $a^{-3} = a^{-1}a^{-1}a^{-1}$
- $a^0 = 1$
- $a^ma^n = a^{m+n}$
- $(a^m)^n$

**Notation.**
We will use additive notation for abelian groups.
- parentheses are suppresed, 
- the binary operation is $+$, 
- the identity element is denoted 0, 
- the inverse of $a$ is denoted $-a$.
- $2a = a+a$, $3a = a+a+a$, etc.
- $-2a = (-a)+(-a)$, $-3a = (-a)+(-a)+(-a) 
- $0a = 0$
- $ma+na = (m+n)a$
- $m(na) = (mn)a$

The following proposition will justify the use of this notation.

**Proposition.** (The Basics)
Let $(G,\star)$ be a group.
1. The identity is unique.
*proof.*
Suppose $e$ and $e'$ are identities. Then, $$e = ee' = e'$$ where the equalities follow from the fact that $e$ and $e'$ are identities.
2. Each $a \in G$ has a unique inverse.
*proof.*
Suppose $b$ and $b'$ are inverse of $a \in G$. Then, $$b = b \star e = b \star (a \star b') = (b \star a) \star b' = e \star b' = b'$$
3. $(a^{-1})^{-1} = a$
*proof.*
Since $aa^{-1} = a^{-1}a = 1$, it follows that $a$ is the inverse of $a^{-1}$. By uniqueness, the result follows.
4. $(ab)^{-1} = b^{-1}a^{-1}$
*proof.*
$$(ab)(b^{-1}a^{-1}) = a(bb^{-1})a^{-1} = a1a^{-1} = aa^{-1} = 1$$ $$(b^{-1}a^{-1})(ab) = a(bb^{-1})a^{-1} = a1a^{-1} = aa^{-1} = 1$$
5. For any $a_1,a_2,\dots,a_n \in G$, the value of $a_1 \star a_2 \star \dots \star a_n$ is independent of bracketing.
*proof sketch.* By induction.

**Example.** 
$(\mathbb{Z},+)$ is a group. $0$ is the identity and the additive inverse is the inverse.

**Example.** 
$(\mathbb{Z},-)$ is not a group since subtraction is not associative.

**Example.**
$(\mathbb{N},+)$ is not a group since it does not have an identity nor an inverse.

**Example.**
$(\mathbb{Z},\cdot)$ is not a group since 2 does not have a multiplicative inverse.

**Example.**
$(\mathbb{Q},\cdot)$ is not a group since $0$ does not have an inverse.

**Example.**
$(\mathbb{Q}^\times,\cdot)$ is a group.

**Example.**
Is there a subset of $\mathbb{Z}$ such that $(G,\cdot)$ is a group. Yes, for example the trivial group $(\{1\},\cdot)$. Moreover, the ordered pair $(\{1,-1\},\cdot)$ is also a group. These are the only subsets of $\mathbb{Z}$ that form a group with respect to multiplication.

**Example.**
What is a group of order 3? We can describe a group via its multiplication table. Let $G = \{1,a,b\}$. Then,

$$
\begin{array}{|c|ccc|}
\hline
& 1 & a & b \\
\hline
1 & 1 & a & b \\
a & a & b & 1 \\
b & b & 1 & a\\ \hline
\end{array}
$$

This is the unique group of order 3. This can be proven by filling out the table according to the cancelation law and the identity law. To prove this a group we need to check associativity and existence of identity and existence of inverses for each element. Moreover, this group is abelian!

**Proposition.** (Cancellation Law)
Let $G$ be a group and let $a,b,c \in G$. 
1. If $ac=bc$, then $a=b$
2. If $ca=cb$ then $a=b$

*proof.*
Suppose $ac=bc$. Then,
$$
\begin{aligned}
(ac)c^{-1} &= (bc)c^{-1} \\
a(cc^{-1}) &= b(cc^{-1}) \\
a1 &= b1 \\
a&=b
\end{aligned}
$$
The proof for part 2. is identical. 

**Example.**
If $ab=a$, then $b = 1$. 

**Example.** 
If $a^2=a$, then $a = 1$. This means that $1$ is the unique element such that $1^2=1$

**Note.**
By the cancellation law, every row and every column of a group multiplication table must be different. In fact, a group multiplication table must be a *latin square*. 

**Example.**
Let $G$ be a group of order 4 such that $ab=1$. By the homework, we know that $ba=1$. This means that $c^2 = 1$. Thus, $a$ and $b$ are inverses of each other and $c$ is its own inverse. We can fill in the rest of the group table like a sudoku puzzle. 
$$
\begin{array}{|c|cccc|}
\hline
& 1 & a & b & c\\
\hline
1 & 1 & a & b & c\\
a & a & c & 1 & b\\
b & b & 1 & c & a\\ 
c & c & b & a & 1\\\hline
\end{array}
$$

Observe that this group is abelian. However, this is not the only group of order 4. 

# Chapter 2: Subgroups

**Definition.**
Let $G$ be a group. A subset $H \subset G$ is a *subgroup* of $G$ if $H$ is a group with respect to the same operation as $G$. We use the notation $H \leq G$ to denote that $H$ is a subgroup of $G$. 

**Proposition.** (Subgroup Criterion)
A subset $H$ of a group $G$ is a subgroup if and only if
1. $1 \in H$.
2. $H$ is closed under group multiplication.
3. $H$ is closed under taking inverses. 

*proof.* ($\impliedby$)
Suppose $H \leq G$. Let $1_H$ be the identity of $H$ and let $1_G$ be the identity of $G$. Let $h \in H$. Then,
$$ 1_H h = h = 1_G h$$
By the cancellation law, $1_H = 1_G$. Closure under the group operation follows from the fact that a subgroup is a group. Lastly, we need to check that the inverse of $h\in H$ is also an inverse with respect to $G$. Let $h'$ be the inverse of $h$ with respect to the subgroup $H$. Then,
$$hh' = h'h = 1_H = 1_G$$
Thus, $h'$ is an inverse with repect to $G$ and $H$ is closed under taking inverse with respect to $G$. 

**Proposition.** (Alternative Subgroup Criterion)
A nonempty subset of $H$ is a subgroup of $G$ if and only if for all $h_1,h_2 \in H$ we have $h_1h_2^{-1} \in H$. 

**Example.**
Recall the Group of order 4 given by the multiplication table 
$$
\begin{array}{|c|cccc|}
\hline
& 1 & a & b & c\\
\hline
1 & 1 & a & b & c\\
a & a & c & 1 & b\\
b & b & 1 & c & a\\ 
c & c & b & a & 1\\\hline
\end{array}
$$
Then, $\{1\} \leq \{1,c\} \leq G$. 

**Note.**
Every group has the trivial group and itself as subgroups. 

**Proposition.** (Intersection of Groups is a Group)
Let $\mathcal{L}$ be the set of subgroups of a group $G$. Define
$$ H = \bigcap_{L \in \mathcal{L}} L$$
to be the intersection of all subgroups in $\mathcal{L}$. Then, $H$ is a subgroup of $G$.

**Definition.**
Let $X$ be a subset of a group $G$. By the previous proposition, the intersection of all subgroups of $G$ that contain $X$ is a subgroup of $G$, denoted $\langle X \rangle$.

**Note.**
If $H$ is a subgroup of $G$ and $X\subset H$, then $\langle X \rangle \leq H$. This means that $\langle X \rangle$ is the smallest subgroup containing $X$. 

**Theorem.** (Group Generated by an Element)
If $a \in G$ and $G$ is a group, then $$\langle a \rangle := \{a^n:n \in \mathbb{Z}\}$$

*proof.*
Let $H = \{a^n:n \in \mathbb{Z}\}$. By homework 2, $H$ is a subgroup and $a \in H$. Therefore, $\langle a \rangle \leq H$. Since $a \in \langle a \rangle$, $a^2 \in \langle a \rangle$ by closure of group multiplication. By induction, $a^n \in \langle a \rangle$ for any natural number $n$. Similarly, $a^{-1} \in \langle a \rangle$ since a subgroup must be closed under inverses. Moreover, $(a^{-1})^2 = a^{-2} \in \langle a \rangle$ by closure of group multiplication. By induction, $a^{-n} \in \langle a \rangle$. Lastly, $1 = a^0 \in \langle a \rangle$ since any subgroup must contain the identity. Hence, $\langle a \rangle \leq H$. This completes the proof.

## Cyclic Groups

**Definition.**
- A group $G$ is *cyclic* if $G = \langle a \rangle$ for some $a \in G$. 
- A subgroup $H$ is *cyclic* if $H = \langle a \rangle$ for some $a \in H$.
- The *order* of $a$ in $G$ is $|\langle a \rangle|$ and is denoted $|a|$.

**Example.**
Recall the group of order 4 with multiplication table
$$
\begin{array}{|c|cccc|}
\hline
& 1 & a & b & c\\
\hline
1 & 1 & a & b & c\\
a & a & c & 1 & b\\
b & b & 1 & c & a\\ 
c & c & b & a & 1\\\hline
\end{array}
$$
Let's examine the subgroups generated by eah of the elements
- $\langle a \rangle = \{1,a,b,c\}$, hence $|a| = 4$
- $\langle b \rangle = \{1,a,b,c\}$, hence $|b| = 4$
- $\langle c \rangle = \{1,c\}$, hence $|c| = 2$
- $\langle 1 \rangle = \{1\}$, hence $|1| = 1$ (this is true in any group)

Thus, G is cyclic. Moreover, the subgroup $H = \{1,c\}$ is also cyclic.

**Example.**
Consider the group $(\mathbb{C}^*,\cdot)$ where $\mathbb{C}^*$ is the set of nonzero complex numbers.
- $\langle i \rangle = \{1, i, -1, -i\}$. The order of $i$ is 4.
- $\langle 2 \rangle = \{2^n:n \in \mathbb{Z}\}$. The order of $2$ is infinite.

**Example.**
Consider the group $(\mathbb{Z},+)$.
- $\langle 3 \rangle = \{3n:n \in \mathbb{Z}\}$ The order of $3$ is infinite.
- $\langle 1 \rangle = \mathbb{Z}$
- $\langle -1 \rangle = \mathbb{Z}$

What about the group $\langle 3,5 \rangle$? We know that $\langle 3 \rangle \leq \langle 3,5 \rangle$. Similarly, we know that $\langle 5 \rangle \leq \langle 3,5 \rangle$. This means that all multiplies of 3 and 5 are in $\langle 3,5 \rangle$. Hence, $$\langle 3 \rangle \cup \langle 5 \rangle \subset \langle 3,5 \rangle$$ However, $\langle 3 \rangle\cup \langle 5 \rangle$ is not a group since it needs to be closed under addition. Notice that $$1 = 2\cdot 3-5 \in \langle 3,5 \rangle$$ Thus, $\mathbb{Z} = \langle 1 \rangle \leq \langle 3,5 \rangle \leq \mathbb{Z}$ and $\langle 3,5 \rangle = \mathbb{Z}$.

In general, $$\langle a,b \rangle = \{am+bn:m,n \in \mathbb{Z}\}$$ From number theory, we know that the smallest natural number in $\langle a,b \rangle$ is $\gcd(a,b)$. This means that $$\langle a,b \rangle = \langle \gcd(a,b) \rangle$$

**Proposition.**
Let $a \in G$ and suppose $G$ is a group. Then, $$|a| = |a^{-1}|$$.

*proof.*
Since $a^{-1} \in \langle a \rangle$, we have $\langle a^{-1} \rangle \leq \langle a \rangle$. Similarly, since $a^{-1} \in \langle a \rangle$, we have $\langle a^{-1} \rangle \leq \langle a \rangle$. Combining the two inequalities shows that $\langle a \rangle = \langle a^{-1} \rangle$. This completes the proof.

**Example.**
In homework 3, you will prove that $|ab| = |ba|$. However, be careful not to emulate the previous proof since $\langle ab \rangle \neq \langle ba \rangle$.

**Lemma.**
Let $a \in G$ and define $S = \{k\in \mathbb{Z}: a^k = 1\}$.
1. If $S = \{0\}$, $|a| = \infty$
2. Otherwise, let $n \in \mathbb{N}$ be the least natural number in $S$. Then, $|a| = n$, $\langle a \rangle = \{1,a,a^2,\dots,a^{n-1}\}$ and $S = n\mathbb{Z}$.

*proof.* (1)
 Suppose $S = \{0\}$ and $a^m = a^n$ for some $m,n \in \mathbb{Z}$. Then, $a^{m-n} = 1$ so $m-n \in S$ i.e. $m = n$. This means that each element of $\langle a \rangle$ is distinct and $|\langle a \rangle| = \infty$.

 *proof.* (2)
 Let $H = \{a^0,a^1,a^2,\dots,a^{n-1}\}$. Suppose $a^k \in \langle a \rangle$ for some $k \in \mathbb{Z}$. Write $k = nq+r$ with $0 \leq r < n$. Then, $$a^k = (a^n)^ka^r = a^r \in H$$ Pick $0 \leq k_1 \leq k_2 < n$ such that $a^{k_1} = a^{k_2}$. Then, $$a^{k_2-k_1} = a^{k_2}(a^{k_1})^{-1} = a^{k_2}(a^{k_2})^{-1} = 1$$ Hence, $k_2-k_1 \in S$. But, $0 \leq k_2-k_1 < n$ and $n$ is the smallest natural number in $S$, so that $k_2-k_1 = 0$ i.e. $k_2 = k_1$.

 **Example.**
 Suppose $|a| = 6$. What is the order of $a^4$? 
 - $a^4 \neq 1$
 - $(a^4)^2 = a^8 = a^2 \neq 1$
 - $(a^4)^3 = a^{12} = 1$ since $6 | 12$.
 
 Thus, the $|a^4| = 3$. Note that $\langle a^4 \rangle = \{1,a^2,a^4\}$.
 - $\langle a^5 \rangle = \langle a^{-1} \rangle = \langle a \rangle$ so $|a^5| = 6$
 - $\langle a^2 \rangle = \langle a^{-2} \rangle = \langle 4 \rangle$ so $|a^2| = 3$.
 - $\langle a^3 \rangle = \{1,a^3\}$ so $|a^3| = 2$.

 **Example.**
 Suppose $a^{10} = 1$. Then, $|a| \in \{1,2,5,10\}$ since the order of $a$ must divide any integer $m$ such that $a^{m} = 1$.

 **Theorem.** (p. 58)
 Every subgroup of a cyclic group is cyclic. Specifically, if $H \leq G = \langle a \rangle$ and $H$ is nontrivial, then $H = \langle a^d \rangle$ where $d$ is the least natural number such that $a^d \in H$.

*proof.*
Let $d$ and $H$ be defined as above. By assumption, $a^d \in H$. By the definition of $\langle a^d \rangle$, we know that $\langle a^d \rangle \leq H$. Let $h \in H$. Since $G$ is cyclic and $h \in G$, there exists an integer $k \in \mathbb{Z}$ such that $h = a^{k}$. By the division algorithm, there exist integers $q$ and $r$ such that $k = qd+r$. Then, $$h = a^k = (a^d)^qa^r$$ where $0 \leq r < d$. Thus, $a^r = h(a^d)^{-q} \in H$. By our choice of $d$, we must have $r=0$. This implies $$h = (a^{d})^q$$ Thus, $H \leq \langle a^d \rangle$. 

**Lemma.**
If $G = \langle a \rangle$ with $|G| = \infty$, then
1. $|a^d| = \infty$ for all $d \in \mathbb{Z} \setminus 0$.
2. $\langle a^m \rangle \leq \langle a^n \rangle$ if and only if $n$ divides $m$.
3. $\langle a^m \rangle = \langle a^m \rangle$ if and only if $|n| = |m|$

*proof.* (2)
Suppose $\langle a^m \rangle \leq \langle a^n \rangle$. This implies that $a^m \in \langle a^n \rangle$. Hence, there exists a nonzero natural number $k$ such that $a^m = a^{nk}$ Since $|a|= \infty$ it follows that $m = nk$ and $n$ divides $m$. The implications in this proof also work in the backwards direction.

**Theorem.**
Let $G = \langle a \rangle$ with $|G| = n < \infty$.
1. If $d > 0$ divides $n$ then $|a^d| = n/d$
2. For $m \neq 0$, let $d = \gcd(m,n)$. Then, $\langle a^m \rangle = \langle a^d \rangle$.
3. For each natural number $m$ that divides $n$, ther is a unique subgroup of $G$ with order $m$.

*proof.* (1)
Since $(a^d)^{n/d} = a^n = 1$ it follows that $|a^d|$ divides $n/d$. Thus, $|a^d| \leq n/d$. To prove the other inequality, we use contradiction. For the sake of contradiction, suppose $|a^d| = k < n/d$. Then, $1 = (a^d)^k = a^{dk}$. This implies that $|a|$ divides $dk$ and $|a| \leq dk < n$ which contradics the assumption that $|a| = n$. Hence, $|a^d| \geq n$. Combining the inequalities yields $|a^d| = n/d$.

*proof.* (2)
Recall that Bezout's lemma from number theory state that $$m\mathbb{Z}+n\mathbb{Z} = \gcd(m,n)\mathbb{Z}$$

We will first prove the claim $\langle a^d \rangle \leq \langle a^m \rangle$. From Bezout's lemma, there exist integers $x,y$ such that $d = xm+yn$. Then, $$a^d = a^{xm+yn} = (a^{m})^x(a^n)y = (a^m)^x \in \langle a^m \rangle$$ Hence, $\langle a^d \rangle$ is a subgroup of $\langle a^m \rangle$. This completes the proof of the claim.

Next we will prove the claim that $\langle a^m \rangle \leq \langle a^d \rangle$. Since $m \in m\mathbb{Z} + $

*proof.* (3)
By (1), $\langle a^{n/m} \rangle$ is a subgroup of order $m$. Suppose there exists $H \leq G$ and $|H| = m$. Then, $H = \langle a^k \rangle$ for some $k \in \mathbb{Z}$. By (2), $$H = \langle a^k \rangle = \langle a^d \rangle$$ where $d = \gcd(m,n)$. Moreover, $|H| = n/d$. This means that $d = n/m$ and $H = \langle a^{n/m} \rangle$. This shows that$\langle a^{n/m} \rangle$ is the unique subgroup of $G$ with order $m$.

**Note.**
From statements (1) and (2), we can conclude the formula $$|a^m| = \frac{n}{\gcd(m,n)}$$ 

**Example.**
Suppose $G = \langle a \rangle$ where $|a| = 4$. Label the elements of $G$ by $\{0,1,2,3\}$. The group table is given by


This is same as the additive group of integers modulo 4. We can say that the cyclic group of order 4 is isomorphic $(Z_4,+)$. 

More generally, the group $(\Z_n,+)$ is the group of integers modulo $n$. We will represent any cyclic group of order $n$ by integers modulo $n$. 

## Computations with Cyclic Groups

**Example.**
List all subroups of $\Z_{50}$.

There should be subgroups of order $n$ where $n | 50$. These are listed below
- Order 1: $\langle 0 \rangle = \{0\}$
- Order 2: $\langle 25 \rangle = \{0,25\}$
- Order 5: $\langle 10 \rangle = \{0,10,20,30,40\}$
- Order 10: $\langle 5 \rangle = \{0,5,10,15,20,25,30,35,40,45\}$
- Order 25: $\langle 2 \rangle = \{0,2,4,6,8,10,\dots,48\}$
- Order 50: $\langle 1 \rangle = \Z_{50}$

**Example.**
Find all elements of order 5 in $\Z_{50}$.

Since there is a unique subgroup of order 5, namely $\{0,10,20,30,40,50\}$, the orders of every element in that group must divide the order of the group. Since 5 is prime it follows that the orders of elements in this group must be either 1 or 5. The only element of order 1 is 0, so 10, 20, 30 and 40 are elements with order 5.

**Example.**
A cyclic group $G$ has subgroups $H$ and $K$ such that $|H| = 8$ and $|K| = 24$. Show that $H \leq K$.

$G$ must have finite order since the order of all nontrivial elements in an infinite cyclic group must have infinite order. Thus, $G$ has a unique subgroup of order 8, which is $H$. Moreover, $K$ is cyclic and $8|24$, $K$ has a unique subgroup of order 8. This subgroup is also a subgroup of $G$. By uniqueness, this subgroup must also be $H$.

**Example.**
A cyclic group $G$ has subgroups $H$ and $K$ such that $|H| = 8$ and $|K| = 18$. What can you say about $H \cap K$?

- Orders of subgroups of $H$: 1, 2, 4, 8
- Orders of subgroups of $K$: 1, 2, 3, 6, 9, 18

This means that $|H \cap K| = 2$. Hence, $H \cap K$ is the unique subgroup of order 2 in $G$.

**Theorem.**
Let $(G,*)$ be a set with operation $*$ such that
1. The operation is associative
2. An identity elements exists, denoted 1

Let $G^* := \{g \in G| g \text{ has an inverse in } G\}$. Then, $(G^*,*)$ is a group.

*proof.*
1. $G^*$ is closed under $*$ since $(gh)^{-1} = h^{-1}g^{-1}$.
2. Associativity is inherited from $G$.
3. The identity is in $G$ since 1 has an inverse in $G$ namely itself.
4. Inverses are contained in $G^*$ since $(a^{-1})^{-1}$.

**Example.**
Consider the complex numbers $\C$ under multiplication. This is not a group since 0 does not have an invers. We can construct the group $$\C^*:=\{z \in \C|z \neq 0\}$$

**Example.**
Consider the set $\Z_6 = \{1,2,3,4,5\}$ under multiplication. This is not a group. The group multiplication table is
$$
\begin{array}{c|cccccc}
    & 0 & 1 & 2 & 3 & 4 & 5 \\ \hline
    0 & 0 & 0 & 0 & 0 & 0 & 0 \\
    1 & 0 & 1 & 2 & 3 & 4 & 5 \\
\end{array}
$$
$\Z_6^* = \{1,5\}$ is the cyclic group $\Z_2$.

**Example.**
Consider the set $\Z_6 = \{1,2,3,4,5\}$ under multiplication. The group $$\Z_8^* = \{1,3,5,7\}$$
is not cyclic. In fact, it is isomorphic to the Klein 4 group.

**Lemma.**
$\Z_n^* = \{m \in \Z_n: \gcd(m,n) = 1\}$.

*proof.*

If $\gcd(m,n) = 1$, then Bezout's Identity implies that there exist integers $x$ and $y$ such that $$xm+yn = 1$$ Since $n = 0$ in $\Z_n$ is follows that $xm = 1$ in $\Z_n^*$.

**Theorem.** (Gauss 1800s)
$\Z_n^*$ is cyclic if and only if $n = 2,4,p^k,2p^k$ where $p$ is an odd prime.

## Functions

**Definition.**
Let $f: X \to Y$. 
1. $f$ is **injective** if $f(x_1) = f(x_2)$ implies $x_1=x_2$ for all $x_1,x_2 \in X$.
2. $f$ is **surjective** if for each $y \in Y$ there exists an $x\in X$ such that $y = f(x)$.
3. $f$ is **bijective** if its is injective and surjective.
4. The **identity function** on $X$, denoted $1_X: X \to X$ is defined by $1_X(x) = x$ for all $x \in X$. 
5. $f$ is **invertible** if there exists a function $g:Y \to X$ such that $g \circ f = 1_X$ and $f \circ g = 1_Y$. The inverse is unique and is denoted $f^{-1}$.

**Theorem.**
$f$ is invertible if and only if it is bijective.

**Theorem.**
If $f:X \to Y$, $g: Y \to Z$, and $h: Z \to W$, then 
$$
h \circ (g \circ f) = (h \circ g) \circ f
$$

**Definition.**
Let $X$ and $Y$ be sets. We say $X$ and $Y$ are **equinumerous** (have the same **cardinality**) if there exists a bijection $f:X \to Y$.

**Theorem.**
If $X,Y$ are finite and have the same cardinality and $f:X \to Y$, then the following are equivalent.
- $f$ is injective
- $f$ is surjective
- $f$ is bijective
- $f$ is invertible

## Symmetric Groups

Let $X$ be a nonempty set. Let $G$ be the set of all functions from $X$ to $X$ with composition as an operation.
1. By the theorem on functions, composition is associative.
2. The identiy function $1_X:X \to X$ is the identity with respect to composition.

However, not all functions in $G$ are invertible. For example, the constant function (assuming $X$ has more than a single element) is not invertible.

**Definition.**
Let $S_X$ be the set of invertible elements of $G$. Using the notation from before we define $S_X := G^*$. This is a group by a theorem proven above. Elements of $S_X$ are called **permutations** of $X$. We call $S_X$ the **symmetric group**.

If $X = [n] := \{1,2,\dots,n\}$, then $S_X$ is denoted $S_n$.

**Example.**
$S_4$ is the set of permutations of $[4]$. How many elements are in $S_4$? Let $\sigma \in S_4$. There are four choices for $\sigma(1)$, three choices for $\sigma(2)$, two choices for $\sigma(3)$, and only one choice for $\sigma(4)$. Hence there are $4!= 24$ elements in $S_4$. Applying this logic to $S_n$ yields

**Theorem.** 
$|S_n| = n!$

## Cycle Notation

**Definition.**
Define the $m$-cycle $\sigma := (a_1\ a_2\ \dots \ a_m) \in S_n$ with $m \leq n$ where $$\sigma(a_i) = \sigma(a_{i+1})$$ and all elements not specified in the cycle are fixed. 

Note that there are multiple representations a cycle since $(1 2 3) = (231) = (312)$.

For $S_4$, we can begin listing the various $m$-cycles
1. Identity: $\{(1)\}$
2. 2-cycles: $\{(12), (13), (14), (23), (24), (34)\}$
3. 3-cycles: $\{(123),(132), (124), (142), (134), (143), (234), (243)\}$
4. 4-cycles: $\{(1234),(1243), (1324), (1342), (1423), (1432)\}$

However, this only covers 21 out of the 24. There are also permutations that are products of cycles.

Products of cycles: $\{(12)(24), (13)(24), (14)(23)\}$

**Theorem.**
Let $S_n$ be a symmetric group, then
1. Every elements of $S_n$ can be written uniquely as a product of disjoint cycles.
2. Disjoint cycles commmute.
3. The order of a $k$-cycle is $k$.
4. The order of a product of disjoint cycles is the least common multiple of the length of the cycles.
5. If $0 < m \leq n$, then the number of $m$-cycles $$\frac{n(n-1)(n-2)\cdots(n-m+1)}{m}$$

**Example.**
Let $\sigma \in S_8$ such that
$$
\begin{array}{|c|cccccccc|}
\hline
n & 1 & 2 & 3 & 4 & 5 & 6 &7 & 8 \\ \hline
\sigma(n) & 3 & 5 & 7 & 1 & 2 & 6 & 4 & 8 \\\hline
\end{array}
$$
Starting at $1$, we see that 
$$1 \to 3 \to 7 \to 4 \to 1$$
Starting at the next smallest element, $2$, we see that
$$2 \to 5 \to 2$$
Starting at the next smallest element, $6$, we see that
$$6 \to 6$$
Starting at the next smallest element, $8$, we see that
$$8 \to 8$$
Hence, we can write $\sigma$ as disjoint cycles
$$\sigma = (1374)(25)$$

**Example.**
$(1234)(3456) = (123)(456)$

**Example.** What is the inverse of $(1234)$?
$$(1234)(4321) = 1$$
Hence, $(1234)^{-1} = (4321)$. Since any element in a symmetric group can be rewritten as a product of disjoint cycles, you can use cycle reversal on each disjoint cycle to find the inverse.

**Example.**
Find the subgroup generated by $\sigma = (123456) \in S_6$.
- $\sigma^1 = (123456)$
- $\sigma^2 = (135)(246)$
- $\sigma^3 = (14)(25)(36)$
- $\sigma^4 = (153)(264)$
- $\sigma^5 = (165432)$
- $\sigma^6 = 1$

**Example.**
Consider the symmetric group on 5 elements, $S_5$. Let's split this group into cycle types.
- There is one 1-cycle. This has order 1.
- There are 10 2-cycyles. This has order 2.
- There are 20 3-cycles. This has order 3.
- There are 30 4-cycles. This has order 4.
- There are 24 5-cycles. This has order 5.
- There are 20 permutations which are products of a 2-cycle and a 3 cycle. Once we chose a 3-cycle, the 2-cycle is immediately determined. These permutations have order 6.
- There are 15 permutations which are productsof two 2 cycles. Once we chose a two cycle there are 3 options for the other two cycle. However this double counts the amount of this cycle type since disjoint cycles can commute. These permutations have order 4.

Note that these cycle types are grouped via the partitions of 5.

**Example.**
How many elements of $S_6$ have order $6$?

Since the order is determined by the cycle type,
- 6-cycles have order 6. There are 120 such cycles.
- Products of 2-cycles and 3-cycles also have order 6. First, we pick a 3-cycle. There are 40 3-cycles. Then, we pick a 2-cycle from the remaining 3 elements. There are 6 ways to do this. Therefore, there are $40 \cdot 3 = 120$ elements of this cycle type in $S_6$.

**Example.**
How many cyclic subgroups of order $6$ in $S_6$?

Since each cyclic subgroup will have 2 elements that have order 6, and there are a total of 240 elements in $S_6$ with order 6, there are 120 possible cyclic subgroups of order 6.

**Example.**
Find the elements of the subgroup $\vbrackets{(12)(345)}$.
$$\vbrackets{(12)(345)} = \braces{1,(12)(345),(543),(12),(345),(12)(543)}$$

## Transpositions

**Definition.**
A **transposition** is a 2-cycle.

**Example.**
In $S_3 = \braces{1,(12),(13),(123),(321)}$ we can write
- $(123) = (12)(23)$
- $(321) = (23)(12) = (12)(13)$
- $1 = (12)(12) = (13)(13)$

This hints that elements in the symmetric group can be written as a product of transpositions. Note that this is not unique.

**Theorem.**
Any element in $S_n$ can be written as a product of transpositions.

*proof.*
From the algorithm shown before, we can write any element in $S_n$ as a product of disjoint cycles. Thus, it suffices to show that any cycle can be written as a product of transpositions. In fact, 
$$
(a_1a_2\dots a_m) = (a_1a_2)(a_2a_3)\dots(a_{m-1}a_m)
$$
This completes the proof. $\blacksquare$

**Theorem.**
No product of an even number of transpositions is equal to a product of an odd number of transpositions.

*proof.* (TBD)

**Definition.**
A permutation is **even** if it is a product of an even number of transpositions. A permutation is **odd** if it is a product of an odd number of transpositions.

**Example.**
In $S_3$
- $\braces{(12), (23), (13)}$ are odd permutations.
- $\braces{1, (123), (321)}$ are even permutations.

## The Alternating Group

Observe that the cycle type determines the parity of the number of transpositions.
- If a cycle has even length, it is an odd permutation.
- If a cycle has odd length, it is an even permutation.
- An even permutation multiplied by an even permutation is an even permutation.
- An even permutation multiplied by an odd permutation is an odd permutation.
- An odd permutation multiplied by an odd permutation is an even permutation.
- The inverse of an even permutation is also an even permutation.
- The inverse of an odd permutation is also an odd permutation.

**Theorem.**
Let $A_n$ be the set of even permuatations of $S_n$. Then, $A_n \leq S_n$ called the **alternating group** on $n$.

**Example.**
$A_3 = \braces{1,(123),(321)}$.

**Example.**
In $S_4$,
- $1$ even 1
- $(12)$ odd 6
- $(123)$ even 8 
- $(1234)$ odd 6
- $(12)(34)$ even 3

Taking the even elements yields $A_4$. Hence, $|A_4| = 12 = \frac{1}{2}|S_4|$.

**Theorem.**
$|A_n| = \frac{1}{2}|S_n| = \frac{1}{2}n!$ for $n \geq 2$.

*proof.*
Let $B_n$ denote the odd permutations of $S_n$. Then, $A_n \cup B_n = S_n$. Since, $A_n \cap B_n = \varnothing$ it suffices to show that $|A_n| = |B_n|$. Fix $\sigma \in B_n$. Consider the functions $\phi:A_n \to B_n$ and $\psi:B_n \to A_n$ such that
$$
\phi(g) = \sigma g \quad \psi(g) = \sigma^{-1}g
$$
Lets show that these functions are well defined. If $g in A_n$, then $g$ is an even permutation. Since the prouct of an even permutation and an odd permutation is odd, $\phi(g) \in B_n$. Now suppose $g \in B_n$, then $g$ is an odd permutation. Moreover, $\sigma^{-1}$ is an odd permutation. Since the product of an odd permutation and an odd permutation is even, it follows that $\psi(g) \in A_n$. Furthermore, $\psi \circ \phi = \phi \circ \psi = id$. Hence, there is a bijection from $A_n$ to $B_n$. This implies $|A_n| = |B_n|$. $\blacksquare$.