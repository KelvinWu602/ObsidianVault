# Introduction

Over the history, different forms of government existed and greatly affected the living standard of people. Started from the French Revolution, democratic movement had spread to the entire global, symbolling a new era of civilization. That said, we can still see numerous autocratic states in current world. How are these autocratic leaderships still exist today? Why do people living under those regimes are generally having poorer living quality than people living in free states? 

# Literature Review

There were some studies on this topic already, including the work by John Ginkel and Alastair Smith in 1999. That literature formulated a game theoretic model to explain why governments rarely offer concessions to protesters, dissident activity is more likely to be successful in motivating large-scale protest under highly repressive conditions, and why regimes collapse suddenly with little warning. 

In this article, I focused on a set of different questions mainly around the succession of an autocratic state, and the interaction between the ruling class, military power, and the people.

# Formalization of the strategic environment

We can identify three major groups of player in an autocratic state: the people, the ruling class, and the military.

In most of the autocratic countries, people are usually unarmed, thus having the weakest bargaining power, yet being able to control the economic output of the entire state by strike and continuously protest. 

The ruling class are unarmed as well, yet they have political power and being able to determine the distribution of wealth. 

The military is the only armed group. They do not have direct access to the national wealth and therefore relying on the ruling class to offer them privilege.

## Simplification of the situation 

Let $t$ be the time index, or the stage of the game. Let $R_t$ be the resource of the whole society at time $t$, and let $P_t = (p_{1_t}, p_{2_t}, p_{3_t})$ be the proposal of resource distribution at any time $t$.

Label the three group of players, namely, the people, the ruling class, and the military by $A,B,C$ respectively.

By default, $B$ will make a proposal, and $A,C$ will decide whether to accept or not. Of cource different individuals in the group has different level of acceptance, but for simplicity, here I assume all people in the same group will share the same utility, strategy and action.

Then, $A, C$ will make decision independently and simultaneously, on whether to accept this proposal, or to deny this proposal (That is, to overthrow the ruling class). 

This forms a simultaneous game in the middle of the repeated bargaining game:

 ![[Pasted image 20221214173538.png]]

- If both $A$ and $C$ accepts, then the society is in peace. $B$ maintains his rule and propose the next proposal.
- If $A$ accepts but $C$ denies, it's a military coup, $B$ is immediately overthrown, and $C$ can propose the next proposal.
- If $A$ denies but $C$ accepts, the military will help $B$ to suppress the people, and $B$ can continue to propose the next proposal.
- If $A$ and $C$ denies, $B$ is overthrown, and the power will belong to $C$ as they have guns, they are going to propose the next proposal.

Notice that, once $B$ is overthrown, he receives a payoff zero and kicked out of the game forever.

Also notice that, no matter $A$ chooses to accept of fight, they still have the same outcomes. Therefore we can simplify the game as the following:

![[Pasted image 20221214180254.png]]
- Under the left branch, $B$ will continue to rule the state and determine the distribution of wealth. 
- Under the right branch, $B$ is overthrown and $C$ rule a military state, it becomes a 2 person repeated game.

# Analysis of the game

Due to its complexity, a full solution is not given (I doubt its existence), however, we can still gain some real world insight from this model.

## Military state
First focus on the right branch, that is after the overthrown of the original government, how would the military state and the people interact, which is a well defined subgame.

This is different from the bargaining game we saw in the lecture, as here the players can collect payoff **at every stage**.

Assume a stationary equilibrium exists, that is both players are playing the same strategy at every decision node.

