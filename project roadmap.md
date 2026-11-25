# Patient Zero

## Comprehensive Project Roadmap

Project Type: Computational Epidemiology, Network Science, Stochastic Simulation & Statistical Analysis

Primary Technologies: Python, NumPy, Pandas, SciPy, NetworkX, Matplotlib, Jupyter Notebook, Tableau Public

### Project Overview

Patient Zero is a computational epidemiology research project investigating how contact-network structures influence infectious disease transmission and how different vaccination strategies affect outbreak severity.

The project combines deterministic mathematical modelling, graph theory, stochastic simulation, Monte Carlo experimentation, and statistical analysis to investigate disease dynamics across three network topologies.

All disease parameters and contact networks are hypothetical. The project is intended for computational research and educational analysis rather than real-world epidemiological forecasting.

### Research Objectives

1. Establish a deterministic SIR model as a mathematical baseline.
2. Construct and analyze contact networks with different structural characteristics.
3. Develop a stochastic, individual-level SIR simulation engine.
4. Investigate the influence of network topology on epidemic dynamics.
5. Evaluate random and degree-targeted vaccination strategies.
6. Quantify stochastic variability through Monte Carlo experimentation.
7. Communicate findings through scientific visualizations and an interactive Tableau Public dashboard.

## Phase 1 — Mathematical Foundations & Deterministic SIR

Objective: Establish the mathematical, computational, and numerical foundations required for epidemic modelling.

### Learning Module 1 — SIR Fundamentals

Topics:

- Compartmental epidemiological models
- Susceptible, Infected, and Recovered populations
- Transmission and recovery rates
- SIR differential equations
- Basic reproduction number
- Epidemic growth, peaks, and decline
- Model assumptions and limitations

Practical component: Playground exercises exploring SIR dynamics and disease parameters.

### Learning Module 2 — Numerical Integration

Topics:

- Ordinary differential equations
- Initial-value problems
- Euler's method
- Discrete time steps
- Numerical approximation errors
- Stability and convergence

Practical component: Playground implementation of Euler's method and exploration of different time-step sizes.

### Learning Module 3 — RK4, RK45 & SciPy

Topics:

- Runge–Kutta methods
- Fourth-order numerical integration
- Adaptive time stepping
- Error estimation and tolerances
- SciPy's `solve_ivp`
- Numerical solver comparisons

Practical component: Playground comparisons of Euler, RK4, and RK45 methods.

### Official Project Implementation

| Checkpoint | Section                             | Deliverable                                                                |
| ---------- | ----------------------------------- | -------------------------------------------------------------------------- |
| 1A         | Imports & Configuration             | Numerical libraries, population parameters, simulation settings            |
| 1B         | SIR Mathematical Model              | Reusable differential equation function                                    |
| 1C         | Deterministic Simulation            | Numerical SIR solution using RK45                                          |
| 1D         | Baseline Visualization              | Susceptible, infected, and recovered trajectories                          |
| 1E         | Metrics & Validation                | Peak infections, peak day, outbreak size, attack rate, conservation checks |
| 1F         | Deterministic Parameter Experiments | Parameter grid, scenario runner, structured results dataset                |

Phase Deliverables: Validated deterministic SIR model, baseline visualization, outbreak metrics, and a structured dataset covering 27 disease parameter combinations.

## Phase 2 — Graph Theory & Network-Based SIR

Objective: Extend epidemic modelling from aggregate population dynamics to individual-level transmission across structured contact networks.

### Learning Module 4 — Graph Theory & NetworkX

Topics:

- Graphs, nodes, and edges
- Degree and degree distributions
- Neighbourhoods and paths
- Clustering coefficients
- Connected components
- Shortest paths
- Erdős–Rényi random networks
- Watts–Strogatz small-world networks
- Barabási–Albert scale-free-like networks
- NetworkX graph generation and analysis

Practical component: Playground construction and manipulation of a small contact network.

### Official Project — Network Generation & Analysis

| Checkpoint | Section                    | Deliverable                                 |
| ---------- | -------------------------- | ------------------------------------------- |
| 2A         | NetworkX Playground        | Small-scale graph experiment                |
| 2B         | Network Generation         | Three reproducible contact networks         |
| 2C         | Network Metrics & Analysis | Structural comparison dataset               |
| 2D         | Network Visualization      | Comparative network topology visualizations |

Network construction uses a shared population of 500 individuals and a target average degree of approximately eight contacts per individual.

### Learning Module 5 — Stochastic SIR

Topics:

