# Skiplists

1. Number of nodes per level
  **a.** What is the probability that the first node reaches level *i*  or higher.
  $P(X >= i)$ can be expressed as a binomial distribution with $i$ trials. In our case, where $P(Success) = 0.5$, we get the distribution $B$~$X(i,0.5)$
  $$
  P(X >= i) = P(X=i) = {{i}\choose{i}} \cdot 0.5^i \cdot 0.5^{i-i} = 1\cdot0.5^i\cdot1 = 0.5^i
  $$
  **b.** If one knows that $k$ nodes have reached level $i$, in how many ways can one choose these nodes?
  Given that we have $n$ nodes, there are ${{n}\choose{k}}$ ways that there can be $k$ nodes that has reached level $i$.
  **c.** What is the probabilty that there are exacklt _k_ nodes at level _i_, where $k = 0,1,...,n$ and $i = 0,1...$, if one does not count the ending nodes with $-\infty{}$ and $\infty$?
  The problem can be expressed as a binomial distribution $X$~$B(i,p)$ where $p$ is the probability that a node reaches level $i$ or higher. As determined in _a)_, $p = 0.5^i$. I.e, the probabilty is
  $$
  P(\text{k nodes at level i}) = P(X = i) = {{i}\choose{i}} \cdot (0.5^i)^i \cdot (1-0.5^i)^{i-i} = 1 \cdot 0.5^{i^2} \cdot 1 = 0.5^{i^2}
  $$
2. Worst case
    a. What is the probability that the first number reaches level $i$ but not higher?
    Given that the probability to reach $i$ and higher is (as determined in 1a) $P(i)=0.5^i$, the probability to reach *exactly* level $i$ is $P(i)-P(i+1) = 0.5^i-0.5^{i+1}$
    b. What is the probability that all the $n$ nodes reach level $i$ but not level $i+1$, for $i=0,1,...,?$
    $A_1$="a node reaches level $i$", $A_2$="all nodes reach level $i$", $B$="all nodes reach exactly level $i$"
    $P(A_1)=0.5^i$
    $P(A_2)=(P(A_1))^n$
    $P(B)=P(A_1)-P(A_2)$
