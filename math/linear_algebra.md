# Linear Algebra: Geometry, Determinants, and Eigenvectors

Study notes from October 16–17, 2026.

These notes summarize our discussion in plain English. Unless stated otherwise, vectors and matrices are real, and geometric statements use the usual Euclidean dot product.

## 1. A matrix transforms vectors

For a matrix with columns $\mathbf a_1,\ldots,\mathbf a_n$,

$$
A\mathbf x=x_1\mathbf a_1+\cdots+x_n\mathbf a_n.
$$

Each column tells us where a standard basis vector goes: $A\mathbf e_i=\mathbf a_i$.

For example,

$$
A=\begin{pmatrix}a&b\\c&d\end{pmatrix}
$$

sends $(1,0)$ to $(a,c)$ and $(0,1)$ to $(b,d)$. The unit square becomes the parallelogram formed by these two columns.

## 2. Linear independence and dependence

A linear combination means multiplying vectors by numbers and adding them:

$$
c_1\mathbf v_1+\cdots+c_k\mathbf v_k.
$$

The **span** is the set of all such combinations.

Vectors are **linearly independent** when

$$
c_1\mathbf v_1+\cdots+c_k\mathbf v_k=\mathbf0
$$

forces every coefficient to be zero. They are **linearly dependent** if some coefficients, not all zero, make that sum zero.

Equivalently, a dependent set contains a vector that can be expressed as a combination of the others.

### Different directions are not enough

Consider

$$
\mathbf u=(1,0),\qquad \mathbf v=(0,1),\qquad \mathbf w=(1,1).
$$

They point in different directions, but $\mathbf w=\mathbf u+\mathbf v$, so they are dependent.

For an independent list:

- The first vector is nonzero and spans a line.
- The second lies outside that line and expands the span to a plane.
- The third lies outside that plane and expands the span to three dimensions.
- The fourth must lie outside the span of the first three.

Independent vectors do not have to be perpendicular. Four independent vectors require an ambient space of at least four dimensions.

If one of four vectors is a combination of the others, their span has **at most** three dimensions; it may have fewer.

## 3. Determinants measure signed volume

For a square $n\times n$ matrix $A$, the absolute value $|\det A|$ is the $n$-dimensional volume of the parallelotope formed by its columns. It is also the factor by which the transformation scales $n$-dimensional volume.

| Dimension | Quantity |
|---|---|
| 2 | Area of a parallelogram |
| 3 | Volume of a parallelepiped |
| 4 and higher | Higher-dimensional volume |

A positive determinant preserves orientation; a negative determinant reverses it. Ordinary area and volume use the absolute value.

### The 2-by-2 formula

$$
\det\begin{pmatrix}a&b\\c&d\end{pmatrix}=ad-bc.
$$

To see the geometry, write the columns as

$$
(a,c)=r(\cos\alpha,\sin\alpha),\qquad
(b,d)=s(\cos\beta,\sin\beta).
$$

Their signed area is base times signed height:

$$
rs\sin(\beta-\alpha)
=rs(\cos\alpha\sin\beta-\sin\alpha\cos\beta)
=ad-bc.
$$

For example,

$$
\det\begin{pmatrix}2&3\\1&4\end{pmatrix}=8-3=5.
$$

### The 3-by-3 formula

$$
\det\begin{pmatrix}a&b&c\\d&e&f\\g&h&i\end{pmatrix}
=a(ei-fh)-b(di-fg)+c(dh-eg).
$$

Geometrically, for columns $\mathbf u,\mathbf v,\mathbf w$,

$$
\det[\mathbf u\ \mathbf v\ \mathbf w]
=\mathbf u\cdot(\mathbf v\times\mathbf w).
$$

The cross product is perpendicular to the base formed by $\mathbf v,\mathbf w$, and its length is the base area. Dotting it with $\mathbf u$ multiplies that area by the signed perpendicular height.

This explains the connection to base area times height. Deriving the coordinate formula for the cross product is a separate step.

