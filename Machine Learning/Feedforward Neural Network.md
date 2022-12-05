#machine-learning 

# Universal Approximation Theorem

>A feedforward neural network with sufficiently many sigmoid hidden units in only 1 layer can approximate any well-behaved function to arbitrary precision.

Consider ReLU functions with shiftable kink point
```desmos-graph
left=-5; right=5;
top=10; bottom=-1;
---
y=3 | x<0 | blue
y=x+3 | x >=0 | blue
```

Which is similar to this in Finance.
![[Pasted image 20221205150421.png]]
We can see the importance of non-linearity! 

Another way of understanding this is the composition of linear functions are still linear.

$$z = W(Wx+b)+b = W^2x + K$$

>[!Note] The theorem said 1 layer is enough, why go deep?
>It allows using fewer parameters due to the high nonlinearity that a deeper network can induce, so is faster to train.

# 3 Layer Network

![[Pasted image 20221205151328.png]]

For each neuron, there is an activation function.

$$x_i^{[\ell]} = g(z_i^{[\ell]})$$
There are all kinds of activation function
1. ReLU
2. Sigmoid
3. Tanh

Depending on the type of problem is solving, we devise different loss function
| Problem                   | Loss         |
| ------------------------- | ------------ |
| Regression                | [[Squared Loss]] |
| Classification | [[Cross-entropy loss]]      |
 


*[[Squared Loss]]*
$\ell$ denotes dimension, $q$ denotes example.
$$L(w;S) = \frac{1}{2}\sum_{q=1}^N \sum_\ell (z_\ell^{[3](q)} - y_\ell^{(q)})^2 $$
*[[Cross-entropy loss]]*
$$L(w;S) = -\sum_{q=1}^N\sum_{\ell} y_\ell^{(q)}\log z_\ell^{[3](q)}$$

# Backpropagation

## Gradient Descent
![[Pasted image 20221205165145.png]]

>[!Notes] Epoch
>One iteration of the outer loop, when the model has gone through all examples once.

>[!Note] Batch
>The number of iterations of the inner loop. In GD the batchsize is the number of training examples.

Ending conditions:
1. Max iteration
2. Reached low enough threshold
3. No improvement in n runs

## Stochastic Gradient Descent

Instead of running through the whole training set then update the weights for once, we pick a random small subset of training examples.

Even though the gradient direction of each update does not point exactly towards the local minima of the loss function plane, it's expected value does. Therefore given enough epochs, it can still converge.

>[!Note] Advantages
>SGD can avoid being trapped in a local minimum since SGD has some randomness in the direction of update.
- Again, we can find connection with the [[Reinforcement Learning#$\epsilon$-Greedy Exploration|e-Greedy Exploration]], and the [[trembling hand equilibrium]] in game theory, that sometimes, mistakes can guide to you a better direction.

## With respect to $w^{[3]}_{lk}$
From the k th layer 2 unit to the l th layer 3 unit
$$\frac{\partial L^{(q)}}{\partial w^{[3]}_{lk}} = \frac{\partial L^{(q)}}{\partial z^{[3](q)}_l}  \frac{\partial z^{[3](q)}_l}{\partial x^{[3](q)}_{l}} \frac{\partial x^{[3](q)}_{l}}{\partial w^{[3]}_{lk}}$$
The first term depends on loss function. 
The second term depends on activation function. 
The last term can be expressed as the following

$$\frac{\partial x^{[3](q)}_{l}}{\partial w^{[3]}_{lk}}= z_k^{[2](q)}$$

## With respect to $w^{[2]}_{kj}$
From the j th layer 1 unit to the k th layer 2 unit
$$\frac{\partial L^{(q)}}{\partial w^{[2]}_{kj}} = 
\sum_\ell
\frac{\partial L^{(q)}}{\partial z^{[3](q)}_l}  \frac{\partial z^{[3](q)}_l}{\partial x^{[3](q)}_l} \frac{\partial x^{[3](q)}_l}{\partial z^{[2](q)}_k}
\frac{\partial z^{[2](q)}_k}{\partial w^{[2]}_{kj}}$$
The first 2 terms are calculated before. 
The third term is the connecting weight $w^{[3]}_{lk}$.

## With respect to $w^{[1]}_{ji}$
From the i th input layer unit to the j th layer 1 unit
$$\frac{\partial L^{(q)}}{\partial w^{[1]}_{ji}} = 
\sum_\ell
\frac{\partial L^{(q)}}{\partial z^{[3](q)}_l}  \frac{\partial z^{[3](q)}_l}{\partial x^{[3](q)}_l} 
\left[
\sum_k
\frac{\partial x^{[3](q)}_l}{\partial z^{[2](q)}_k}
\frac{\partial z^{[2](q)}_k}{\partial x^{[2](q)}_k}
\frac{\partial x^{[2](q)}_k}{\partial z^{[1](q)}_j}
\right]
\left[
\frac{\partial z^{[1](q)}_j}{\partial x^{[1](q)}_j} 
\frac{\partial x^{[1](q)}_j}{\partial w^{[1]}_{ji}} 
\right]
$$

# Vanishing Gradient Problem

All of the above update rules includes the derivative of activation functions.

Sigmoid
```desmos-graph
left=-5; right=5;
top=1.5; bottom=-0.5;
    ---
	y = \frac{1}{1+e^{-x}}
```

Tanh
```desmos-graph
left=-5; right=5;
top=1.5; bottom=-1.5;
    ---
	y = \tanh(x)
```

When the unit output is large, the gradient is 0. Thus, vanishing gradient.

Solutions:
1. Smaller weight initialization. [[Xavier Initialization]]
2. Normalize input of each layer. [[Batch normalization]]