- Deterministic versus stochastic modelling
- Individual-level disease states
- Bernoulli trials
- Infection and recovery probabilities
- Conversion of continuous-time rates to discrete-time probabilities
- Neighbour-dependent transmission
- Synchronous state updates
- Random seeds and reproducibility
- Stochastic variability
- Simulation validation

Practical component: Playground experiments with probabilistic transmission, recovery, and random sampling.

### Official Project — Network-Based SIR Engine

| Checkpoint | Section                           | Deliverable                                                    |
| ---------- | --------------------------------- | -------------------------------------------------------------- |
| 2E         | Stochastic Probability Playground | Probabilistic event experiments                                |
| 2F         | Stochastic SIR Implementation     | Reusable individual-level simulation engine                    |
| 2G         | Single Outbreak Simulation        | Epidemic trajectories across network topologies                |
| 2H         | Stochastic Variability            | Multiple realizations under identical model parameters         |
| 2I         | Model Validation                  | Conservation, reproducibility, transition, and edge-case tests |

Phase Deliverables: Three characterized contact networks, a reusable stochastic SIR simulation engine, comparative outbreak trajectories, and model validation results.

## Phase 3 — Interventions & Statistical Experiments

Objective: Evaluate the effectiveness of vaccination interventions and quantify uncertainty across stochastic epidemic outcomes.

### Learning Module 6 — Experimental Design & Vaccination

Topics:

- Experimental controls and treatment groups
- Hypothesis formulation
- Vaccination coverage
- Random vaccination
- Degree-targeted vaccination
- Network centrality and intervention effectiveness
- Fair experimental comparisons
- Confounding variables
- Experimental reproducibility

Practical component: Targeted experiments where necessary to illustrate intervention mechanics.

### Official Project — Vaccination Strategies

Implementation components:

1. Baseline scenarios without vaccination.
2. Random selection of vaccinated individuals.
3. Degree-targeted selection of vaccinated individuals.
4. Vaccination coverage configuration.
5. Vaccination-state integration with the SIR engine.
6. Consistent initial conditions and experimental controls.
7. Verification of vaccination assignments and population counts.

### Learning Module 7 & 8 — Monte Carlo & Statistics

Topics:

- Monte Carlo simulation
- Independent stochastic replications
- Random number generation
- Sampling variability
- Descriptive statistics
- Confidence intervals
- Distribution analysis
- Effect sizes and comparative statistics
- Computational efficiency and experimental batching

Practical component: Small-scale sampling and uncertainty experiments where appropriate.

### Official Project — Monte Carlo Experiments

Experimental configuration

| Parameter                       | Options                                                  |
| ------------------------------- | -------------------------------------------------------- |
| Population                      | 500                                                      |
| Initially infected              | 1%, 5%, 10%                                              |
| Transmission rate (\\(\beta\\)) | 0.2, 0.3, 0.4                                            |
| Recovery rate (\\(\gamma\\))    | 0.10, 0.20, 0.25                                         |
| Network topologies              | Random, small-world, scale-free                          |
| Vaccination strategies          | Random, degree-targeted                                  |
| Vaccination configurations      | 1 unvaccinated baseline + 3 coverage levels per strategy |
| Monte Carlo repetitions         | 100 per configuration                                    |

Planned Experimental Scale

Disease scenarios

# 27

Scenario configurations

# 567

Total simulation runs

# 56,700

$3\times3\times3\times3\times7\times100=56{,}700$

Execution strategy and final batch size are subject to performance benchmarking.

### Official Project — Statistical Analysis

Implementation components:

1. Consolidation of Monte Carlo outputs.
2. Calculation of mean and median outbreak metrics.
3. Estimation of standard deviations and confidence intervals.
4. Comparison of epidemic severity across topologies.
5. Evaluation of vaccination effectiveness.
6. Analysis of stochastic extinction and outbreak variability.
7. Identification of meaningful trends and interactions.
8. Preparation of structured statistical summary datasets.

Phase Deliverables: Vaccination intervention framework, Monte Carlo experiment dataset, statistical comparisons, and quantitative findings.

## Phase 4 — Scientific Visualization & Tableau Public

Objective: Translate experimental outputs into interpretable scientific findings and interactive visual analytics.

### Learning Module 9 — Scientific Visualization

Topics:

- Visualization principles for scientific research
- Time-series comparisons
- Distribution visualizations
- Uncertainty and confidence intervals
- Network visualizations
- Visualizing intervention effectiveness
- Figure consistency and accessibility
- Network animation techniques
- Interpretation of comparative graphics

### Official Project — Research Visualizations

Planned visualizations include:

- Deterministic and stochastic SIR curves.
- Comparative outbreak trajectories across network topologies.
- Degree distributions and network structure comparisons.
- Monte Carlo outbreak-size distributions.
- Peak infection and peak timing comparisons.
- Vaccination strategy effectiveness plots.
- Confidence intervals and uncertainty visualizations.
- Selected network infection-state snapshots or animations.

