# LEARNING MODULE 2

## 1. Shortcomings of differential equations
- the formula for $dI/dt$ tells us the rate at which infections are changing right now
- this doesn't give us any information about how many people will be infected tomorrow, next week, or next month
- we use numerical integration to solve the differential equation for different periods of time

## 2. Euler's method
- generally, 

    $New Value \approx Old \ Value + Rate \ of \ Change \cdot Time \ Elapsed$
- mathematically, it can be written as

    $y(t + \Delta t) \approx y(t) + (dy/dt)\Delta t$
- let's now apply this to the SIR equations:

    $S_{t+\Delta t} = S_t - \beta \cdot [(S_t \cdot I_t)/N] \cdot \Delta t$

    $I_{t+ \Delta t} = I_t + (\beta \cdot [(S_t \cdot I_t)/N] - \gamma I_t) \cdot \Delta t$

    $R_{t+ \Delta t} = R_t + \gamma I_t \Delta t$

## 3. Time-step Size
- larger the time step, more the possibility of the model introducing errors
- it approximates too much if $\Delta t$ is too large
- try comparing $\Delta t_1$ = 1 day, $\Delta t_{0.5}$ = 0.5 day, and $\Delta t_{0.1}$ = 0.1 day

## 4. Euler vs. SciPy
- Euler's method: 
    - simple
    - first-order accuracy
    - usually fixed step sizes
    - manual error control
    - use for learning and validation
- SciPy RK45:
    - sophisticated complexity
    - higher-order accuracy
    - adaptive step sizes
    - built-in tolerances for error control
    - use as the main deterministic SIR model

## 5. Conservation
- we know that $N = S + I + R$
- let's add our differential equations:

    $dN/dt$

    $=dS/dt + dI/dt + dR/dt$

    $= - \beta \cdot (S \cdot I / N) + \beta (S \cdot I / N) - \gamma \cdot I + \gamma \cdot I$

    $= 0$