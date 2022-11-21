It is possible to create an interesting notation based on Bayes rule that helps with simple derivations, such as [Chapter-2 exercises](https://colab.research.google.com/github/AllenDowney/ThinkBayes2/blob/master/notebooks/chap02.ipynb) from the excellent free book ['Think Bayes 2'](https://allendowney.github.io/ThinkBayes2/).

The notation was born out of the following observations:
- A lot of basic Bayesian manipulations are in essense about doing normal probability calculations, but in subspaces of the probabilistic universe in question. For example by $P(A)$ we mean the probability of $A$ in the 'Universe' $\mathcal{U}$, while by $P(A|B)$ we mean the proability of $A$ in the subspace $B$. Why not then make the 'Basis' space explicit in all cases.
- In the traditional notation, we confound the multiplication and addition operators to operate both on scalars and random variables. It would be a bit clearer for beginners if we did not.

# The notation
 - We use $.$ and $+$ for scalar operations
 - We use $\\&$ and $\lor$ for random variable operations
 - A probability such as $P(A)$ is instead written as $A[\mathcal{U}]$. 
 - A probability such as $P(A | B)$ is then written as $A[B]$.
 - A probability such as $P(A.B | C)$ is then written as $(A \\& B)[C]$.
 - A probability such as $P(A.B | C+D)$ is then written as $(A \\& B)[C \lor D]$.
 
# The rules:
 1. Within parentheses, the normal rules of probability apply. For example $(A \\& (B + C))[D] =  (A \\& B + A \\&C)[D]$
 2. The rule of conditional probability becomes the device for moving terms between parentheses and square brackets. It is the key that makes the notation useful. It gets this easy to remember 'Change of Bayesis (pun intended)' form: $$A[B] . B[C] = (A \\& B)[C]$$

Due to rule 2, this notation only works in the case of independent variables. 

# Applications

These applications are inspired by the exercises mentioned in the book chapter at the top.

## Deriving Bayes Theorem

$$\begin{align*} 
(A \\& B)[C] = (B \\& A)[C] = A[B] . B[C] = B[A] . A[C] 
\\ \implies A[B] = \frac{B[A] . A[C]}{B[C]}
\end{align*}$$

That's Bayes Theorem. To recover the traditional form, we set $C$ to $\mathcal{U}$. 

Due to this, rule 2 expressed in this notation is [yet another way to remember](short-notes/2022-04-01-remember-bayes.md) Bayes theorem, by 'Change of Bayesis'.

## Deriving A Basic Formula for Total Probability

Given independent subspaces $B_i$ which together cover $\mathcal{U}$, we have

$$\begin{align*} 
A[\mathcal{U}] 
\\ = (A \\& \mathcal{U})[\mathcal{U}] 
\\ = (A \\& \sum_i{B_i} )[\mathcal{U}] 
\\ = (\sum_i{A \\& B_i} )[\mathcal{U}] 
\\ = \sum_i{(A \\& B_i)[\mathcal{U}]}
\\ = \sum_i{(A[B_i] \\& B_i[\mathcal{U}]})
\end{align*}$$
