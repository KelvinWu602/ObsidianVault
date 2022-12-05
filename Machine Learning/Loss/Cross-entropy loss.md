# Definition
$$L = -\sum_{\ell=1}^N\sum_{i=1}^d y_i^\ell \log f_i^\ell$$
- $\ell$ indexed example
- $i$ indexed output dimension

# Backpropagation
$$\frac{\partial L}{\partial f_i^\ell} = - \frac{ y^\ell_i}{f^\ell_i}$$