### Cofactor expansion: 4-by-4 and beyond

Choose a row or column. For each entry, delete its row and column, take the determinant of what remains, and multiply by the entry and its alternating sign.

For expansion along row $i$,

$$
\det A=\sum_{j=1}^{n}a_{ij}(-1)^{i+j}\det M_{ij},
$$

where $M_{ij}$ is the matrix obtained by deleting row $i$ and column $j$.

For the first row of a $4\times4$ matrix:

$$
\det A
=a_{11}\det M_{11}
-a_{12}\det M_{12}
+a_{13}\det M_{13}
-a_{14}\det M_{14}.
$$

Each minor here is $3\times3$. A row or column containing many zeros makes the calculation easier.

The alternating signs reflect the fact that exchanging two columns reverses orientation. The full expansion follows from the determinant's linearity in each column, its sign change under exchanges, and $\det I=1$.

## 4. Why determinant zero means no inverse

For a square matrix,

$$
\det A=0
\iff \text{the columns are linearly dependent}
\iff A\mathbf x=\mathbf0\text{ for some }\mathbf x\ne\mathbf0
\iff A\text{ is not invertible}.
$$

Geometrically, the transformation loses at least one dimension. Different inputs become indistinguishable.

For example,

$$
A=\begin{pmatrix}1&2\\2&4\end{pmatrix},
\qquad
A\begin{pmatrix}x\\y\end{pmatrix}
=(x+2y)\begin{pmatrix}1\\2\end{pmatrix}.
$$

Every output lies on one line. In particular,

$$
A\begin{pmatrix}2\\0\end{pmatrix}
=A\begin{pmatrix}0\\1\end{pmatrix}
=\begin{pmatrix}2\\4\end{pmatrix}.
$$

An inverse cannot recover both original inputs from the same output. This is lost information, not merely a difficult calculation.

## 5. Higher-dimensional volume and perpendicular height

An axis-aligned four-dimensional box with side lengths $a,b,c,d$ has volume $abcd$. Its points satisfy four independent coordinate bounds. We can define and calculate this volume even though we cannot directly visualize it.

The same base-times-height rule extends to higher dimensions:

$$
V_n=V_{n-1}h.
$$

Suppose four independent vectors in $\mathbb R^5$ span a four-dimensional subspace. Let $\mathbf n$ be a unit vector perpendicular to that subspace. For a fifth vector,

$$
h=|\mathbf v_5\cdot\mathbf n|,
\qquad
V_5=V_4|\mathbf v_5\cdot\mathbf n|.
$$

Example: if the first four vectors are $\mathbf e_1,\ldots,\mathbf e_4$ and the fifth is $(2,3,4,5,6)$, then $V_4=1$, $\mathbf n=\mathbf e_5$, and $V_5=6$.

The first four components tilt the fifth edge along the base. Its fifth component supplies the perpendicular height.

If the first four vectors are dependent, the five vectors cannot span five dimensions, so the five-dimensional volume is zero.

### Can we always find a perpendicular vector?

If a subspace $W$ has dimension $r$ inside $\mathbb R^n$, its orthogonal complement has dimension

$$
\dim W^\perp=n-r.
$$

Thus four vectors in $\mathbb R^5$ always have a common nonzero perpendicular vector. If those four vectors are independent, their perpendicular space is a line, giving two opposite unit normals.

Find a normal by solving

$$
\mathbf v_i\cdot\mathbf n=0
\quad\text{for every }i,
$$

then divide a nonzero solution by its length.

If the given vectors span the entire ambient space, only the zero vector is perpendicular to all of them.

## 6. Eigenvectors and eigenvalues

An **eigenvector** is a nonzero vector satisfying

$$
A\mathbf v=\lambda\mathbf v.
$$

The number $\lambda$ is its **eigenvalue**.

For a real eigenvector and real eigenvalue, the transformed vector remains on the same line through the origin:

- $\lambda>0$: same direction, scaled length.
- $\lambda<0$: opposite direction on the same line.
- $\lambda=0$: sent to the origin.

