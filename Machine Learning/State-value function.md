#reinforcement-learning 

>[!NOTE] Definition
>$$v_{\pi}(s) = \mathbb{E}_{\pi}[G_t | S_t = s]$$

We can see how this idea emerged from comparing policies by [[Markov Decision Process#Return|Expected Return]].

# Computation

Normally, we need to simulate the game infinitely many times, and average out all the return samples, then get the expected return. This is obviously impractical.

1. What if the game never terminates?
2. How many times do we need to simulate the game?

Therefore, we need some clever way to turn this into a solvable problem in finite time. This introduces us the Bellman Expectation Equation.

## Bellman Expectation Equation

$$v_\pi(s) = \mathbb{E}\pi[G_t|S_t=s] = \mathbb{E}\pi[r+\gamma v_\pi(s') | S_t = s]$$

See the [[Bellman Expectation Equation|derivation]].

# Matrix Form

Consider $v_\pi(s_1)$, we have
$$v_\pi(s_1) = \mathbb{E}\pi[r+\gamma v_\pi(s') | S_t = s_1]$$
The expectation is average over the space of $S_{t+1}$ and $a$, so we can write it as:
$$v_\pi(s_1) = \sum_{s',r} \sum_a(r+\gamma v_\pi(s'))P(s',r|s_1,a)\pi(a|s_1)$$
Rearranging the terms:
$$v_\pi(s_1) = \sum_{s',r} (r+\gamma v_\pi(s'))\left[ \sum_a P(s',r|s_1,a)\pi(a|s_1)\right]$$
We can define that:
$$P^\pi_{s_1s'} = \sum_a P(s',r|s_1,a) \pi(a|s_1)$$
Which can be interpreted as *given $s_1$, the probability of moving to $s'$, following policy $\pi$*. With this transitional probability defined, we can express $v_\pi(s_1)$ in matrix form.

Then we can also define
$$R^\pi_1 = \sum_{s',r} r P^\pi_{s_1s'}$$
Which can be interpreted as *given $s_1$, the expected reward that will be received in the very next move, following policy $\pi$*.

Then we can simplify the Bellman Expectation Equation:
$$v_\pi(1) = R^\pi_1 + \gamma 
\begin{bmatrix} 
P^\pi_{11} & \cdots & P^\pi_{1n}
\end{bmatrix} 
\begin{bmatrix}
v_\pi(1) \\
\vdots \\
v_\pi(n) 
\end{bmatrix}
$$
- Current state $S_t = 1$, next state $S_{t+1} \in [1,n]$

This can be generalized to any current state:

$$
\begin{bmatrix}
v_\pi(1) \\
\vdots \\
v_\pi(n)
\end{bmatrix}
= 
\begin{bmatrix}
R^\pi_1 \\
\vdots\\
R^\pi_n
\end{bmatrix}
+ \gamma 
\begin{bmatrix} 
P^\pi_{11} & \cdots & P^\pi_{1n}
\end{bmatrix} 
\begin{bmatrix}
v_\pi(1) \\
\vdots \\
v_\pi(n) 
\end{bmatrix}
$$
Or in compact form
$$v_\pi = R^\pi + \gamma P^\pi v_\pi$$
Then we can solve for stationary value function:
$$(I - \gamma P^\pi) v_\pi = R^\pi$$
$$ v_\pi = (I - \gamma P^\pi)^{-1}R^\pi$$
- $v_\pi$ is unique, thus for each policy, the expected return is unique
- $P^\pi$ is a contraction matrix, and the inverse always exists

