#activation

# Definition
$$g(x) = \begin{cases} x & x\ge0 \\ ax & \text{otherwise}\end{cases}$$
```desmos-graph
y=0.1x | red | x < 0
y=x | red | x > 0
```

# Backpropagation
$$g'(x) = a, x<0$$

# Drawback

Non differentiable at x=0, therefore we have [[Exponential Linear Unit]].
