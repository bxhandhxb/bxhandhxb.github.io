---
layout: post
title: PGM notes2
date: 2019-02-07 11:05:24.000000000 +09:00
---
PGM自然地把data、inference、learning结合起来，公用相同的loss。  what you predict is exactly what you learn from data。

PGM是一种语言，帮助建立复杂的数学模型，否则要用繁琐的公式去写；一个PGM对应一套条件独立性和独立性的假设

> A more formal description:

It refers to a family of distributions on a set of random variables that are compatible with all the probabilistic independence propositions encoded by a graph that connects these variables

> A informal blurb:

It is a smart way to write/specify/compose/design exponentially-large probability distributions without paying an exponential cost, and at the same time endow the distributions with structured semantics

Directed edges give causality relationships (Bayesian Network or Directed Graphical Model)

Undirected edges simply give correlations between variables (Markov Random Field or Undirected Graphical model)

> why gms

概率论提供了部件组合的粘合剂，确保整个系统是一致的，并提供了将模型与数据接口的方法。

图形理论模型提供了一个极具吸引力的界面，人类可以通过该界面模拟高度互动的变量集以及一个自然适用于高效通用算法设计的数据结构。

在统计学，系统工程，信息论，模式识别和统计力学等领域研究的许多经典多变量概率系统都是一般图形模型形式主义的特例。

PGM框架提供了将这些系统视为共同的基础形式主义的实例。

PGM 是tradeoff between richness of representation and economy in presentation cost

A family of full graphs 

A family of limited graphs

A family of completely independenct graphs

PGM 帮助把指数级运算降低到多项式级运算。定性规范是把你大专业知识喂给模型。

> 三个基础的block    

. common parent

Fixing B decouples A and C

. Cascade

Knowing B decouples A and C

. V-structure

Knowing C couples A and B because A can "explain away" B w.r.t. C 

这种V型结构是把两个独立的event联系起来的一种方式。

I(G) belongs to I(P)

I(P)是分布P包含的所有独立性断言。 那么I(G)是我们关心的独立性断言，G被称为P的I-map. I-map方便了我们去可视化独立性。

//I可以是空集。I(G)是安全的，不会过度陈述。

> directed separation 用图论的方法判断条件独立和边缘独立。 D-separated == conditionally independent

Then we follow this procedure:

1. Draw the ancestral graph.
Construct the “ancestral graph” of all variables mentioned in the probability expression. This is a reduced version of the original net, consisting only of the variables mentioned and all of their ancestors (parents, parents’ parents, etc.)

2. “Moralize” the ancestral graph by “marrying” the parents.
For each pair of variables with a common child, draw an undirected edge (line) between them. (If a variable has more than two parents, draw lines between every pair of parents.)

3. "Disorient" the graph by replacing the directed edges (arrows) with undirected edges (lines).

4. Delete the givens and their edges.
If the independence question had any given variables, erase those variables from the graph and erase all of their connections, too. Note that “given variables” as used here refers to the question “Are A and B conditionally independent, given D and F?”, not the equation “P(A|BDF) =? P(A|DF)”, and thus does not include B.

5. Read the answer off the graph.

- If the variables are disconnected in this graph, they are guaranteed to be independent.

- If the variables are connected in this graph, they are not guaranteed to be independent.

- Note that “are connected” means “have a path between them,” so if we have a path X-Y-Z,
X and Z are considered to be connected, even if there’s no edge between them.

- If one or both of the variables are missing (because they were givens, and were
therefore deleted), they are independent.

> active trail : //个人理解，此处的active即为dependent

 Let X, Y , Z be three sets of nodes in G. We say that X and Y are d-separated given Z, if there is no active trail between any node x belongs to X and y belongs to Y given Z.







