# Introduction to topology

## Basic Topology

### Topological Equivalence

> When we say two objects are “topologically equivalent”, we mean equivalent up to **homeomorphism**.

**Homeomorphism: **a continuous function between two objects or topological spaces which 

1. is continuous.
2. is a bijection (one to one and onto, hence invertible).
3. has a continuous inverse function.

Examples: continuous stretching, bending …

![image-20240509191543329](./../../../../../../code/Markdown/images/image-20240509191543329.png)

### Topological Invariants

Properties or numeric quantities that remain unchanged under homeomorphism, such as Euler Characteristic.
$$
\chi = V-E+F
$$

> The Euler Characteristic can be generalized to parametrise general spaces via the process of “cellulation”, which is division of surface into polygonal cells, such as triangulation.
>
> 比如上节课学的toric code, 就是将一个曲面cellulation 成了很多方形.

![image-20240509192425675](./../../../../../../code/Markdown/images/image-20240509192425675.png)

![image-20240509192313230](./../../../../../../code/Markdown/images/image-20240509192313230.png)

> Since $\chi(torus) \ne \chi(sphere)$, the sphere and torus are topologically inequivalent.

**Genus: ** The formal term used to count the number of handles in a surface.

> 可以理解为洞的个数, sphere没有, torus有一个.

#### Theorem:

The Euler Characteristic of any compact orientable surface of genus $g$ is ==$2-2g$.==
$$
\chi = 2-2g
$$


>![image-20240509192859851](./../../../../../../code/Markdown/images/image-20240509192859851.png)

#### Theorem:

All compact surfaces with genus $g$ are homeomorphic to a sphere with $g$ handles.

### Application

> For toric code, the number of qubits encoded is $2-\chi$.

$$
physical\ qubits=E\\
generators = (F-1)+(V-1)\\
logical\ qubits = physical\ qubits - generators = 2+E-F-V = 2-\chi
$$

> 其实这个公式不止对toric code成立, 为toric code时, $\chi=0$, 所以逻辑比特为2, 如果换用其他拓扑图形, 使得$\chi$ 减小, 我们就可以获得更多的逻辑比特. 

Generalizing to genus g g-torus:

1. Cellulate a general torus with a square lattice.
2. Define stabilizer generators.

$$
\chi(g-torus) = 2-2g\\
qubits\ encoded = 2g
$$

## Homology

![image-20240509194041338](./../../../../../../code/Markdown/images/image-20240509194041338.png)

n-cell: an n-dimensional object in a cellulation.

+ 0-cell: vertices.
+ 1-cell: edges.
+ 2-cell: plaquettes.

### Chains

![image-20240510160136154](./../../../../../../code/Markdown/images/image-20240510160136154.png)

> 可以理解为选取了边集中的一个子集(标记为1的部分).

![image-20240510160533331](./../../../../../../code/Markdown/images/image-20240510160533331.png)

Similarly, we can define 0-chains, 2-chains and n-chains.

![image-20240510160643697](./../../../../../../code/Markdown/images/image-20240510160643697.png)

#### The Boundary Map

n-boundary map $\partial_n$: a group-structure preserving map from the set of n-chains c to the (n-1)-chains d.

![image-20240510161128369](./../../../../../../code/Markdown/images/image-20240510161128369.png)

![image-20240510161253266](./../../../../../../code/Markdown/images/image-20240510161253266.png)

### Cycles

Central concept in homology.

n-cycle: an n-cycle is an n-chain c satisfying:
$$
\partial_nc = 0_{n-1}
$$
A cycle is a chain with null boundary, i.e. “without a boundary”.

![image-20240510161611396](./../../../../../../code/Markdown/images/image-20240510161611396.png)

### Boundary

n-boundary chains: any n-chain which is the boundary of (n+1)-chain is called n-boundary chain or n-boundary.

### Notations

$$
C_n: &\text{The group of n-chains.}\\
Z_n: &\text{The group of n-cycles.}\\
B_n: &\text{The group of n-boundaries.}\\
$$

+ ==Every n-boundary is an n-cycle, but not every n-cycle is a n-boundary.==

![image-20240510162649486](./../../../../../../code/Markdown/images/image-20240510162649486.png)

> 如上图, 左侧的trivial cycle恰好为一个boundary, 而右侧的两个none-trivial cycle不是boundary.

+ $\partial_{n-1}\partial_nc_n = 0_{n-2}$

> Since the boundary of a boundary is null.

+ $B_n \subseteq Z_n \subseteq \C_n$.

> Homology studies the properties and interplay of these groups.

### Homology Equivalence

Two n-chains c and d are homologically equivalent if they are equal up to composition with an n-boundary b, 
$$
c = d+b,\ where\ b\in B_n
$$
![image-20240510163431752](./../../../../../../code/Markdown/images/image-20240510163431752.png)

> 我们可以使用这一性质, 将n-chains划分为不同的等价类.

![image-20240510163841591](./../../../../../../code/Markdown/images/image-20240510163841591.png)

![image-20240510163953913](./../../../../../../code/Markdown/images/image-20240510163953913.png)

> 说实话这里我还没太懂这几个群的rank怎么计算.

**Claim: **$rank(C_n) = rank(Z_n)+rank(B_{n-1})$.

> 对于边界算子, kernel为$Z_N$, range 为$B_{n-1}$.

**Claim: **$\chi = \sum_{k}(-1)^k \beta_k$.

> $\beta$ is the betti number.



## Cohomology

![image-20240510164434598](./../../../../../../code/Markdown/images/image-20240510164434598.png)

![image-20240510164529303](./../../../../../../code/Markdown/images/image-20240510164529303.png)

> co-chain 和 chain 做内积得到数.

![image-20240510164711531](./../../../../../../code/Markdown/images/image-20240510164711531.png)

> 注意dual space中lattice的中心为原来space的一个vertex.

![image-20240510164845542](./../../../../../../code/Markdown/images/image-20240510164845542.png)

> 注意算内积的时候都是modulo 2.

![image-20240510164939797](./../../../../../../code/Markdown/images/image-20240510164939797.png)

> 最后一行写错了, 应该想说的是$C_n$表示n-chain, 而$C^n$表示n-cochian.

![image-20240510165155477](./../../../../../../code/Markdown/images/image-20240510165155477.png)

### Cohomology Groups

$$
\widetilde{\partial}^n: &\text{n-coboundary map.}\\
Z^n: &\text{the group of cocycles(kernel).}\\
B^n: &\text{the image of coboundaries(iamge/range).}\\
H^n = \frac{Z^n}{B^n} & \text{nth cohomology group.}\\
Betti\ numbers\ \beta^n: &\text{rank of the nth cohomology group.}
$$

