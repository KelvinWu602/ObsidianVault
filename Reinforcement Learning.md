>[!Tip] What kinds of problems does it solve?
>Reinforcement learning can solve sequential decision problems, which can be modeled as a [[Markov Decision Process| MDP]], where the solution to this problem would be an optimal policy $\pi^*$.


# Value function

There are two kinds of value function:
- [[State-value function]]
- [[Action-value function]]
The action-value function is more useful for unknown MDP problems. 

# Optimal Value Function

## Optimal state-value function
$$\forall s, v_*(s) = \max_\pi v_\pi(s)$$
Find a policy such that it can yield the highest expected return no matter starting at which state, the optimal state-value function describe the expected return of such policy.

## Optimal action-value function
$$\forall (s,a), q_*(s,a) = \max_\pi q_\pi(s,a)$$
Find a policy such that it can yield the highest expected return no matter starting at which state and action. The optimal action-value function describe the expected return of such policy.

# Optimal Policy

First, a policy can be fully described with a 2D matrix.

| $\pi$     | $a_1$    | $a_2$ |     
| ----- | -------- | ----- |
| $s_1$ | 0.5 | 0.5 |
| $s_2$ | 0.6| 0.4 |

Consider two policy, $\pi_1, \pi_2$, 
- if we have $v_{\pi_1}(s_1)>v_{\pi_2}(s_1)$:
	Then the row corresponding to $s_1$ of policy $\pi_1$ is preferred.
- if we have $v_{\pi_1}(s_2)<v_{\pi_2}(s_2)$:
	Then the row corresponding to $s_2$ of policy $\pi_2$ is preferred.

Then if we combine the $s_1$ row of $\pi_1$ and $s_2$ row of $\pi_2$, we can get $\pi_3$, which is better than both $\pi_1$ and $\pi_2$.

According to the [[State-value function#Matrix Form|derivation]], we know that there is a value upperbound for the optimal policy, that is once we have found that
$$v_\pi(s_i) = v_*(s_i)$$
Then we fix the $s_i$ corresponding row of $\pi$, and continue to improve other rows. At the end, we will come up with an optimal policy such that 
$$\forall i, v_\pi(s_i) = v_*(s_i)$$
Then we claim this policy is the *optimal policy*, $\pi^*$.

>[!Note] Properties of Optimal Policies
>1. There exists one or more than one optimal policies.
>2. They all can achieve the optimal state-value function.
>3. They all can achieve the optimal aciton-value function.
- How to prove the 3rd point?


Mobile test