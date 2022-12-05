#activation 

# Definition

$$g(x) = \max(0,x)$$
```desmos-graph
y=0 | x<0 | blue
y = x | x>=0 | blue
```

# Backpropagation
$$\frac{d g}{dx} = \begin{cases} 0 & x<0 \\ 1 & x \ge 0 \end{cases}$$

# Problems

## Not differentiable at 0
We estimate it by a *softplus* function.
$$g(x) = \log(1+e^x)$$
```desmos-graph
y=0 | x<0 | red
y=x | x>0 | red
y=\ln(1+e^{x}) 

```


## Vanishing Gradient
Vanishing gradient problem still happens if $x<0$. Therefore we have [[Leaky ReLU]].
