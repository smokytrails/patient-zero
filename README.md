# Patient Zero

### Infectious Disease Simulation and Vaccination Experiments on Complex Networks

*An investigation into epidemic dynamics, network topology, and the effectiveness of network-aware vaccination strategies.*

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![NetworkX](https://img.shields.io/badge/NetworkX-Graph_Theory-43853D?style=flat-square)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-Interactive_Dashboard-E97627?style=flat-square&logo=tableau&logoColor=white)

**[Explore the Interactive Tableau Dashboard](https://public.tableau.com/app/profile/harshita.nagasubramanian/viz/PatientZero/Dashboard4)** | **[View the Research Notebook](patient_zero.ipynb)**

---

## Static Dashboard View

<!-- Centered Dashboard Preview -->
<p align="center">
  <img src="assets/Patient Zero - Cover Page.png" alt="MapKW" width="600px">
</p>

---

## Project Overview

Infectious diseases do not spread through populations uniformly. The underlying structure of social connections influences how quickly infections propagate, how severe outbreaks become, and how effectively interventions can contain transmission.

**Patient Zero** is a computational research project that investigates these dynamics through mathematical modelling, graph theory, stochastic epidemic simulation, Monte Carlo experimentation, and statistical inference.

The project progresses from a deterministic compartmental SIR model to an individual-level, network-based SIRV simulation engine, evaluating random and degree-targeted vaccination strategies across three distinct network topologies.

The resulting simulation data is transformed into an interactive Tableau dashboard, enabling exploration of epidemic outcomes across different epidemiological parameters and intervention configurations.

## Project at a Glance

| Metric | Scale |
|---|---:|
| Stochastic epidemic simulations | 56,700 |
| Unique experimental scenarios | 567 |
| Individuals per simulation | 500 |
| Network topologies | 3 |
| Vaccination configurations | 7 |
| Monte Carlo repetitions per scenario | 100 |
| Matched experimental comparison groups | 81 |
| Statistical strategy comparisons | 9 |

## Research Question

> How does network topology influence epidemic outcomes, and how effectively can network-aware vaccination strategies reduce outbreak severity?

### Research Objectives

- Model infectious disease transmission using deterministic and stochastic epidemic models.
- Investigate the relationship between network connectivity and epidemic behaviour.
- Quantify stochastic variability across repeated outbreak simulations.
- Compare random and degree-targeted vaccination strategies at different coverage levels.
- Evaluate vaccination effectiveness relative to matched unvaccinated baselines.
- Quantify statistical uncertainty and assess the significance of intervention outcomes.
- Communicate computational research findings through interactive data visualization.

---

## Methodology

### 1. Mathematical Foundations

The project begins with the classical Susceptible-Infected-Recovered (SIR) compartmental model, represented by a system of ordinary differential equations:

$$
\frac{dS}{dt}=-\beta\frac{SI}{N}
$$

$$
\frac{dI}{dt}=\beta\frac{SI}{N}-\gamma I
$$

$$
\frac{dR}{dt}=\gamma I
$$

Where:

- $S$ represents susceptible individuals.
- $I$ represents infected individuals.
- $R$ represents recovered individuals.
- $\beta$ represents the transmission rate.
- $\gamma$ represents the recovery rate.
- $N$ represents the total population.

Numerical solutions are computed using SciPy's adaptive RK45 integration method, based on the Dormand-Prince 5(4) Runge-Kutta pair.

A deterministic parameter sweep establishes foundational relationships between transmission, recovery, initial infection levels, and epidemic outcomes before introducing network structure and stochasticity.

### 2. Graph Theory & Network Modelling

Populations are represented as graphs, where nodes correspond to individuals and edges represent potential disease-transmitting contacts.

Three network generation models are implemented using NetworkX:

| Network Topology | Generation Model | Structural Characteristics |
|---|---|---|
| Random | Erdős-Rényi | Randomly distributed connections and relatively homogeneous connectivity |
| Small-world | Watts-Strogatz | High local clustering and short network paths |
| Scale-free | Barabási-Albert | Heterogeneous connectivity and highly connected hubs |

Each network contains 500 nodes with a target average degree of approximately eight, supporting comparisons across different connectivity structures.

Network analysis examines degree distributions, clustering coefficients, connected components, maximum degree, and average shortest-path lengths.

### 3. Stochastic Epidemic Simulation

The deterministic model is extended into an individual-level stochastic simulation in which disease transmission occurs through established network connections.

The probability of infection depends on the number of infected neighbours:

$$
P(S\rightarrow I)=1-\exp\left(-\frac{\beta k_I\Delta t}{\bar{k}_{\mathrm{target}}}\right)
$$

The probability of recovery is defined as:

$$
P(I\rightarrow R)=1-\exp(-\gamma\Delta t)
$$

The simulation engine incorporates synchronous state transitions, randomized initial infections, reproducible random-number generation, population conservation checks, and natural outbreak termination.

Vaccination subsequently extends the model into a four-compartment SIRV framework:

$$
S+I+R+V=N
$$

Vaccinated individuals remain within the network but are protected from infection.

### 4. Vaccination Strategies

Three intervention strategies are evaluated:

| Strategy | Description | Coverage |
|---|---|---|
| None | Unvaccinated experimental baseline | 0% |
| Random | Individuals selected uniformly at random | 10%, 20%, 30% |
| Degree-Targeted | Individuals prioritized by highest network degree | 10%, 20%, 30% |

Degree-targeted vaccination investigates whether protecting highly connected individuals can disrupt transmission pathways more effectively than distributing vaccines randomly.

### 5. Monte Carlo Experimentation

A full factorial experimental design evaluates epidemic behaviour across the following parameter space:

| Experimental Factor | Values |
|---|---|
| Population size | 500 |
| Network topology | Random, Small-world, Scale-free |
| Initial infected proportion | 1%, 5%, 10% |
| Transmission rate ($\beta$) | 0.2, 0.3, 0.4 |
| Recovery rate ($\gamma$) | 0.10, 0.20, 0.25 |
| Vaccination configuration | 7 configurations |
| Repetitions | 100 per scenario |
| Maximum simulation duration | 1,000 days |

The factorial design produces:

$$
3\times3\times3\times3\times7=567
$$

unique experimental scenarios and:

$$
567\times100=56,700
$$

stochastic epidemic simulations.

The computational pipeline incorporates:

- Independent random-number streams for vaccination, initial infection assignment, and disease progression.
- Matched seeds across corresponding experimental repetitions.
- Batch-based execution across 27 computational batches.
- Persistent CSV checkpoints for interruption recovery.
- Reproducibility and simulation integrity checks.

### 6. Statistical Analysis

Simulation outcomes are evaluated using five principal epidemiological metrics:

| Metric | Description |
|---|---|
| Final outbreak size | Total individuals infected throughout an outbreak |
| Peak infections | Maximum simultaneous infections |
| Time to peak | Time required to reach maximum infections |
| Epidemic duration | Time until outbreak termination or the simulation limit |
| Attack rate | Proportion of the total population infected |

Vaccination effectiveness is calculated relative to the corresponding unvaccinated baseline:

$$
E=100\left(\frac{\bar{O}_0-\bar{O}_v}{\bar{O}_0}\right)
$$

The additional benefit of degree-targeted vaccination is quantified as:

$$
A=\bar{O}_{\mathrm{random}}-\bar{O}_{\mathrm{targeted}}
$$

Statistical inference incorporates:

- Stratified paired bootstrap resampling with 2,000 iterations.
- Percentile-based 95% confidence intervals.
- One-sided paired sign-flip permutation tests with 10,000 permutations.
- Holm multiple-comparison correction.
- Aggregation sensitivity analysis.

---

## Key Findings

### Network Structure Influences Epidemic Severity

Across unvaccinated baseline simulations:

| Network Topology | Mean Outbreak Size | Mean Peak Infections | Mean Duration |
|---|---:|---:|---:|
| Random | 280.94 | 78.05 | 71.40 days |
| Small-world | 216.95 | 57.63 | 70.27 days |
| Scale-free | 291.84 | 95.92 | 62.29 days |

The evaluated scale-free network exhibited the largest average outbreak size and highest peak infection burden, despite having the shortest average epidemic duration.

These findings demonstrate that greater epidemic severity does not necessarily correspond to longer outbreak duration.

### Degree-Targeted Vaccination Outperforms Random Vaccination

At 20% vaccination coverage, average reductions in final outbreak size relative to matched unvaccinated baselines were:

| Network Topology | Random Vaccination | Degree-Targeted Vaccination |
|---|---:|---:|
| Random | 39.84% | **61.44%** |
| Small-world | 40.14% | **49.25%** |
| Scale-free | 36.66% | **83.21%** |

Degree-targeted vaccination achieved greater aggregate outbreak reductions across all three evaluated network structures.

The largest effectiveness at this coverage level was observed in the scale-free network, where targeting highly connected individuals substantially disrupted epidemic transmission.

### Network-Aware Interventions Can Improve Vaccine Allocation

The largest estimated advantage of degree-targeted vaccination over random vaccination occurred in the scale-free network at just 10% coverage.

| Metric | Result |
|---|---:|
| Network topology | Scale-free |
| Vaccination coverage | 10% |
| Additional infections prevented | **155.01** |
| 95% confidence interval | 153.33–156.64 |
| Holm-adjusted p-value | 0.0009 |

All nine aggregate topology-coverage comparisons favoured degree-targeted vaccination, with bootstrap confidence intervals above zero.

However, the additional benefit of targeting did not increase monotonically with vaccination coverage, highlighting the importance of distinguishing overall vaccination effectiveness from the incremental advantage of a particular allocation strategy.

These findings are conditional on the simulated networks, experimental parameters, and model assumptions.

---

## Interactive Tableau Dashboard

The computational results are presented through a custom three-page Tableau Public experience.

**[Launch the Patient Zero Dashboard](https://public.tableau.com/app/profile/harshita.nagasubramanian/viz/PatientZero/Dashboard4)**

### Dashboard Features

| Visualization | Analytical Purpose |
|---|---|
| Epidemic Severity vs. Duration | Examines relationships between outbreak size, duration, and peak infections |
| Vaccination Effectiveness | Compares outbreak reductions across topologies and intervention strategies |
| Targeted Vaccination Advantage | Presents additional infections prevented and associated confidence intervals |
| Outbreak Distribution | Visualizes outbreak-size distributions using custom violin plots |
| Vaccination Impact Across Scenarios | Encodes scenario-level outbreak reductions through radial geometry |
| Epidemic Risk Profile | Illustrates the probability of different outbreak severity classifications |

Interactive filters support exploration across network topology, vaccination strategy, vaccination coverage, transmission rate, recovery rate, and initial infected proportion, where supported by the underlying datasets.

The presentation also includes a dedicated research appendix documenting methodology, model assumptions, statistical analysis, data sources, and academic references.

### Custom Visualization Engineering

Several dashboard visualizations required specialized data transformations beyond conventional Tableau chart construction:

- **Violin plots:** Gaussian kernel density estimation, mirrored polygon geometry, density normalization, and ordered coordinate paths.
- **Radial visualization:** Trigonometric transformations converting scenario-level effectiveness estimates into radial polygon coordinates.
- **Risk pictograms:** Polygon-based human figures representing estimated outbreak severity proportions.
- **Confidence interval plots:** Dual-axis visualization of statistical point estimates and uncertainty intervals.

The precomputed confidence intervals represent the full epidemiological parameter grid for each topology and coverage combination. They are not dynamically re-estimated when filtering individual epidemiological parameters.

---

## Data Engineering

All epidemic data is generated synthetically through the Python simulation engine. No external patient records or observed epidemiological datasets are used.

The analytical pipeline transforms individual simulation outcomes into validated, dashboard-ready datasets.

### Core Analytical Datasets

| Dataset | Records | Description |
|---|---:|---|
| `simulation_results.csv` | 56,700 | Individual stochastic simulation outcomes |
| `scenario_summary.csv` | 567 | Aggregated scenario-level epidemic metrics |
| `vaccination_effectiveness.csv` | 18 | Vaccination effectiveness and uncertainty estimates |
| `strategy_comparison.csv` | 9 | Targeted vaccination advantages and statistical inference |
| `vaccination_effectiveness_detailed.csv` | 486 | Parameter-level vaccination effectiveness |
| `strategy_comparison_detailed.csv` | 243 | Parameter-level strategy comparisons |

### Visualization-Specific Datasets

| Dataset | Records |
|---|---:|
| `violin_density.csv` | 57,267 |
| `violin_polygons.csv` | 114,534 |
| `violin_comparison.csv` | 147,258 |
| `radial_outbreak.csv` | 2,268 |
| `epidemic_risk_pictogram.csv` | 680,400 |

These datasets encode existing simulation outcomes into visualization-compatible structures and do not represent additional epidemic simulations.

---

## Technical Stack

| Technology | Application |
|---|---|
| Python | Simulation engine, experimentation, and data processing |
| NumPy | Numerical computation and random-number generation |
| Pandas | Data transformation, aggregation, and analytical pipelines |
| SciPy | Numerical integration and kernel density estimation |
| NetworkX | Graph generation and network analysis |
| Statsmodels | Multiple-comparison correction |
| Matplotlib | Scientific visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Computational research and documentation |
| Tableau Public | Interactive dashboards and visual storytelling |
| Git & GitHub | Version control and project publication |

---

## Validation & Reproducibility

Computational validation is integrated throughout the research workflow.

Validation procedures include:

- Population conservation across disease compartments.
- Verification of valid individual disease states.
- Numerical integration integrity checks.
- Vaccination coverage and node-selection validation.
- Zero-transmission and zero-infection edge cases.
- Seed-based simulation reproducibility.
- Experimental scenario and repetition completeness checks.
- Simulation outcome range and consistency validation.
- CSV export integrity and row-count verification.
- Visualization geometry and polygon path validation.

Fixed random seeds, matched experimental repetitions, and persistent simulation checkpoints support reproducible analysis within the defined experimental environment.

### Exploring the Project

The easiest way to explore Patient Zero is through the published Tableau dashboard or the official Jupyter notebook, which contains the mathematical foundations, implementation, saved outputs, figures, statistical analysis, and research conclusions.

To establish a local Python environment:

```bash
pip install numpy pandas scipy networkx statsmodels matplotlib seaborn jupyter
```

Open the research notebook:

```bash
jupyter notebook patient_zero.ipynb
```

**Computational note:** The complete Monte Carlo experiment is computationally intensive and originally required approximately three hours to complete. Running the entire notebook is unnecessary for reviewing the research. Existing saved outputs and consolidated simulation results can be used for downstream analysis without repeating all 56,700 simulations.

---

## Model Assumptions & Limitations

Patient Zero is designed as a controlled computational research experiment rather than a calibrated epidemiological forecasting system.

The model assumes:

- A closed population of 500 individuals for network experiments.
- Static contact networks with one fixed realization per topology.
- Constant transmission and recovery parameters within each simulation.
- Perfectly protective vaccination administered before outbreak initiation.
- Permanent immunity following recovery within the simulation.
- No demographic changes, behavioural adaptation, or population migration.

The results are conditional on these assumptions, the selected network realizations, and the evaluated epidemiological parameter grid.

Statistical confidence intervals quantify uncertainty within the experimental design rather than uncertainty across real-world populations.

### Future Research

Potential extensions include:

- Independent network realizations and larger populations.
- Dynamic and temporally evolving contact networks.
- Imperfect vaccine efficacy and waning immunity.
- Alternative centrality-based vaccination strategies.
- Additional epidemiological compartments, including exposed individuals.
- Empirical contact-network integration and epidemiological calibration.

---

## Conclusion

Patient Zero demonstrates how network structure and intervention allocation can influence simulated infectious disease transmission.

Across the evaluated experimental conditions, degree-targeted vaccination consistently achieved greater aggregate outbreak reductions than random vaccination, with particularly substantial benefits in the scale-free network.

By combining mathematical modelling, graph theory, stochastic simulation, statistical inference, data engineering, and interactive visualization, the project provides an end-to-end computational framework for investigating epidemic dynamics and network-aware intervention strategies.

---

## Academic References

1. Kermack, W. O., & McKendrick, A. G. (1927). *A contribution to the mathematical theory of epidemics.* Proceedings of the Royal Society of London A, 115, 700–721. [DOI](https://doi.org/10.1098/rspa.1927.0118)

2. Erdős, P., & Rényi, A. (1959). *On random graphs I.* Publicationes Mathematicae Debrecen, 6, 290–297.

3. Watts, D. J., & Strogatz, S. H. (1998). *Collective dynamics of 'small-world' networks.* Nature, 393, 440–442. [DOI](https://doi.org/10.1038/30918)

4. Barabási, A.-L., & Albert, R. (1999). *Emergence of scaling in random networks.* Science, 286, 509–512. [DOI](https://doi.org/10.1126/science.286.5439.509)

5. Cohen, R., Havlin, S., & ben-Avraham, D. (2003). *Efficient immunization strategies for computer networks and populations.* Physical Review Letters, 91, 247901. [Article](https://pubmed.ncbi.nlm.nih.gov/14683159/)

---

## About the Author

**Harshita Nagasubramanian**

BSc (Honours) Data Science  
Big Data Concentration | Management Option  
Wilfrid Laurier University

A data science graduate with experience in process automation, digital transformation, and business intelligence, complemented by a strong interest in artificial intelligence, computational modelling, and data visualization.

---

**Patient Zero** | Computational Research & Data Visualization | 2026
