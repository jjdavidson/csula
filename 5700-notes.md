# Math 5700: Numerical Linear Algebra Methods

**Professor:** Dong Zhou
**Email:** dzhou@calstatela.edu
**Office Hours:** Monday 2-3pm, Wednesday 10-11am
**Office:** 221F

**Textbook:** *Numerical Linear Algebra.* Lloyd N. Trefethen & David Bau III

**Grade**
- Attendance: 5%
- Homework: 30%
- Midterm 1: 20%
- Midterm 2: 20%
- Course Project: 25%

# Week 1

## Numerical Linear Algebra
methods for solving linear algebra problems by numerical computation

### Topics
- *Linear Systems*: Solve $Ax = b$ where $A$ is a nonsingular square matrix. How would you invert this matrix numerically? There are **direct methods**, such as Gaussian elimination, which give exact solutions. There are also **iterative methods** that give approximate solutions. Iterative methods are preferable when direct methods run into space and time limitations.
- *Least Squares Problems*: Find a solution to $Ax=b$, but $A$ is not a square matrix. This usually occurs in linear regression applications. An overdetermined system has an $m \times n$ matrix where $m>n$.
- *Eigenvalue Problems*: $Av = \lambda v$. Find all, or a selection, of eigenvalues and eigenvectors. Usually, iterative methods work best for the eigenvalue problem.
- *Singular Value Decomposition*: $A=U\Sigma V^T$ where $U,\Sigma,V$ are matrices satisfying certain properties. The SVD has applications in image compression.

### Applications
- *Physics and Engineering*: Solving large systems of linear equations arising from discretizing differential equations (e.g., finite difference, finite element methods). One example is the heat equation $$u_t = \Delta u +f$$ Using finite element method, we can turn the differential equation into a difference equation $A\vec{u}=\vec{b}$ where the solution $\vec{u}$ represents an approximation of the PDE over a discretized domain.
- *Optimization*: Linear Programming, where matrices are used to represent constraint and objective functions.
- *Image Processing*: image compression (SVD), image recognition (eigenfaces in facial recognition)
- *Social Networks, Clustering*: eigenvalue problems
- And many more...

**Example**
Recall the definition of the derivative from calculus
$$f'(x) = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h}$$
A numerical method for approximating $f'(x_0)$
$$f'(x_o) = \frac{f(x_0+h)-f(x_0)}{h}$$
where $h$ is small. The approximation above is known as the **finite difference equation**. In particular, this is the forward difference equation.

