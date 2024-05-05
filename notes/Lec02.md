# Toric Code

## Introduction

Toric code is the simplest example of a topological code.

<img src="./../../../../../../code/Markdown/images/image-20240505225535799.png" alt="image-20240505225535799" style="zoom: 67%;" />

> These two loops are called none-trivial loop, because they can not be deformed into a point or to each other.

## Physical Qubits

<img src="./../../../../../../code/Markdown/images/image-20240505225850921.png" alt="image-20240505225850921" style="zoom:67%;" />

+ of edges $L^2+L^2 = 2L^2$.
+ Each edge correspond to a physical qubit.
+ of physical qubits $2L^2$.

## Stabilizer Generator

| ![image-20240505230117776](./../../../../../../code/Markdown/images/image-20240505230117776.png) | ![image-20240505230125680](./../../../../../../code/Markdown/images/image-20240505230125680.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

+ Plaquette Operator = $ \underset{S\in P}{\otimes} Z_s$.

+ Vertex Operator = $\underset{S\in V}{\otimes} X_v$.

+ Plaquette and Vertex operators commute.

  > If two operator dose not overlap, then they are surely commute.
  >
  > If they overlap, the overlapping qubits will be exactly two, and since $XZ = ZX$, they are commute.

## Multiplication of Plaquette Operators

<img src="./../../../../../../code/Markdown/images/image-20240505231020678.png" alt="image-20240505231020678"  />

> 几个块状算子的张量积即为他们边界上的一圈$Z$的张量积, 因为被share 的边界两个$Z$抵消, $ZZ= I$.

**Claim:** Independent Generators $L^2-1$.

> Since $\underset{\alpha}{\prod P_{\alpha}} = I$.

## Dual Lattice

![image-20240505231547947](./../../../../../../code/Markdown/images/image-20240505231547947.png)

> 这里感觉和线代学的对偶空间有点联系, 但是没有看得特别明白, 但大致意思应该是说分析plaquette算子, 相当于在对偶空间分析vertex算子, 所以前面说的那些plaquette的性质应当对于vertex也成立.

## Encoded Qubits

The encoded qubits of toric code is ==2==.

+ We have total $2L^2$ physical qubits, which means $n = 2L^2$.

+ We have total $2(L^2-1)$ generators, which means $m = 2(L^2-1)$.
+ Since $k = n-m$, we encoded totally 2 qubits.

## Encoded Logical Operators

Recall that the requirements for the encoded logical operators:

+ Must commute with all elements of the stabilizer group.
+ Must not be an element of the stabilizer group.
+ Must satisfy the communication and anti-communication relation of the Pauli operators they encode.

Now let`s try to construct a $Z$ operator:

> 首先我们考虑能否使一个封闭的二维图形? 不行, 因为封闭的二维图形必定由一些Plaquette组成, 所以其属于Stabilizer Group.
>
> 所以下面我们考虑string, 即一维的线性结构.

![image-20240505232630923](./../../../../../../code/Markdown/images/image-20240505232630923.png)

> $XZ = -ZX$

<img src="./../../../../../../code/Markdown/images/image-20240505233026189.png" alt="image-20240505233026189" style="zoom:50%;" />

> 这就是我们最终构造出来的$Z$ 和 $X$, 其实他们也不一定要是一条笔直的线, 可以有一些zigzag, 但只要保证是loop即可.
>
> 另外, 水平和竖直的环恰好对应了本篇笔记开头的那两个none-trivial的环.

## Equivalent of Logical Operators under Stabilizer Multiplication.

![image-20240505233315870](./../../../../../../code/Markdown/images/image-20240505233315870.png)

> 正如Lec01所讲的那样, 一个算子乘上一些列的stabilizer 都与原来等效.

## Code Distance

+ Minimum weight of any logical operator in the code.
+ 可以看到我们的logical operator最短应当为水平和竖直方向笔直的直线(环), 因为zigzag只会增加weight.
+ Thus, $ d = L$.
+ $[[n = 2L^2,\ k = 2,\ d = L]]$.

 ## Error Correction via Toric Code

Recall that:

+ We can detect errors on stabilizer codes by measuring the stabilizer generators.
+ Syndrome: outcome of the measurement of a given stabilizer generator.
+ When error $E$ happens, the stabilizer generators that don`t commute with $E$ will output $-1$.

![image-20240505234043393](./../../../../../../code/Markdown/images/image-20240505234043393.png)

![image-20240505234121286](./../../../../../../code/Markdown/images/image-20240505234121286.png)

![image-20240505234253504](./../../../../../../code/Markdown/images/image-20240505234253504.png)

> 像图三这样, 如果有两次犯错他们的路径构成了一个环, 他们形成了一个stabilizer, 相当于负负得正, 自我修复了.

**The Toric Code Hamiltonian**

<img src="./../../../../../../code/Markdown/images/image-20240505234554805.png" alt="image-20240505234554805" style="zoom:67%;" />

> There are actually four kinds of ground states for toric code, which make sense because $2^k = 2^2 = 4$, the size of the logical qubits space is 4.