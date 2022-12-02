# 5 components:
1. States: a full description of your environment
2. Actions: all the possible actions that the player can take given the current state
3. Transition Probabilities: describe the possible next state, given current state and action taken
4. Reward function: given current state and action, the expected reward based on transition probabilities
5. Discount factor: discount in rewards from the future

We usually write a MDP as $(S,A,P,R,\gamma)$
$P_{ss'}^a$  probability of moving from $s$ to $s'$ given that action $a$ was taken
$R_{s}^a$   expected value of reward received on the *NEXT* state $s'$.
$\gamma \in [0,1]$ 

# How is it Markov?

Consider the transition probability for some current state $s$ and action $a$
$$P(S_{t+1} = s' | S_{t} = s , A_{t}=a)$$ ^4816ff

We can make it independent of $a$,

$$P(S_{t+1}=s'|S_{t}=s) = \sum_{a\in A} P(S_{t+1} = s' | S_{t} = s , A_{t}=a)P(A_{t}=a | S_{t}=s)$$
- Note that $P(A_t=a | S_t=s)$ is described by the policy $\pi(a|s)$

The reason why this is Markov, is because the current state has already contained all past information, that is:
$$P(S_{t+1} | S_t) = P(S_{t+1}|S_1 ... S_t)$$

# Objective and Solution

## Return

$R_t$ is a single reward that the agent would receive on an active. However, local optimum action does not mean global optimum action, otherwise the agent is simply using Greedy Algorithm.

>[!Tip] Key
>What is important is the total, overall gain. We call this **Return** $G$.

![[Pasted image 20221202192329.png]]

>[!question] Why do we need $\gamma$ ?
>- What if $\gamma = 1$? 
>- What if $\gamma = 0$?
>- What if $\gamma > 1$?


>[!Tip] The Optimal Policy $\pi^*$
The optimal solution to a MDP is therefore the policy that can yield the highest return. 

But what does the highest return means? Since $R_t$ is random, so as $G_t$. For each episode, we may obtain different value of $G_t$ even with the same policy $\pi$, due to the stochastic state transition.

Therefore it is not fair to compair two policies with 1 return sample, what we should compare is the expected return for each policy. If we assume the initial state is always the same, then we should compare:
$$\mathbb{E}_{\pi} [G_t | S_t = s]$$
- $\pi$ is the policy under evaluation
- $s$ is the initial state

This value, is also called the [[State-value function|state-value function]].

# A few jargons

>[!Tip] Partially observable Markov Decision Process
>In normal MDP, all states are fully observable. But when some states are not fully observable, we call them **POMDP**.

>[!Tip] Episodic
> Used to describe a MDP that always terminates.

>[!Tip] Stationary Policy
>It means the action probabilities at each state depends **ONLY** on the state, not time.

>[!Tip] Deterministic Policy
>Given current state, one can be sure with which action to be taken.
>

