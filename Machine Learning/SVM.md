#machine-learning #SVM

![[Pasted image 20221201233258.png]]

# Hard SVM

Hard margin SVM is useful on datasets that are [[Linearly Separable]]. The goal is to find a [[Canonical Separating Hyperplane]] which is optimal. That is, the margin between it and its closest points are the largest.

$$w^Tx^{(1)}+w_0 = +1$$
$$w^Tx^{(2)}+w_0 = -1$$
$$w^T(x^{(1)}-x^{(2)}) = 2$$

$W^Tx^{(1)}$ and $W^Tx^{(2)}$ are the projection length of $x^{(1)}, x^{(2)}$ on $W$, multiplied by $|W|$, therefore the margin is:
$$\gamma = \frac{1}{2}\frac{w^T(x^{(1)}-x^{(2)})}{||w||} = \frac{1}{||w||}$$
Therefore, the target is to solve the following problem

## Primal Optimization Problem

$$\min_w \frac{1}{2}||w||^2\text{   such that  } \forall \ell, y^{(\ell)}(w^Tx^{(\ell)}+w_0)\ge1$$
Time complexity depends on $d$.

According to [[Lagrangian Duality]], there is a dual problem.

## Dual Optimization Problem

Define *Lagrangian*

$$L(w,w_0,\alpha) = \frac{1}{2}w^Tw - \sum_{\ell}\alpha^{(\ell)} \left(y^{(\ell)}(w^Tx^{(\ell)}+w_0)-1\right), \forall \alpha^{(\ell)}\ge0$$

Then try to minimize $L$ on $w,w_0$

Calculate $\frac{\partial L}{\partial w}$ and  $\frac{\partial L}{\partial w_0}$

$$\frac{\partial L}{\partial w} =  w - \sum_{\ell} \alpha^{(\ell)}y^{(\ell)}x^{(\ell)} = 0$$
$$w=\sum_{\ell} \alpha^{(\ell)}y^{(\ell)}x^{(\ell)}$$
$$\frac{\partial L}{\partial w_0} =  - \sum_{\ell} \alpha^{(\ell)}y^{(\ell)} = 0$$$$\sum_{\ell} \alpha^{(\ell)}y^{(\ell)} = 0$$

Substitute back to the Lagrangian:

$$\min_{w,w_0}L(w,w_0,\alpha) = \frac{1}{2}\sum_{i} \sum_j\alpha_iy_ix_i\alpha_jy_jx_j - \sum_{i} \sum_j\alpha_iy_ix_i\alpha_jy_jx_j - w_0 \sum_i \alpha_i y_i + \sum_i \alpha_i$$
$$=\sum_i \alpha_i-\sum_{i} \sum_j\alpha_i\alpha_jy_iy_jx_ix_j$$
By the slater's condition and KKT, the dual gap is zero.

The dual problem then is
$$\max_{\alpha} \sum_i \alpha_i-\sum_{i} \sum_j\alpha_i\alpha_jy_iy_jx_ix_j$$
$$\text{ such that} \sum_i\alpha_iy_i=0, \forall i,\alpha_i\ge0$$

This depends on N, where time complexity is $O(N^3)$

We can use SMO algorithms to solve the $\alpha_i$.

## Support Vectors

Points $x$ such that $w^Tx+w_0 =\pm1$ .
$$\alpha_i \ne 0 \iff w^Tx_i+w_0 = \pm1 $$
The canonical optimal separating hyerplane only depends on support vectors.


>[!Tips] Constructing $w,w_0$.
>After finding $\alpha_i$, we can construct $w,w_0$.

$$w = \sum_i \alpha_iy_ix_i = \sum_{x_i\in SV} \alpha_iy_ix_i$$
$$w_0 = \frac{1}{|SV|}\sum_{x_i\in SV} (y_i-w^Tx_i) $$

## Discriminant function

$$g(x) = w^Tx+w_0$$
where $w,w_0$ are defined above.

For every new $x$, if $g(x)>0$, $x\in C_1$. Otherwise $x\in C_2$.


## More than 2 Classes

For each class k, create a SVM $g_k(x)$ for class k and class not k.

Classify to class j if $g_j(x)$ is the largest.


# Soft SVM

## Need for Soft SVM

Not [[Linearly Separable]] due to 
1. Overlapping
2. High noise level

Hard SVM is sentitive to outliers.
![[Pasted image 20221205021426.png]]

## Slack Variables

$$y_i(w^Tx_i+w_0) \ge 1$$
If this constrain is too strict, we try to relax it.
$$y_i(w^Tx_i+w_0) \ge 1-\xi_i$$
>[!Tips] $\xi_i$
>Note that it is subscripted with $i$, that is for each example, they have their own slack variables.

We want to find a canonical separating hyperplane such that the relaxed constrain is true but the slack variables are as small as possible.

### Soft error
We want to minimise the total penalty.
$$\sum_i \xi_i$$

![[Pasted image 20221205022315.png]]

## Primal and Dual Problem

![[Pasted image 20221205022543.png]]


# Alternative formulation
[[Gradient Descent SVM]]


# Non-linear Extension

The original data is not [[Linearly Separable]], then we try to project it to a higher dimensional space with basis function, so that it is [[Linearly Separable]].
![[Pasted image 20221205030745.png]]


## Computation Complexity

To solve this, we need to calculate the dot product between every pair of examples.
![[Pasted image 20221205031023.png]]

For example, original data is of dimension 2, if we have 4 examples, we need
- $_4C_2 \times (2 \text{ multiplication} + 1\text{ addition})$

If the projected data is of dimension 10,
- $_4C_2 \times (10 \text{ multiplication} + 9\text{ addition})$


## Kernel Trick

![[Pasted image 20221205031459.png]]
We only need the dot products, not the transformed examples. It means we can take shortcut to calculate the dot product of transformed data with original  data.

Usually, to find a shortcut, we start with the basis function definiton.
Try to do a tedious dot product, then factorize the terms.
After facterization, usually it can save steps.

Examples are:
1. Polynomial kernel
2. Radial Basis Function Kernel
