# LEARNING MODULE 5

## Deterministic vs. Stochastic SIR
- in a deterministic model, $I(t)$ could be a float value like 304.29 and not necessarily an int value as it represents a continuous approximation
- in a stochastic model, each individual has a discrete state
- at any particular time, we might have 304 infected individuals, but never 304.29
- stochastic variability comes into play because an individual could affect 5 people before recovering or none
- ths is why Monte Carlo experiments are necessary rather than relying on a single simulation

## 2. Bernoulli Trials
- random experiment with 2 possible outcomes:
    - success with a probability of $p$
    - failure with a probability of $1-p$
- probability of at least one successful transmission: 

    $P(infection) = 1-(1-p)^k$ 
    
    where
    - $p$: per-edge transmission probability
    - $k$: infected neighbors

## 3. Translating $\beta$ and $\gamma$ into Probabilities
- the $\beta$ and $\gamma$ that we've used so far are continuous-time rates, not direct probabilities
- for discrete-time stochastic models, we need to convert rates into probabilities over a time step $\Delta t$
- recovery probability: $p_{recovery}=1-e^{-\gamma \Delta t}$ where
    - $\gamma$ is the recovery rate and
    - $\Delta$ is the time step
- infection probability: $p_{infection}=1-e^{-\lambda k \Delta t}$ where
    - $\lambda$ is the per-edge transmission hazard,
    - $k$ is the number of infected neighbors, and
    - $\Delta t$ is the time step
- here, $\beta$ is NOT equal to $\lambda$

    $\lambda = \beta /k_{avg \ target}$
- therefore, our infection probability becomes:

    $p_{infection}=1-e^{(-\beta k \Delta t)/k_{avg \ target}}$

## 4. How a Stochastic Simulation advances through Time

- each day, the simulation will:
    - read the current disease states
    - evaluate possible infections (using infection probability formula)
    - evaluate possible recoveries
    - apply all changes simultaneously 
    - record population totals (S, I, and R values)
- this process is called synchronous updating
- we use this model because if A infects B today, B shouldn't be able to affect C on the same day
- this is used to avoid unnecessary convolution and and artificially influencing the outbreak

## 5. Random Seeds and Reproducibility
- an outcome can change with changes in seed, graph, parameters, and implementation
- sources of randomness:
    - network randomness (Erdős–Rényi graph)
    - epidemic randomness

## 6. Validation
- population conservation: $N = S + I + R$ at every step
- nonnegative counts: $S, I, R >= 0$
- integer counts: $S, I, R \in int$
- valid transition: $S \rightarrow I \rightarrow R$
- no reinfection: $R \nrightarrow I$
- reproducibility: same seed + config $\rightarrow$ same results
- zero transmission: no new infections when $\beta = 0$
- zero recovery: no recovery when $\gamma = 0$