### Learning Module 10 — Tableau Public

Topics:

- Tableau data structures
- Dimensions and measures
- Data relationships
- Calculated fields
- Interactive filters and parameters
- Dashboard layout and navigation
- Visual storytelling
- Publishing and sharing Tableau dashboards

### Official Project — Tableau Data Exports

Preparation of analysis-ready CSV datasets covering:

1. Deterministic scenario summaries.
2. Stochastic simulation summaries.
3. Time-series epidemic trajectories.
4. Network structural metrics.
5. Vaccination intervention comparisons.
6. Statistical aggregates and uncertainty estimates.

### Tableau Public Dashboard

The dashboard will support interactive exploration of disease configurations, network topologies, vaccination strategies, and vaccination coverage.

Planned dashboard views include epidemic trajectories, outbreak severity comparisons, vaccination effectiveness, network characteristics, and statistical summaries.

Phase Deliverables: Publication-quality scientific figures, Tableau-ready datasets, and an interactive Tableau Public research dashboard.

## Phase 5 — Documentation, Validation & Publication

Objective: Consolidate the modelling, experimentation, and analysis into a reproducible and professionally presented research portfolio project.

### Learning Module 11 — Scientific Reporting & Reproducibility

Topics:

- Research question formulation
- Scientific methodology documentation
- Experimental reproducibility
- Results interpretation
- Statistical reporting
- Research limitations
- Technical documentation
- Responsible communication of simulation findings
- Research presentation and publication

### Official Project — Findings & Conclusions

Research reporting components:

1. Research objectives and hypotheses.
2. Mathematical and computational methodology.
3. Network topology characteristics.
4. Deterministic and stochastic model comparisons.
5. Vaccination intervention findings.
6. Statistical interpretation of Monte Carlo experiments.
7. Model assumptions and limitations.
8. Research conclusions.
9. Potential extensions and future work.

### Official Project — Documentation & Final Polish

Finalization tasks:

- Comprehensive Jupyter Notebook Markdown documentation.
- Code organization and removal of temporary experiments.
- Consistent naming and figure numbering.
- Reproducibility and execution-order verification.
- Final validation of datasets and calculations.
- Dependency documentation.
- Project README.
- GitHub repository organization.
- Tableau dashboard integration.
- Research methodology and limitations documentation.

### Publication & Portfolio Presentation

Final publication components:

1. Public GitHub repository.
2. Reproducible research notebook.
3. Tableau Public dashboard.
4. Project overview and technical documentation.
5. Selected research figures and findings.
6. Professional project showcase materials.

Phase Deliverables: Complete research notebook, documented GitHub repository, published Tableau dashboard, and presentation-ready research findings.

# Optional Extension — Module 12: SEIR Modelling

Objective: Extend the SIR framework by introducing an exposed, non-infectious compartment to represent an incubation period.

Potential extensions include:

- SEIR differential equations.
- Individual-level exposed states.
- Incubation-period parameters.
- Stochastic SEIR transitions.
- Comparative SIR and SEIR simulations.
- Sensitivity analysis of incubation periods.
- Extensions to the Tableau dashboard.

This module is supplementary to the core research scope.

## Development & Learning Methodology

The project follows a structured learning-driven development approach.

| Component                       | Method                                                                    | Purpose                                   |
| ------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------- |
| Learning Modules                | Conceptual instruction and independently written notes                    | Establish theoretical understanding       |
| Playground Exercises            | Runnable experimental code and exploratory analysis                       | Develop practical intuition               |
| Official Project Implementation | Incremental, manually written code with line-by-line understanding        | Build the research system                 |
| Validation Checkpoints          | Assertions, controlled tests, numerical checks, and output interpretation | Establish correctness and reproducibility |
| Documentation & Publication     | Research reporting, technical documentation, and portfolio preparation    | Communicate methods and findings          |

### Final Project Deliverables

1. Patient Zero Research Notebook — Complete mathematical modelling, network generation, stochastic simulation, interventions, statistical experiments, and research analysis.
2. Tableau Public Dashboard — Interactive visualization of epidemic dynamics, network effects, and vaccination effectiveness.
3. GitHub Repository — Reproducible source code, dependencies, datasets, methodology, and documentation.
4. Research Findings — Evidence-based conclusions concerning network topology, outbreak variability, and vaccination intervention effectiveness.

Central research question: How do contact-network topology and vaccination strategy influence epidemic spread, outbreak severity, and intervention effectiveness in a stochastic SIR model?