#SVM 

It is defined only for a [[Linearly Separable]] dataset.

For a given dataset, we want the points closest to the hyperplane can satisfy
$$|w^Tx + w_0| = 1$$
And for all other points, we want
$$|w^Tx+w_0|>1$$
Considered the label $y$, we can express the constrain as:
$$y(w^Tx+w_0) \ge 1$$

![[Pasted image 20221204233825.png]]

To convert a general separating hyperplane to a canonical separating hyperplane, we need to do some scaling.


If the hyperplane is optimal, that is, the margin is maximised, then both side must be equal distance.
$$w^Tx_1 + w_0 = \pm k_1$$
$$\frac{1}{k_1}w^T x_1 + \frac{w_0}{k_1} = \pm1$$