How good is this finite different approximation?
$$
\begin{aligned}
\text{Error} &= \frac{f(x_0+h)-f(x_0)}{h} - f'(x_0) \\
&= \frac{f(x_0+h)-f(x_0) -f'(x_0)h}{h}
\end{aligned}
$$

By Taylor's Theorem, we know that
$$ f(x_0+h) = f(x_0)+f'(x_0)h+\frac{f''(x_0)}{2}h^2+ \mathcal{O}(h^3)$$

Substituting into the error we see that
$$
\begin{aligned}
\text{Error} &= \frac{\frac{f''(x_0)}{2}h^2+ \mathcal{O}(h^3)}{h} \\
&= \frac{f''(x_0)}{2}h + \mathcal{O}(h^2) \\
&= \mathcal{O}(h)
\end{aligned}
$$

We should expect for $h$ small enough, the approximation error decays like $\mathcal{O}(h)$. In other words, if we decrease the step size $h$ in half, the error will also be reduced by half. 

Let's implement this in Matlab
```
function roundofferr_example

% define f(x) and f'(x)
f = @(x) x^2;
df = @(x) 2*x;

% specify x_0 value
x0 = 2.1;

% Compute the error of the forward difference for decreasing step sizes
for n = 1:40
    h = 2^(-n);
    Df = (f(x0+h)-f(x0))/h;
    err = abs(Df-df(x0));
    fprintf(sprintf('n= %d, h = %.14e, err = %.14e\n', n,h,err));pause
end


```


We make two observations:
- At first, the approximation error decreases according to $\mathcal{O}(h)$
- At some point, the error increases even when the step size $h$ decreases. This is due to *roundoff error*. 

# Week 2

### Floating Point Number System

**Definition.**
A *floating point number system* (FPNS) $F(\beta,k,m,M)$ is a subset of the real number system. Elements in $F$ are the number 0 and all numbers of the form $$\pm\frac{s}{\beta^k}\times \beta^e$$ where
- $\beta$: the base
- $k$: the precision (number of digits in the base expansion)
- $s$: an integer in the range $[1,\beta^k]$
- $e$: the exponent in the range $[m,M]$

**Example.**
Consider the FPNS $F(10,2,0,1)$. Numbers will be of the form
$$\pm0.d_1d_2\times 10^e$$ where
- $e \in [0,1]$
- $1 \leq d_1 \leq 9$
- $0 \leq d_2 \leq 9$

There are a total 361 floating point numbers. Listed below.

$$
\begin{array}{|c|ccc|ccc|}
\hline
0 & +0.10\times 10^0 & \dots & \pm0.19 \times 10^0 & +0.10\times 10^1 & \dots & \pm0.19 \times 10^1 \\
& +0.20\times 10^0 & \dots & \pm0.29 \times 10^0 & +0.20\times 10^1 & \dots & \pm0.29 \times 10^1 \\
& \vdots & \cdots & \vdots & \vdots & \cdots & \vdots \\
& +0.90\times 10^0 & \dots & \pm0.99 \times 10^0 & +0.90\times 10^1 & \dots & \pm0.99 \times 10^1 \\
\hline
\end{array}
$$

For this FPNS:
- the smallest nonzero positive number is $0.10\times 10^0 = 0.1$
- the largest positive number is $0.99\times 10^1 = 9.9$
- the number $0.1234$ is represented in the FPNS by $0.12$
- Any attempt to create a number between $0$ and $1$ results in an *underflow*. 
- Any attempt to creat a number larger than $9.9$ results in an *overflow*.

### Real Numbers vs Floating Point Numbers

- The real numbers are continuous, but FPNS is discrete. 
- The real numbers are infinite, but FPNS is finite
- The real numbers are uniformly distributed, but FPNS is not uniformly distributed. 

In the FPNS example $F(10,2,0 1)$, the floating point numbers in the interval $[0.1,1]$ are spaced $0.01$ units apart. However, in the interval $[1,10]$, the floating point numbers are spaced $0.1$ units apart.

### IEEE Standard Floating Point Format

Most computers use double precision (64-bit) FPNS $F(2,53,-1022,1023)$. The smallest number in this system is $$2^{-1022} \approx 2.225 \times 10^{-308}$$ and the largest number in this system is $$2^{1023}-1 \approx 1.798\times 10^{308}$$

### Machine Epsilon

The *machine epsilon* is the largest relative error that can occur due to rounding in floating point number systems. It is defined as
$$\epsilon_{machine} = \frac{1}{2}\beta^{1-k}$$
This number is half the distance between 1 and the next largest floating point number. 

**Example.**
In $F(10,2,0,1)$, $$\epsilon_{machine} = \frac{1}{2}10^{-1} = 0.05$$
In IEEE double precision floating point system, $$\epsilon_{machine} = \frac{1}{2}2^{-53} \approx 1.1102\times10^{-16}$$
In MATLAB, you can ype the command *eps* to find the machine epsilon. However, in MATLAB they define the machine epsilon to be the distance between 1 and the next largest floating point number. 

Machine epsilon has the property such that for all $x \in \mathbb{R}$, there exists a floating point number $x'$ such that the relative error is bounded by machine epsilon
$$|x-x'| \leq \epsilon_{machine} |x|$$
Let $fl(x)$ be the floating point representation of a real number. Then, $$fl(x) = x(1+\epsilon)$$ for some $|\epsilon| \leq \epsilon_{machine}$. 

### Roundoff Error and Approximation Error

Let's return to the forward difference quotient example:
$$\frac{f(x_0+h)-f(x_0)}{h} \approx f'(x_0)$$
Rewriting the error in terms of floating point representation yields
$$
\begin{aligned}
&\frac{f(x_0+h)(1+\epsilon_1)-f(x_0)(1+\epsilon_2)}{h}-f'(x_0) \\
=&\frac{f(x_0+h)-f(x_0)}{h} + \frac{\epsilon_1f(x_0+h)-\epsilon_2f(x_0)} {h} -f'(x_0) \\
=& \mathcal{O}(h)+Cf(x_0)\frac{\epsilon_{machine}}{h}
\end{aligned}
$$

The first term is the approximation error inherent in the forward difference method approximation scheme. The appoximation error shrinks as the step size shrinks. 

The second term represents the error due to using a FPNS. Notice that the error increases as the step size decreases. We usually do not notice the roundoff error since the coefficient depends on the machine epsilon which is usually very small.

![Graph of Truncation Error vs Roundoff Error](img/5700error-tradeoff.png)

The roundoff error takes over roughly when
$$\frac{1}{2}f''(x_0) \approx cf(x_0)\epsilon_{machine}$$
In our example, $f(x) = x^2$, $x_0 = 2.1$, so $f''(x_0) = 2$ and $f(x_0) \approx 4$. Hence, 
$$\frac{1}{2}\cdot 2h \approx c \cdot 4 \frac{10^{-16}}{h}$$
so $h \approx 10^{-8}$.

## 1.1 Matrices and Vectors

### Matrix-Vector Multiplication.
Let $A \in \mathbb{R}^{m\times n}$ be an $m \times n$ matrix, and $x \in \mathbb{R}^n$ be a column vector.
$$
A = (a_{ij})
\qquad \vec{x} =
\begin{bmatrix}
x_1 \\ \vdots \\x_n
\end{bmatrix}
$$

The product $\vec{b} = A \vec{x} \in \mathbb{R}^m$ and the $i$th entry of $\vec{b}$ is
$$b_i = \sum_{j=1}^na_{ij}x_j = a_{i1}x_1 + a_{i2}x_2 + \dots + a_{in}x_n$$

Another way to view this product is to think of it as a linear combination of the columns of $A$ with coefficients from $\vec{x}$. We can write $A = [\vec{a}_1 \ \vec{a}_2 \ \dots \ \vec{a}_n]$. Then, 
$$
\begin{bmatrix}
b_{1} \\ \vdots \\ b_{m}
\end{bmatrix}
= \begin{bmatrix}
\sum_{j=1}^na_{1j}x_j \\
\vdots \\
\sum_{j=1}^na_{mj}x_j
\end{bmatrix} 
=\sum_{j=1}^nx_j
\begin{bmatrix}
a_{1j} \\\vdots \\ a_{mj}
\end{bmatrix}
=\sum_{j=1}^n x_j \vec{a}_j
$$

### Matrix-Matrix Multiplication.
Let $A \in \mathbb{R}^{m\times n}$ and $X \in \mathbb{R}^{n\times p}$, then the product $B = AX \in \mathbb{R}^{m \times p}$. There are two main way to interpret the product $B$. 

**Dot Products:** If we think in terms of the entries of the matrices.
$$
A = (a_{ij})
\quad
X = (x_{ij})
\quad
B = (b_{ij})
$$
The $b_{ij}$ entry of $B$ is the dot product of the $i$th row of $A$ and the $j$th column of $X$.
$$b_{ij} = \sum_{k=1}^n a_{ik}x_{kj}$$

**Linear Combinations:** 
If we write $B = [\vec{b}_1,\dots,\vec{b}_p]$ and $X = [\vec{x}_1,\dots,\vec{x}_p]$, then the $ith$ column of $B$ can be interpreted as a linear combination of the columns of $A$ with coefficients from the $i$th column of $X$. In particular, $$[\vec{b_1},\dots,\vec{b_p}] = [A\vec{x}_1,\dots,A\vec{x}_p]$$

### Operation Count
To estimate the cost (in time to execute) of these computations, we count the number of *floating point operations* (flops). Each addition, subtraction, multiplication,division, or square root counts as one flop.

**Example.**
Count the flops of matrix-vector multiplication $\vec{b} = A \vec{x}$.
```
for (i = 1...m) {
    for (j = 1...n) {
        b_i := b_i+a_{ij}x_j
    }
}
```
In the innermost loop we do 1 multiplication and 1 addition per loop leading to 2n FLOPS. The innermost loop is repeated $m$ times leading to a total of $2mn$ FLOPS.

If $m=n$, the flop counts for performing the matrix-vector multiplication $A\vec{x}$ is $2n^2$. This is order $n^2$, which is denoted $\mathcal{O}(n^2)$.

If the matrix size doubles $(n \to 2n)$ then the flop count quadruples $(2n^2 \to 8n^2)$.

**Example.**
Count the FLOPS of matrix-matrix multiplication. $B = AX$. Since $$B = [\vec{b}_1 \dots \vec{b}_p], \qquad X = [\vec{x}_1 \dots \vec{x}_p]$$ the matrix multiplication can be interpreted as $p$ matrix-vector multiplications.

## 1.2 Triangular Systems

**Definition.**
Let $A \in \mathbb{R}^{n \times n}$. We call $A$
- *Upper Trianglular* if $a_{ij} = 0$ for $i>j$.
- *Lower Triangular* if $a_{ij} = 0$ for $i<j$.

### Lower Triangular Systems
Consider a lower triangular system $A\vec{x} = \vec{b}$ where $A$ is nonsingular.

*Forward Substitution*: start with first row and move down.
- 1st row: $a_{11}x_1 = b_1 \implies x_1 = \frac{b_1}{a_{11}}$
- 2nd row:
- $n$th row: 

**Example.**
$$
\begin{bmatrix}
1 & 0 & 0 \\
-1 & 2 & 0 \\
2 & -5 & 3
\end{bmatrix}
\begin{bmatrix}
x_1 \\ x_2 \\x_3
\end{bmatrix} = 
\begin{bmatrix}
1 \\ 2 \\ 3
\end{bmatrix}
$$

### FLOP count for Forward Substitution

Algorithm in pseudo code:
```
for (i = 1...n) {
    for (j = 1...i-1) {
        b_i = b_i-a_{ij}x_j
    }
    x_i := b_i/a_{ii}
}
```

### Upper Triangular Systems
Consider an upper triangular system $A\vec{x} = \vec{b}$ where $A$ is nonsingular.

*Back Substituion*: start from the last row and move upward.
- $n$th row: $a_{nn}x_n = b_n \implies x_n = \frac{b_n}{a_{nn}}$
- $(n-1)$th row: $a_{n-1,n-1}x_{n-1}+a_{n-1,n}x_n = b_{n-1} \implies x_n = \frac{b_n}{a_{nn}}$


### LU Decomposition
For a general nonsingular $A \in \mathbb{R}^{n \times n}$ and a linear system $$A \vec{x} = \vec{b}$$ if $A$ can be expressed as a product of a lower triangular matrix and an upper triangular matrix: $$A = LU$$ Then, $A\vec{x} = LU\vec{x} = \vec{b}$ can be solved with two steps:
- Step 1: Solve $L\vec{y} = \vec{b}$ using forward substitution.
- Step 2: Solve $U\vec{x} = \vec{y}$ using back substitution.

The decomposition/factorization $$A = LU$ is called the LU decomposition. The method for solving $A\vec{x} = \vec{b}$ is called the *Gaussian Eliminiation method*.

In MATLAB, the LU decomposition is computed using the command `lu`. For example,
```
[L,U] = lu(A)
```

# Week 3

### Gaussian Elimination

- the simplest way to solve $A\vec{x} = \vec{b}$ by hand
- the standard method for solving $A\vec{x} = \vec{b}$ on a computer

**Gaussian Elimination in Two Phases**
1. transform $A\vec{x} = \vec{b}$ into an upper-triangular matrix by *elementary row operations*.
2. Solve the upper-triangular system by back substitution.

In order to apply gaussian elimination, we write the linear system into the form of an augmented matrix $$[A\ |\ \vec{b}]$$

The following elementary row operations do not alter the solution to the linear system:
- Add a multiple of one row to another
- Interchange two rows
- Multiply one row by a nonzero constant.

To transform $A$ into an upper-triangular matrix, we apply row operations to get zeros below the diagonal.

**Step 1.**
$$
\begin{bmatrix}
    a_{11} & a_{12} & \dots & a_{1n} & b_1 \\
    a_{21} & a_{22} & \dots & a_{2n} & b_2 \\
    \vdots & \vdots & & \vdots & \vdots \\
    a_{m1} & a_{m2} & \dots & a_{mn} & b_m \\
\end{bmatrix}
$$

**Step 2.**

**After $n-1$ Steps.**
$$
\begin{bmatrix}
    * & \dots & * & * \\
    & \ddots & \vdots & \vdots \\
    &   & * & * \\
\end{bmatrix} = 
\begin{bmatrix}
    U & y
\end{bmatrix}
$$

### Interpretationf of the multipliers $l_{ij}$
Recall that $A\vec{x}$ can be viewed as a linear combination of columns of $A$, where the coefficients are the components of $\vec{x}$. 
$$
A\vec{x} = 
\begin{bmatrix}
    \vec{a}_1 & \dots & \vec{a}_n
\end{bmatrix} 
\begin{bmatrix}
    x_1 \\ \dots \\ x_n
\end{bmatrix} =
x_1\vec{a}_1 + x_2\vec{a}_2 + \dots + x_n\vec{}
$$

Similarly, $\vec{x}^TA$ is a linear combination of rows of $A$, where the coefficients are the components of $x$. This can be seen from the fact that $$(\vec{x}^TA)^T = A^T\vec{x}$$
The RHS of the equation is just a linear combination of the columns of $A^T$. However, a column of $A^T$ is just a row of $A$.

In Gaussian elimination
$$
A = 
\begin{bmatrix}
\vec{a}_1^T \\ \vdots \\ \vec{a}_m^t
\end{bmatrix} \qquad
\text{where $\vec{a}_i^T$ is the $i$th row of $A$}
$$

**Step 1:** $A \to L_1A$
$$
A = 
\begin{bmatrix}
\vec{a}_1^T \\ \vdots \\ \vec{a}_2^t
\end{bmatrix} \to
\begin{bmatrix}
\vec{a}_1^T \\ \vec{a}_2^T-l_{21}\vec{a}_1^T \\
\vec{a}_3^T - l_{31}\vec{a}_1^T \\ \vdots \\
\vec{a}_m^T - l_{m1}\vec{a}_1^T
\end{bmatrix} =
\begin{bmatrix}
1 \\ 
l_{21} & 1\\
l_{31} & & 1\\
\vdots & & & \ddots\\
l_{m1} & & & & 1
\end{bmatrix}A = L_1A
$$

Observe that the matrix $L_1$ is lower-triangular.

**Step 1:** 

**After Step $n-1$:** 

The elimination process is equivalent to multiplying $A$ by a sequence of lower-triangular matrices $L_i$ on the left to obtain an upper triangular matrix $$L_{n-1}\cdots L_2L_1 A = U$$
Moreover, since lower triangular matrices are closed under multiplication and matrix inverses, it follows that 
$$A = L_1^{-1}L_2^{-1} \cdots L_{n-1}^{-1}U = LU$$

Thus, Gaussian elimination is a method that can be used to perform the $LU$ decomposition of a nonsingular matrix.

**Example.** Compute the $LU$ decomposition of $A$ and solve $A\vec{x} = \vec{b}$ where
$$
A = \begin{bmatrix}
2 & 4 & 2 & 3 \\
-2 & -5 & -3 & -2 \\
4 & 7 & 6 & 8 \\
6 & 10 & 1 & 12
\end{bmatrix}, \qquad
\vec{b} = \begin{bmatrix}
-3 \\ -3 \\ -1 \\ 16
\end{bmatrix}
$$

Perform Gaussiang elimination column by column. Save space by storing multipliers where the zeros are in each column.

Step 1:
$$
\begin{bmatrix}
2 & 4 & 2 & 3 \\
l_{21} & -1 & -1 & 1 \\
l_{31} & -1 & 2 & 2 \\
l_{41} & -2 & -5 & 3
\end{bmatrix} \qquad
\begin{array}{c}
\\
l_{21} = -1 \\ 
l_{31} = 2 \\ 
l_{41} = 3
\end{array}
$$

Step 2:
$$
\begin{bmatrix}
2 & 4 & 2 & 3 \\
l_{21} & -1 & -1 & 1 \\
l_{31} & l_{32} & * & * \\
l_{41} & l_{42} & * & *
\end{bmatrix} \qquad
\begin{array}{c}
\\
 \\ 
l_{32} = 1 \\ 
l_{42} = 2
\end{array}
$$

Step 2:
$$
\begin{bmatrix}
2 & 4 & 2 & 3 \\
l_{21} & -1 & -1 & 1 \\
l_{31} & l_{32} & * & * \\
l_{41} & l_{42} & l_{43} & *
\end{bmatrix} \qquad
\begin{array}{c}
\\
\\ 
\\ 
l_{43} = 
\end{array}
$$

**Remark:**
Gaussian Elimination in the augmented system:
$$
\begin{bmatrix}
A & \vec{b}
\end{bmatrix} \to
\begin{bmatrix}
U & \vec{y}
\end{bmatrix},
\qquad U\vec{x} = \vec{y} \to \vec{x}
$$

# Week 4

### FLOP Count of Gaussian Elimination
Let $A$ be an $n \times n$ matrix. Gaussian Elimination can be described by the following pseuodocode

```
% loop over columns of A
for j = 1,...,n-1:
    % loop over rows below A(j,j)
    for i = j+1,...,n
        % Get multiplier
        l(i,j) = A(i,j) / A(i,i)
        % Row operation
        A(i,j+1:n) := A(i,j+1:n)-l(i,j) * A(j,j+1:n)
```

In the inner for loop, we perform one division and $n-j$ additions and multiplications. Summing over the loops the number of FLOPS is
$$
\sum_{j=1}^{n-1} \sum_{i=j+1}^n (2(n-j)+1) = \mathcal{O}\left(\frac{2}{3}n^3\right)
$$

### Gaussian Elimination As Presented Has Some Issues

**Example.** (Issue due to nonsingular submatrices.)
$$
A = \begin{bmatrix}
0 & 1 \\ 1 &1
\end{bmatrix}
$$
Gaussian Elimination fails since the upper left entry is 0. In the homework you prove that Gaussian Elimination works if and only if all leading principal submatrices of $A$ are nonsingular.

**Example.** (Issue due to machine epsilon.)
$$
A = \begin{bmatrix}
10^{-20} & 1 \\ 1 & 1
\end{bmatrix}
$$

**Step 1:** 
$$
A = \begin{bmatrix}
10^{-20} & 1 \\ 0 & 1-10^{20}
\end{bmatrix}
$$
$l_{12} = 10^{20}$. Therefore, the $LU$ decomposition is 
$$
L = \begin{bmatrix}
1 & 0 \\ 10^{20} & 1
\end{bmatrix} \qquad
U = \begin{bmatrix}
10^{-20} & 1 \\ 0 & 1-10^{20}
\end{bmatrix}
$$
In a floating point system where $1-10^{20}$ is represented by $-10^{20}$
The $LU$ decomposition is 
$$
L = \begin{bmatrix}
1 & 0 \\ 10^{20} & 1
\end{bmatrix} \qquad
\tilde{U} = \begin{bmatrix}
10^{-20} & 1 \\ 0 & -10^{20}
\end{bmatrix}
$$
This second decomposition does not multiply to $A$.

### Gaussian Elimination with Pivoting
We want to introduce a **pivoting strategy** to make the diagonal entry as far from 0 as possible. There are two strategies
- Partial Pivoting: using only row interchanges
- Complete Pivoting: using row and column interchanges

We want to be careful not to add to much complexity to the algorithm in order to not lose the $\mathcal{O}(n^3)$ time complexity.

For partial pivoting, the main idea is to interchange the pivot entry with the largest element (in magnitude) below it in the mattrix during each step. This means we will need to keep track of all the row swaps with a permutation matrix.

The choice of pivot implies
$$
|l_{ik}| \leq 1, \quad l_{ik} = \frac{a_{ik}^{(k-1)}}{a_{kk}^{(k-1)}}, \qquad i = k+1,\dots,n
$$

**Example.**
Use Gaussian eliminatioin with partial pivoting to solve
$$
\begin{bmatrix}
0 & 4 & 1 \\ 1 & 1 & 3 \\ 1 & 3 & 1
\end{bmatrix}
\begin{bmatrix}
x_1 \\ x_2 \\x_3
\end{bmatrix} = 
\begin{bmatrix}
9 \\ 6 \\ 1
\end{bmatrix}
$$

We begin by swapping Row 1 and Row 3. Then we compute the multipliers.
$$
\begin{bmatrix}
1 & 3 & 1 \\ 1 & 1 & 3 \\ 0 & 4 & 1
\end{bmatrix}
\begin{array}{l}
\\ l_{21} = 0.5 \\ l_{31} = 0
\end{array}
$$
Performing row operatiions yields
$$
\begin{bmatrix}
1 & 3 & 1 \\ 1 & 1 & 3 \\ 0 & 4 & 1
\end{bmatrix}
$$
Next we swap Row 2 and Row 3 and compute the multipliers

Perfoming row operations yields

The $LU$ decomposition is thus
$$
L = \begin{bmatrix}
1 & 0 &  \\ 0 & 1 & 0 \\ 1/2 & 1/2 & 1
\end{bmatrix} \qquad
U = \begin{bmatrix}
2 & -2 & 1 \\ 0 & 4 & 1 \\ 0 & 0 & 1
\end{bmatrix}
$$

To solve the system, we must perform the same permutations to the vector $b$. Then, we can perform forward subsitution to find $y$. Lastly, we can perform backward substitution to find $x$.

Note, in the previous example, $LU \neq A$. Instead, $LU = PA$ where $P$ is a permutation matrix.

**Definition.**
A **permutation matrix** is a square matrix that has exactly one entry of 1 in each row and column with all other entries 0.

In the previous example,
$$
LU = PA, \quad P =
\begin{bmatrix}
0 & 0 & 1 \\
1 & 0 & 0 \\
0 & 1 & 0
\end{bmatrix}
$$

Note that the matrix $P$ can be decomposed into two permuation matrices corresponding to row swaps.
$$
P=P_2P_1, \quad 
\begin{bmatrix}
1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0
\end{bmatrix}
\begin{bmatrix}
0 & 0 & 1 \\ 0 & 1 & 0 \\ 1 & 0 & 0
\end{bmatrix}
$$

Note that if $P$ is a permutation matrix, it is also an orthogonal matrix meaning that $$P^{-1} = P^T$$

Gaussion elimination with partial pivoting produces the following matrix decomposition
$$LU = PA \quad \text{or} \quad P^TLU = A$$
where
- $L$: unit lower triangular with $|l_{ij}| \leq 1$
- $U$: upper triangular
- $P$: a permutation matrix

Such decomposition is not unique in general. In MATLAB, the command $lu$ returns an $LU$ decomposition using patial pivoting. To get the matrices $L$, $U$, and $P$ use the command
```
[L,U,P] = lu(A)
```

### Cost of Partial Pivoting
At each step of Gaussian elimination with partial pivoting we need to :
- search for the largest entry in magnitude
- perform row interchange.

At step $k$ ($n-1$ steps total):
1. Compare $n-k+1$ values to obtain the maximum. This requires comparing $n-k$ pair of values.
2. Switching rows requires fetching and storing $2(n-k+1)$ entries.

Since Gaussian elimination has $n-1$ steps, there are a total of 
$$
\sum_{k=1}^{n-1} (n-k) + 2(n-k+1)= \frac{3(n-1)(n)}{2}+2(n-1) = O(n^2)
$$

For $n$ large, the cost of partial pivoting $O(n^2)$ is small compared to the cost of Gausssian elimination $O(n^3)$.

### Scaled Partial Pivoting
There is a small refinement that can be made to Gaussian elimination which many numerical computing software packages implement.

**Example.**
$$
\begin{bmatrix}
1 & 10^4 \\ 1 & 10 ^{-4}
\end{bmatrix}
\begin{bmatrix}
x_1 \\x_2
\end{bmatrix}
= \begin{bmatrix}
10^4 \\ 1
\end{bmatrix}
$$
The solutiion to the system above is 
$$x = \frac{10^8-10^4}{10^8-1} \approx 1, \quad y = \frac{10^4-1}{10^4-10^{-4}} \approx 1$$


**Standard Partial Pivoting**
We find the multiplier $l = 1$ and we perform $R_2-R_1$ to obtain
$$
\left[
\begin{array}{cc|c}
1 & 10^4 & 10^4 \\ 0 & 10^{-4} - 10^4 & 1-10^4
\end{array}
\right]
$$
In a FPNS where $10^{-4}-10^4$ is represented by $-10^4$ and where $1-10^4$ is represented by $-10^4$, the augmented matrix becomes
$$
\left[
\begin{array}{cc|c}
1 & 10^4 & 10^4 \\ 0 & - 10^4 & -10^4
\end{array}
\right]
$$
This will lead to a solution of $x = 0$ and $y = 1$.

**Scaled Partial Pivoting**

First, we will compute the relative sizes of the entries in the first column to the rest of the column
- $\frac{1}{10^4}$ is small
- $\frac{1}{10^{-4}}$ is big

Therefore, we will swap the rows.

### Complete Pivoting
At step $k$,
1. Find the largest entry in magnitude of the submatrix $A_{k:n,k:n}$.
2. Use a row and column interchange to move the entry to the pivot.

To find the largest entry, we have to make $(n-k+1)^2-1$ comparisons. Since their are $n-1$ steps in Guassian elimination, the total cost is on the order of $O\left(\frac{1}{3}n^3\right)$. This is the same cost as Gaussian elimination, so this method is rarely used in practice.

Since there are both row and column permutations, gaussian eliminations with completed pivoting produces a decomposition
$$
PAQ = LU
$$
where $P$ and $Q$ are permutations matrices.

# Week 5

## Special Linear Systems

Let $A$ be an $n \times n$ nonsingular matrix. Since these matrices usually arise in applications, there are some common matrix types that arise
- Symmetric/ Hermitian matrices
- Positive definite matrices
- Banded matrices

### Symmetric matrices

**Definition.**
An $n \times n$ real valued matrix $A$ is said to be **symmetric** if 
$$A^T = A$$
An $n \times n$ complex valued matrix $A$ is said to be **hermitian** if 
$$A^* = A$$ where $A^*$ denotes the conjugate transpose.

If $A$ is symmetric and all its leading principal submatrices are nonsingular, then there is a unique factorization
$$A = LDL^T$$
where $L$ is unit upper triangular and $D$ is a diagonal matrix.

By exploiting symmetry, the operation count can be cut iin half. Therefore, the operation count is on the order of $$O\left(\frac{1}{3}n^3\right)$$

### Positive Definite Matrices
An $n \times n$ real valued matrix is **positive definite** if for all nonzero $x \in \R^n$, the following quadratic form $$xAx^T > 0$$

If $A$ is positive definite, then
- $A$ is nonsingular
- all its eignevalues are positive
- all its leading principal submatrices are positive definite. In particular, all diagonal entries are positive.

If $A$ is a symmetric positive definite matrix, then it has the following factorizations
- $A = LDL^T$ and $D$ has positive diagonal entries
- **Cholesky Factorization:** $A = R^TR$ and $R$ is upper triangular with positive diagonal entries.

The operation count for the Cholesky factorization is also cut in half due to exploiting symmetry. Therefore, the operation count is on the order of $$O\left(\frac{1}{3}n^3\right)$$

### Banded Matrices and Tridiagonal Matrices
**Definition.**
An $n \times n$ matrix is **banded** if the only nonzero entries lie on the diagonal and off-diagonal entries. The **bandwidth** is the number of nonzero diagonals in the matrix. A **tridiagonal matrix** is a banded matrix with bandwidth equal to three.

Gaussian elimination for tridiagonal matrices only requires one row operation in every step. In fact, there are only 3 FLOPS in each step
1. Find multiplier
2. Multiply diagonal element by multiplier
3. Subtract off-diagonal entry by falue in step 2.

Hence, the operation count for Gaussian eliminations is $$3n-3 = O(3n)$$ Banded matrices are example of **sparse matries**. The majority of entries in a sparse matrix are 0. Sparse matrices usually arise when there is only some local dependency between the entries.