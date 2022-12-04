#SVM 

# Hard-Margin SVM

We want to find a plane, such that $y_i g(x_i) -1 \ge 0$ for all $i$, and keeping $w$ small.

We can design a loss function to do gradient descent.

$$L = \sum_i E_\infty \left(y_ig(x_i)\right)+\lambda||w||^2$$
$$E_\infty(z) = \begin{cases}0 & z\ge1 \\ C & \text{otherwise}\end{cases}$$

A huge loss $C$ will give a steep gradient, to quickly rectify the bad hyperplane.

Update rule:
$$\frac{\partial L}{\partial w} = \frac{\partial}{\partial w}\sum_i E_\infty \left(y_i(w^Tx_i+w_0)\right)+\lambda||w||^2$$
$$=\sum_i\frac{\partial}{\partial w} E_\infty \left(y_i(w^Tx_i+w_0)\right)+\lambda\frac{\partial}{\partial w}w^Tw$$
$$=\sum_i 0+\lambda2w$$
We can see that $E_\infty(z)$ are constant and not varying with $w$. This formulation has bug. But it helps us to see why hinge loss can work.

# Hard-Margin SVM

The only difference, is the *otherwise* part of the $E_\infty(z)$, we use *hinge loss* instead.
$$E_\infty(z) = 1-z, \forall z < 1$$
![[Pasted image 20221205025522.png]]

Then we can have
$$\frac{\partial L}{\partial w}=\sum_i 1\left[y_i(w^Tx_i+w_0)<1\right](-1)y_ix_i+\lambda2w$$
- If $x$ is class 1 but treated as -1 --> $w$ is too far away from $x$ --> subtract gradient so that $w \leftarrow w + \alpha x_i$