For $C$, assume they propose a fixed percentage of total resource:
$$\text{Proposal} = (xR_t, (1-x)R_t)$$
Then his payoff at each timestamp is $xR_t$, considering the discount factor $\delta$, his payoff will be:
$$\text{C's payoff} = xR_t + \delta xR_{t+1} + \delta^2 x R_{t+2} + \cdots$$
$$P_C=x (R_t + \delta R_{t+1} + \delta^2 R_{t+2} + \cdots)$$

For $A$, their strategy $f(x)$ is a mapping from $(1-x)R_t$ to $R_{t+1}$. Intuitively, the more resource the people are getting, the more resource they are generating in the near future (education, investment, etc.), thus the assumption that $f(x)$ is a strictly increasing function. 

Then we can express C's payoff as the following: 
$$R_{t+1} = f((1-x)R_t)$$
$$R_{t+2} = f((1-x)R_{t+1})$$
$$P_C = x(R_t + \delta f((1-x)R_{t})+ \delta^2 f((1-x)f((1-x)R_t)) + \cdots)$$

Assume $f(x) = x$ for simplicity then
$$P_C= x(R_t + \delta (1-x)R_{t}+ \delta^2 (1-x)^2R_t) + \cdots)$$
$$= x R_t(1 + \delta (1-x) + (\delta (1-x))^2 + \cdots)$$
$$= x \frac{R_t}{1-\delta (1-x)} = P_C$$
To maximise this payoff, 
$$\frac{d P_C}{dx} = \frac{R_t}{1-\delta(1-x)} - x\frac{\delta R_t}{(1-\delta(1-x))^2}=0$$
$$\frac{R_t}{1-\delta(1-x)} = x\frac{\delta R_t}{(1-\delta(1-x))^2}$$
$$1-\delta(1-x) = x\delta $$
$$1=\delta$$
which is a contradiction, that means there does not exist $x$ that can maximise the payoff of this function. However we can consider the boundary cases that is when $x=1$.

![[Pasted image 20221214190828.png]]
C's payoff when $R_t =1,\delta = 0.9$.

Thus, this is an take-all equilibrium. Given that the people are playing strategy $f(x)=x$, the ruling class will simply take all wealth of the society and leave this country.

On the other hand, given that the government will take all resources, there is no incentive for people to change their strategy. Producing more even the payoff is zero is stupid. 

This coincides with the fact that most of the military states are poor, such as Myanmar, Afghanistan, etc. 

In reality, the government has the freedom to give their people some degree of resources, in order to achieve longer term interest.


## Peace or civil war?

The ruling class $B$ is clear about the importance of the support from the military, being overthrown at any round is strictly worse than continuing their regime. In reality, it can mean death. 

Therefore, $B$ will try his best to keep $C$ happy. That is to offer $C$ more than the maximum payoff $C$ can get if $C$ chooses to fight, let it be $\bar{P_C}$.

The exact amount of $\bar{P_C}$ depends on both $A,C$ strategies. However, it must be bounded, otherwise any dictator $B$ could not exist.

So in $B$'s proposal, he will distribute $R_t = (p_t, R_t-\bar{P_C}-p_t ,\bar{P_C})$.
Notice that $R_t-\bar{P_C}-p_t$ can affects $R_{t+1}$. 

Assume the people still adopts $f(x)=x$, then we have $R_{t+1} = R_t-\bar{P_C} - p_t$. $B$ must have $R_{t+1} \ge \bar{P_C}$ such that the military power does not overthrown him. 

Therefore, $B$ will distribute at least $\bar{P_C}$ to the people.
$$R_t-\bar{P_C} - p_t \ge \bar{P_C}$$
$$R_t- 2\bar{P_C} \ge p_t$$
This can again explains why in autocratic countries, the dictator still care  about economic development, as they need to ensure they have enough money to keep the military power away from rebell.

## The effect of strike

If we analyze the people's strategy closely:
$$f(x) = x$$
We can admire that it is extremely powerful. Not only does it immediately eliminate the incentive for the military power to continue their regime, it also guarantees the end of an autocratic state.
$$R_{t+1} = R_t - \bar{P_C} - p_t$$
$$R_{t+1} \le R_t$$
At some point, $R_{t+n}  < \bar{P_C}$.

It has the same spirit from the tit-for-tat strategy. If you only give me $x$, I will only generate $x$, nothing more, nothing less. This signal basically means: "Don't take away my production output!" In reality, we can see examples of this strategy, such as strike to paralyse the society and demand for more freedom at the cost of economic downturn.

# Conclusion

Even though I made up a lot of unrealistic assumptions in the analysis, such as people's strategy of $f(x)=x$, which causes $R_{t+1} \le R_t$ that is obviously wrong (Many autocratic states achieved economic growth), we can still see some implications in reality, such as:
- People are better off living under autocratic government than a military government. Because under autocratic government, there is a military balancing their power. However in military state, their power is not limited by anyone.  
- The reason why autocratic government still has incentive to boost the economy, is too keep running the regime profitable to himself, as well as satisfying his military power.
- The importance of strike in terms of threatening an autocratic government.


# Reference
Ginkel, J., & Smith, A. (1999). So You Say You Want a Revolution: A Game Theoretic Explanation of Revolution in Repressive Regimes. _The Journal of Conflict Resolution_, _43_(3), 291–316. http://www.jstor.org/stable/174669