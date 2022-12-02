The output is continuous numerical value.


# Evaluation
1. [[Squared Loss]]

## Math (multivariable calculus)

$$w = (X^TX)^{-1}X^Ty$$
Proof: 
$$\frac{\partial L}{\partial w_i} = \sum_{\ell=1}^N 2(w_0x_0^\ell + w_1x_1^\ell + w_2x2^\ell + .. + w_dx_d^\ell) x_i^{\ell} = 0$$
$$w_0 \sum x_ix_0 + w_1 \sum x_i $$