# LEARNING MODULE 3

## 1. The Theory behind Runge-Kutta
- Euler's method: $y_{n+1} = y_n + h \cdot f(t_n,y_n)$
- the Euler estimate forms a straight line that's used for estimation
- on the other hand, n-th order Runge-Kutta or RK(n) uses n slope estimates 
- for example, take RK4's 4 slope estimates:
    - $k_1 = f(t_n,y_n)$
    -> what's the slope at the beginning
    - $k_2 = f(t_n + h/2, y_n + hk_1/2)$ -> what's the slope around the midpoint (using our first estimate)?
    - $k_3 = f(t_n + h/2, y_n + hk_2/2)$ -> let's refine that midpoint estimate
    - $k_4 = f(t_n+h, y_n + hk_3)$ -> what's the slope near the end?
- when the four estimates are combined, we get

    $y_{n+1} = y_n + h(k_1 + 2k_2 + 2k_3 + k_4)/6$

## 2. RK45
- calculates the 4th-order and 5th-order estimates and calculates the difference (that's our error)
- if the error is too large, step size needs to become smaller
- SciPy's Dormand-Prince RK45 implementation, the 5th-order estimate advances the solution, while the 4th-order estimate helps approximate the error
- how does SciPy know the step size?
    - rtol - relative tolerance
    - atol - absolute tolerance
    - for each component, the solver comares its estimated local error against a scale approximately given by: $atol + rtol \cdot |solution \ value|$