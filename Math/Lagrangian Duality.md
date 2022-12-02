# Primal Problem

$$\inf_x f_0(x)$$
$$f_i(x) \le 0, \forall i \in [1,m]$$
$$h_i(x) = 0, \forall i \in [1,q]$$

A constrained optimization problem with equality and inequality constrains.

## Min-max representation of the Primal Problem

We can express the Primal Problem in Lagrangian.

$$L(x,\lambda,v) = f_0(x) + \sum_{i=1}^m \lambda_i f_i(x) + \sum_{i=1}^q v_ih_i(x)$$
Note that $v_i$ are unconstained, but $\lambda_i \ge 0$.

See definition of [[Supremum]].
With $\lambda_i \ge 0$, we have $\sum_{i=1}^m \lambda_i f_i(x) \le 0$, thus:
$$\sup_{\lambda\ge0,v} L(x,\lambda,v) = \sup_{\lambda\ge0,v} [f_0(x) + \sum_{i=1}^m \lambda_i f_i(x) + \sum_{i=1}^q v_i h_i(x)]$$
* if x fulfills all the constrains, i.e., x is feasible, then $\sup_{\lambda\ge0,v} L(x,\lambda,v)  = f_0(x)$
* otherwise, $\sup_{\lambda\ge0,v} L(x,\lambda,v)  = \infty$ 

Therefore, with the assumption that x is feasible, we can conclude that
$$\sup_{\lambda\ge0,v} L(x,\lambda,v) = 
\begin{cases} 
          f_0(x) &  x \text { is feasible}\\
          \infty & \text{otherwise} 
       \end{cases}$$
Then we need to apply Infinum to this expression, with x as the decision variable:
$$\inf_x\sup_{\lambda\ge0,v} L(x,\lambda,v) = \inf_x f_0(x)$$

# Dual Problem

If we change the order, we get the dual problem:
$$\sup_{\lambda\ge0,v} \inf_x L(x,\lambda,v)$$
From the weak duality, we know that the dual solution is less than or equal to the primal solution.
Therefore, solving the dual problem is finding the best lower bound for the primal solution.


## Weak duality
$$\text{Primal}\ge\text{Dual}$$
$$\inf_x \sup_{\lambda\ge0,v} L(x,\lambda,v) \ge \sup_{\lambda\ge0,v} \inf_x L(x,\lambda,v)$$
Proof:
Consider any function $f: W \times Z \rightarrow R$
$$\inf_{w\in W} f(w,z_0) \le f(w_0,z_0) \le \sup_{z\in Z}f(w_0,z)$$
$$\inf_{w\in W} f(w,z_0) \le \sup_{z\in Z}f(w_0,z)$$
* Above is true for arbitrary $z_0, w_0$
* Substitute $z_0, w_0$ with their largest or smallest possible (Here assume W and Z are closed)
$$\sup_{z\in Z}\inf_{w\in W}f(w,z) \le \inf_{w\in W}\sup_{z\in Z}f(w,z)$$
## Strong duality
$$\text{Primal} = \text{Dual}$$
$$\inf_x \sup_{\lambda\ge0,v} L(x,\lambda,v) = \sup_{\lambda\ge0,v} \inf_x L(x,\lambda,v)$$
