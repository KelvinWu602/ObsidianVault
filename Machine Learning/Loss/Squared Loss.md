#loss 

# Definition
$$L = \frac{1}{2}\sum_{\ell=1}^N \sum_{i=1}^d (f_i^{\ell} -y_i^{\ell})^2$$
- $\ell$ indexed example
- $i$ indexed output dimension

# Backpropagation
$$\frac{\partial L}{\partial f_i^\ell}=\frac{1}{2} 2(f_i^\ell-y_i^\ell)=f_i^\ell-y_i^\ell$$






