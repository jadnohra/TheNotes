<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Summary
It is possible to create an interesting notation based on Bayes rule that helps with simple derivations, such as [Chapter-1](https://colab.research.google.com/github/AllenDowney/ThinkBayes2/blob/master/notebooks/chap01.ipynb) and [Chapter-2](https://colab.research.google.com/github/AllenDowney/ThinkBayes2/blob/master/notebooks/chap02.ipynb) exercise in the free book ['Think Bayes 2'](https://allendowney.github.io/ThinkBayes2/).

# Notation
  - Probabilistic terms always use an outer parentheses expression followed by a square bracket expression, like so: $$(A + B)[C]$$
    - The parentheses contain terms made up of random variables
    - The square brackets contain the subset of the full universe $$\mathcal{U}$$ within which the random variable expression takes place. This creates a homogenous explicit notation replacing the 'A given B' notation. Examples follow.
  - A probability such as $$P(A)$$ is written as $$A[\mathcal{U}]$$. 
  - A probability such as $$P(A \vert B)$$ is then written as $$A[B]$$.
  - A probability such as $$P(A.B \vert C)$$ is then written as $$(A . B)[C]$$.
  - A probability such as $$P(A.B \vert C+D)$$ is then written as $$(A . B)[C + D]$$.
 
# Rules
  1. Within parentheses, the normal rules of probability apply. For example 
   
   $$(A . (B + C))[D] =  (A . B + A . C)[D]$$
  
  2. The rule of conditional probability becomes the device for moving terms between parentheses and square brackets. 
  
  $$ A[B] . B[C] = (A . B)[C] $$

Rule 2 is the key that makes the notation useful, producing this easy to remember **'Change of Bayesis'** (not a typo) form. 
Due to rule 2, this notation only works in the case of independent variables. 

# Similarities

Does $$ A[B] . B[C] = (A . B)[C] $$ seem familiar? Yes it does!

* In Calculus, the chain rule, which is a 'change of variable' or 'change of basis' rule is in Leibniz notation by $$\frac{dx}{dz} = \frac{dx}{dy} \frac{dy}{dz}$$
* In Linear Algebra, the change of basis is in [robotics notation](https://www.cs.columbia.edu/~allen/F17/NOTES/frames2.pdf) given by $$v^B = T^A_B v^a$$

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