Example:

$$
A=\begin{pmatrix}2&0\\0&3\end{pmatrix}.
$$

Then

$$
A\begin{pmatrix}1\\0\end{pmatrix}
=2\begin{pmatrix}1\\0\end{pmatrix},
\qquad
A\begin{pmatrix}0\\1\end{pmatrix}
=3\begin{pmatrix}0\\1\end{pmatrix}.
$$

But $(1,1)$ is not an eigenvector: its image $(2,3)$ is not a scalar multiple of it.

An eigenvector is not necessarily a unit vector. Every nonzero scalar multiple of an eigenvector is also an eigenvector with the same eigenvalue.

## 7. Why use lambda I minus A?

### Why does A v = lambda v not imply A = lambda?

$A$ is a matrix; $\lambda$ is a number. The equation describes what $A$ does to one particular nonzero vector. It does not say that $A$ scales every vector by that number.

A vector cannot be cancelled like a nonzero scalar.

If $A\mathbf v=\lambda\mathbf v$ held for **every** vector, then $A=\lambda I$.

### Why include the identity matrix?

The identity satisfies $I\mathbf v=\mathbf v$, so

$$
\lambda\mathbf v=(\lambda I)\mathbf v.
$$

Therefore,

$$
A\mathbf v=\lambda\mathbf v
\iff(\lambda I-A)\mathbf v=\mathbf0.
$$

We use $\lambda I$ to represent scalar multiplication as a matrix operation, allowing subtraction from $A$.

$$
\lambda I-A
=\begin{pmatrix}\lambda-a&-b\\-c&\lambda-d\end{pmatrix}
\quad\text{when}\quad
A=\begin{pmatrix}a&b\\c&d\end{pmatrix}.
$$

### Does a zero product mean one factor must be zero?

Not for a matrix acting on a vector:

$$
\underbrace{\begin{pmatrix}0&0\\0&-1\end{pmatrix}}_{\text{nonzero matrix}}
\underbrace{\begin{pmatrix}1\\0\end{pmatrix}}_{\text{nonzero vector}}
=\mathbf0.
$$

So $(\lambda I-A)\mathbf v=\mathbf0$ does **not** imply $\lambda I-A=0$ or $\mathbf v=\mathbf0$.

We exclude the zero vector from the definition of an eigenvector because it satisfies the equation for every $\lambda$ and identifies no direction.

## 8. The characteristic polynomial

The **characteristic polynomial** is

$$
p_A(\lambda)=\det(\lambda I-A).
$$

For an $n\times n$ matrix, it has degree $n$. Its roots are the eigenvalues, allowing complex roots when necessary.

The reasoning is:

1. Seek a nonzero vector satisfying $A\mathbf v=\lambda\mathbf v$.
2. Rearrange to $(\lambda I-A)\mathbf v=\mathbf0$.
3. Such a vector exists exactly when $\lambda I-A$ is singular.
4. Therefore solve $\det(\lambda I-A)=0$.

It is **$\lambda I-A$** that must be singular. The original matrix $A$ need not be singular.

For our diagonal example,

$$
p_A(\lambda)
=\det\begin{pmatrix}\lambda-2&0\\0&\lambda-3\end{pmatrix}
=(\lambda-2)(\lambda-3).
$$

Thus the eigenvalues are $2$ and $3$. After finding each eigenvalue, solve $(A-\lambda I)\mathbf v=\mathbf0$ to find its eigenvectors.

Some books use $\det(A-\lambda I)$ instead. It differs by the factor $(-1)^n$ and has the same roots.

## Key connections

- **Independence:** each vector adds a direction outside the span of the preceding vectors.
- **Determinant:** signed volume scaling.
- **Zero determinant:** dimension is lost, so the transformation has no inverse.
- **Eigenvector:** a nonzero vector on which the matrix acts as scalar multiplication.
- **Characteristic polynomial:** finds the scalars for which such vectors exist.
