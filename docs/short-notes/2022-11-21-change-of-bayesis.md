<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

It is possible to create an interesting notation based on Bayes rule that helps with simple derivations, such as [Chapter-2 exercises](https://colab.research.google.com/github/AllenDowney/ThinkBayes2/blob/master/notebooks/chap02.ipynb) from the excellent free book ['Think Bayes 2'](https://allendowney.github.io/ThinkBayes2/).

The notation was born out of the following observations:
  - We move a lot between probabilistic subspaces and that's key. For example by $$P(A)$$ we mean the probability of $$A$$ in the 'Universe' $$\mathcal{U}$$, while by $$P(A\|B)$$ we mean the proability of $$A$$ in the subspace $$B$$. Why not then make the indication 'Basis' space explicit and homogeneous?
  - In the traditional notation, we confound the multiplication and addition operators to operate both on scalars and random variables. It would be a bit clearer for beginners if we did not.

# The notation
  - We use $$.$$ and $$+$$ for scalar operations
  - We use $$\land$$ and $$\lor$$ for random variable operations
  - A probability such as $$P(A)$$ is instead written as $$A[\mathcal{U}]$$. 
  - A probability such as $$P(A \| B)$$ is then written as $$A[B]$$.
  - A probability such as $$P(A.B \| C)$$ is then written as $$(A \land B)[C]$$.
  - A probability such as $$P(A.B \| C+D)$$ is then written as $$(A \land B)[C \lor D]$$.
 
# The rules:
  1. Within parentheses, the normal rules of probability apply. For example $$(A \land (B + C))[D] =  (A \land B + A \land C)[D]$$
  2. The rule of conditional probability becomes the device for moving terms between parentheses and square brackets. It is the key that makes the notation useful. It gets this easy to remember 'Change of Bayesis (pun intended)' form:
  
  $$ A[B] . B[C] = (A \land B)[C] $$

Due to rule 2, this notation only works in the case of independent variables. 

# Applications

These applications are inspired by the exercises mentioned in the book chapter at the top.

## Deriving Bayes Theorem

$$\begin{align*} 
&(A \land B)[C] = (B \land A)[C] = A[B] . B[C] = B[A] . A[C] 
\\ &\implies A[B] = \frac{B[A] . A[C]}{B[C]}
\end{align*}$$

That's Bayes Theorem. To recover the traditional form, we set $$C$$ to $$\mathcal{U}$$. 

Due to this, rule 2 expressed in this notation is [yet another way to remember](short-notes/2022-04-01-remember-bayes.md) Bayes theorem, by 'Change of Bayesis'.

## Deriving A Basic Formula for Total Probability

Given independent subspaces $$B_i$$ which together cover $$\mathcal{U}$$, we have

$$\begin{aligned} 
A[\mathcal{U}] 
\\ &= (A \land \mathcal{U})[\mathcal{U}] 
\\ &= (A \land \sum_i{B_i} )[\mathcal{U}] 
\\ &= (\sum_i{A \land B_i} )[\mathcal{U}] 
\\ &= \sum_i{(A \land B_i)[\mathcal{U}]}
\\ &= \sum_i{(A[B_i] \land B_i[\mathcal{U}]})
\end{aligned}$$
