# Definition
$$g(x) = \begin{cases}x & x \ge 0 \\ a(e^x -1) & \text{otherwise} \end{cases}$$

a = 1
```desmos-graph
right=2;
---
y=x | x>0
y = e^x - 1 | x < 0
y = 0.5(e^x - 1) | x < 0
```

# Backpropagation
$$g'(x) = \begin{cases} 1 & x\ge 0 \\ ae^x & x<0\end{cases}$$

# Advantage

It has a mean activation value closer to 0, which can enable faster learning.

