Markov Chains - A mathematical system that undergoes transitions from one state to another according to certain probalistic rules. Note that a key feature is the probability of transiting to any particular state depends on <u>only the current state. NOT preceeding states.</u>

Here:
$'/{X_k,k\epsilon\mathbb{N}/}'$
Where $'X_k'$ is the state of the process at time <i>k</i>
and <i>k</i> is a part of all integers

From here, we can make a markov chain

$'Pr(X_(k+1)=j\mid X_k=i)'$ <- This means probability of the next state equalling j given that the current state equals i, this is independant of any previous state.

We can make a matrix of i (the current state) and j (the next state) states, with each part of the matrix showing the probability of the next state based on the current state $'P_(ij)'$.


Note the Current State of the matrix are the rows
Note the Next State of the Matirx are the columns

$$ P = \begin{pmatrix}
P_11 & P_12 & P_13 \\
P_21 & P_22 & P_23 \\
P_31 & P_32 & P_33
\end{pmatrix}
$$

The rows of the matrix must equal to 1 (hence, the matrix is <i>row stochaitic</i>)
 $$ P_11 + P_12 + P_13 = 1$$




