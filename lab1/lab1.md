# Skiplists

1. Number of nodes per level
  **a.** What is the probability that the first node reaches level *i*  or higher?
  $P(X >= i)$ can be expressed as a binomial distribution with $i$ trials. In our case, where $P(Success) = 0.5$, we get the distribution $B$~$X(i,0.5)$
  $$
  P(X >= i) = P(X=i) = {{i}\choose{i}} \cdot 0.5^i \cdot 0.5^{i-i} = 1\cdot0.5^i\cdot1 = 0.5^i
  $$
  **b.** If one knows that $k$ nodes have reached level $i$, in how many ways can one choose these nodes?
  Given that we have $n$ nodes, there are ${{n}\choose{k}}$ ways that there can be $k$ nodes that has reached level $i$.
  **c.** What is the probability that there are exactly _k_ nodes at level _i_, where $k = 0,1,...,n$ and $i = 0,1...$, if one does not count the ending nodes with $-\infty{}$ and $\infty$?
  The problem can be expressed as a binomial distribution with $n$ (the number of nodes) trials and $P(Success) = 0.5^i$ for a trial or node to reach level $i$, as determined in 1a, i.e. $X$~$B(n,0.5^i)$
  $$
  P(X=k) = {{n}\choose{k}} \cdot 0.5^{i^k} \cdot (1-0.5^i)^{n-k}
  $$
2. Worst case
    **a.** What is the probability that the first number reaches level $i$ but not higher?
    Given that the probability to reach $i$ and higher is (as determined in 1a) $P(i)=0.5^i$, the probability to reach *exactly* level $i$ is $P(i)-P(i+1) = 0.5^i-0.5^{i+1}$
    **b.** What is the probability that all the $n$ nodes reach level $i$ but not level $i+1$, for $i=0,1,...,?$
    We informally define a few events, such that $A_1(i)$="a node reaches level $i$", $A_2(i)$="all nodes reach level $i$", $B(i)$="all nodes reach exactly level $i$".
    $P(A_1(i))=0.5^i$
    $P(A_2(i))=P(A_1(i))^n$ where $n$ is the number of nodes
    $P(B(i))=P(A_2(i))-P(A_2(i+1))=0.5^{i^n}-0.5^{(i+1)^n}$
    **c.** What is the probability that all nodes reach the same level? Simplify the expression as much as possible.
    Given that $B(i)$ is defined as "all nodes reach exactly level $i$", we can use it to  express the probability of this happening at any level. $B(i)$ and $B(i+1)$ are independent which means that we can sum the probability of all levels with
    $$
    P(B(0)\cup B(1)\cup ...\cup B(n)) = P(B(0))+P(B(1))+...+P(B(n))
    $$
    $$
    \sum_{k=0}^\infty P(B(k))
    $$
3. Memory space
    **a.** Let $X$ denote the number of nodes at level $i$. In point 1 you have computed the probability that $X = k$. What is the distribution of the random variable $X$ and why? What are the parameters of the distribution?
    The distribution of $X$ is $f(x,n,i)$ where $x$ is the number of nodes out of $n$ nodes that reached level $i$ or higher. The parameters $n$ and $i$ are necessary as the distribution is based on a binomial distribution as seen in 1c. **PARANOIA NOTE**
    **b.**
    What is the expected value if nodes at level $i$ for $i=0,1,2,...$,without counting the ending nodes?
    The expected value $\mathbb{E}$ for a binomial distribution $X$~$B(n,p)$ is $\mathbb{E} = np$.
