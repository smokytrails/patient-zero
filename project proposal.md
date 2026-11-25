# Patient Zero
## An Interactive Epidemiological Simulation and Network Analysis Project

**Project Type:** Computational Research, Mathematical Modelling & Data Science  
**Project Duration:** 7 Days (15–25 Focused Hours)  
**Project Status:** Planning  
**Portfolio Series:** Technical Explorations — Project 01 of 05  
**Primary Language:** Python  
**Development Environment:** VS Code and Jupyter Notebook

---

## 1. Executive Summary

*Patient Zero* is a computational research project designed to investigate how infectious diseases spread through populations and how different social structures and public health interventions influence outbreak dynamics.

The project will explore two approaches to epidemiological modelling: traditional compartmental models, which represent populations as groups of susceptible, infected, and recovered individuals, and network-based simulations, which model disease transmission through individual social connections.

Through mathematical modelling, graph theory, stochastic simulation, and Monte Carlo experimentation, Patient Zero will investigate how network structure influences outbreak severity, duration, and intervention effectiveness.

The final product will combine an executable Jupyter Notebook, animated simulations, statistical comparisons, and potentially an interactive Tableau Public dashboard.

Unlike a conventional software development project, Patient Zero will prioritize computational experimentation, mathematical understanding, and scientific interpretation over application infrastructure or frontend engineering.

## 2. Project Motivation

Patient Zero is the first project in a planned series of five independent technical portfolio projects, each designed to explore a different area of computer science, data science, or artificial intelligence.

The series is intended to encourage hands-on learning through relatively short, technically challenging experiments.

A central motivation is to move away from large, infrastructure-heavy software projects involving multiple services, extensive application architecture, and complicated deployment workflows.

Instead, the focus will be on smaller computational problems that can be understood, implemented, tested, visualized, and documented within approximately one week.

Patient Zero was selected as the first project because it offers a strong combination of mathematical modelling, algorithmic experimentation, graph theory, and visual storytelling.

The project will also establish a repeatable approach for documenting technical work and communicating findings through GitHub and LinkedIn.

## 3. Research Objectives

### 3.1 Primary Research Question

**How does the structure of a population's social network influence the transmission of an infectious disease, and how effective are different interventions in controlling an outbreak?**

### 3.2 Supporting Research Questions

1. How do deterministic compartmental models compare with stochastic network-based epidemic simulations?
2. How does network topology influence outbreak size, peak infections, and duration?
3. Do densely connected populations experience faster or more severe outbreaks?
4. How do random, small-world, scale-free, and community-based networks differ in their transmission patterns?
5. How effective are vaccination, isolation, and reduced social contact under different network conditions?
6. Can targeted vaccination based on network centrality outperform random vaccination?
7. How much variability exists between repeated outbreaks under identical model parameters?

### 3.3 Project Objectives

The project aims to:

- Develop a mathematical understanding of fundamental epidemiological models.
- Implement a deterministic SIR simulation.
- Construct stochastic network-based epidemic models.
- Apply graph theory to represent and analyze social interactions.
- Design controlled experiments to compare outbreak behaviour.
- Evaluate selected public health interventions.
- Use Monte Carlo methods to quantify uncertainty.
- Produce informative visualizations and animated simulations.
- Communicate findings through a reproducible computational notebook and technical portfolio presentation.

## 4. Technical Methodology

### 4.1 Compartmental Epidemiological Modelling

The first component will implement the Susceptible–Infected–Recovered (SIR) model.

The population will be divided into three compartments:

- **Susceptible (S):** Individuals who can contract the disease.
- **Infected (I):** Individuals currently carrying and transmitting the disease.
- **Recovered (R):** Individuals who have recovered and are assumed immune for the duration of the simulation.

The deterministic model will be described using ordinary differential equations:

\[
\frac{dS}{dt}=-\beta\frac{SI}{N}
\]

\[
\frac{dI}{dt}=\beta\frac{SI}{N}-\gamma I
\]

\[
\frac{dR}{dt}=\gamma I
\]

Where:

- \(N\) represents the total population.
- \(\beta\) represents the effective transmission rate.
- \(\gamma\) represents the recovery rate.
- \(R_0=\beta/\gamma\) represents the basic reproduction number under the model's assumptions.

Python and SciPy will be used to numerically solve the system.

The resulting epidemic curves will provide a baseline against which network-based simulations can be evaluated.

An SEIR extension, introducing an exposed population, may be explored if the core implementation is completed ahead of schedule.

### 4.2 Network-Based Epidemic Simulation

The second component will represent the population as a graph.

Each individual will be represented by a node, while edges will represent potential disease-transmitting social interactions.

Individuals will transition between epidemiological states based on stochastic infection and recovery rules.

Four network structures are proposed for investigation:

| Network Type | Description | Research Significance |
|---|---|---|
| Random network | Connections are formed probabilistically | Establishes a baseline for relatively unstructured contact patterns |
| Small-world network | High local clustering with occasional long-distance connections | Represents clustered communities connected by shortcuts |
| Scale-free network | Highly unequal connectivity with prominent hub nodes | Investigates the influence of highly connected individuals |
| Community-based network | Individuals form groups with stronger internal connections | Examines localized outbreaks and cross-community transmission |

NetworkX will be used to generate, analyze, and visualize the graphs.

Relevant network characteristics will include degree distribution, average degree, clustering, connected components, and selected centrality measures.

Comparisons will account for differences in network size and connectivity to avoid attributing effects to topology that arise from unrelated parameter changes.

### 4.3 Stochastic Disease Transmission

Unlike deterministic SIR models, the network simulation will incorporate randomness into individual infection and recovery events.

At each simulation step, infected individuals may transmit the disease to susceptible neighbours according to a specified probability.

Infected individuals may also recover according to a recovery probability or an explicitly defined infectious-period distribution.

The simulation will track the epidemiological state of every individual over time.

The project will investigate how identical initial conditions can produce different outbreak outcomes because of stochastic variation.

Transmission probabilities, recovery assumptions, time-step definitions, and their relationship to the compartmental model will be documented.

### 4.4 Public Health Intervention Experiments

Selected intervention strategies will be introduced into the network simulations.

**Random vaccination:** A randomly selected proportion of individuals will be immunized before the outbreak.

**Targeted vaccination:** Individuals with high network connectivity or centrality will be prioritized for vaccination.

**Isolation:** Infected individuals will have some or all of their transmission-capable connections temporarily removed or disabled.

**Reduced social contact:** The number or frequency of potentially infectious interactions will be decreased.

Each intervention will be evaluated against a no-intervention baseline.

Where appropriate, interventions will be tested at multiple intensity levels.

The experiments will investigate whether intervention effectiveness varies according to network structure.

### 4.5 Monte Carlo Experimentation

Repeated simulations will be conducted to quantify variability in outbreak outcomes.

For each selected experimental condition, multiple simulation runs will be performed using controlled random seeds.

Results will be aggregated to calculate:

- Mean and median outbreak size.
- Peak infected population.
- Time to peak infection.
- Outbreak duration.
- Total proportion of the population infected.
- Probability of a major outbreak, using a predefined threshold.
- Variability and uncertainty across simulation runs.

Monte Carlo analysis will help distinguish consistent patterns from isolated simulation outcomes.

The number of repetitions will be selected based on computational feasibility and the precision required for meaningful comparisons.

### 4.6 Model Comparison and Interpretation

The deterministic SIR model and stochastic network simulations will be compared using clearly documented assumptions.

The comparison will focus on differences in population mixing, transmission mechanisms, outbreak variability, and the effects of contact structure.

Because the models represent transmission differently, parameter values will not be assumed directly equivalent without appropriate calibration.

The objective is not to declare one modelling approach universally superior, but to understand the questions each model can answer and the limitations of its assumptions.

## 5. Experimental Design

The project will follow a hypothesis-driven experimental approach.

Initial hypotheses may include:

**H1 — Network structure:** Populations with different network topologies will exhibit different outbreak trajectories even when population size and approximate contact density are controlled.

**H2 — Network hubs:** Targeted vaccination of highly connected individuals will reduce outbreak size more effectively than random vaccination in networks with strongly unequal degree distributions.

**H3 — Community structure:** Strong community boundaries will influence the timing and distribution of infections across population groups.

**H4 — Stochastic variation:** Repeated simulations with identical parameters will produce a distribution of outbreak outcomes rather than a single deterministic trajectory.

**H5 — Intervention intensity:** Increasing intervention coverage will generally reduce transmission opportunities, although the magnitude of improvement may vary by network structure.

Hypotheses will be refined during the planning stage.

Experimental parameters will be controlled wherever possible, and findings will be interpreted in relation to the assumptions and limitations of the simulated environment.

## 6. Technical Stack

| Technology | Intended Purpose |
|---|---|
| Python | Primary programming language |
| Jupyter Notebook | Main development, experimentation, and documentation environment |
| NumPy | Numerical operations and random sampling |
| SciPy | Differential equation solving and mathematical computation |
| NetworkX | Graph generation, network analysis, and contact-network modelling |
| Pandas | Experiment results and statistical aggregation |
| Matplotlib | Scientific charts and simulation animations |
| Plotly | Optional interactive visualizations |
| Tableau Public | Optional shareable analytical dashboard |
| VS Code | Local development environment |
| Git and GitHub | Version control and portfolio publication |
| Codex | AI-assisted implementation, debugging, and testing |

The project will favour established Python libraries and lightweight local execution.

No database, authentication system, backend API, or dedicated frontend framework is required for the initial version.

## 7. Project Architecture and File Organization

Patient Zero will follow a notebook-first development approach.

The primary objective is to maintain a simple, readable project structure that supports experimentation without unnecessary fragmentation.

### Proposed Repository Structure

```text
patient-zero/
├── Patient_Zero.ipynb
├── README.md
├── requirements.txt
└── outputs/
    ├── figures/
    ├── animations/
    └── data/
```

The output directories will be created only when required.

### Main Jupyter Notebook

The notebook will serve as the central project artifact, combining mathematical explanations, executable Python code, experimental results, visualizations, and conclusions.

Proposed sections:

1. Introduction and research questions
2. Epidemiological foundations
3. Deterministic SIR implementation
4. Network generation and structural analysis
5. Stochastic transmission simulation
6. Intervention experiments
7. Monte Carlo analysis
8. Model comparison
9. Visualizations and findings
10. Limitations and future research

Markdown cells will explain the purpose and reasoning behind each implementation.

Python cells will contain the associated computations and visualizations.

The notebook will be organized for sequential execution and must run successfully from beginning to end.

Additional Python modules will be introduced only if a demonstrated technical requirement justifies them.

## 8. Visualization and Presentation Strategy

The visualization component will focus on communicating simulation behaviour and experimental findings.

### 8.1 Simulation Visualizations

Potential outputs include:

- Animated transmission through contact networks.
- Nodes changing colour according to epidemiological state.
- Time-series plots of susceptible, infected, and recovered populations.
- Side-by-side comparisons of network structures.
- Visual demonstrations of intervention effects.
- Animated progression of outbreaks through community networks.

### 8.2 Statistical Visualizations

Potential analytical outputs include:

- Infection curves.
- Outbreak-size distributions.
- Intervention effectiveness comparisons.
- Network-property comparisons.
- Monte Carlo uncertainty intervals.
- Peak infection and outbreak-duration comparisons.

### 8.3 Optional Tableau Public Dashboard

A Tableau Public dashboard may be developed to present aggregated experimental findings.

Possible features include filters for network type, intervention strategy, and simulation parameters.

The dashboard will be considered an optional presentation enhancement rather than a core development dependency.

The final presentation will emphasize scientific interpretation and technical transparency over decorative interface design.

## 9. Development Philosophy and Division of Responsibilities

A central objective of Patient Zero is to maintain active intellectual involvement throughout the development process.

The project will use AI-assisted development while ensuring that conceptual understanding, experimental decisions, and interpretation remain primarily human-directed.

### 9.1 Project Owner — Researcher and Technical Decision-Maker

**Primary responsibilities:**

- Define and refine research questions.
- Understand the mathematical foundations.
- Select modelling assumptions and parameters.
- Develop hypotheses.
- Evaluate algorithmic alternatives.
- Make final technical and scope decisions.
- Predict experimental outcomes.
- Interpret simulation results.
- Investigate unexpected findings.
- Explain the methodology independently.
- Determine which results are meaningful enough to publish.

The project owner will not be expected to manually write every line of code, but should understand the purpose, behaviour, and limitations of the implemented components.

### 9.2 ChatGPT — Technical Mentor and Research Collaborator

**Primary responsibilities:**

- Facilitate brainstorming and scope refinement.
- Explain mathematical and computational concepts.
- Help compare modelling approaches.
- Review proposed algorithms and assumptions.
- Assist with experimental design.
- Challenge unsupported conclusions.
- Explain errors and unexpected behaviour.
- Review technical accuracy.
- Support interpretation and documentation.

ChatGPT should encourage reasoning and independent problem-solving rather than immediately producing extensive implementation instructions.

Where appropriate, conceptual questions and small exercises should precede major coding tasks.

### 9.3 YouTube and Educational Resources — Supplementary Learning

**Primary responsibilities:**

- Provide visual explanations of unfamiliar concepts.
- Support understanding of differential equations, graph theory, and stochastic simulation.
- Demonstrate relevant mathematical or computational techniques.

Educational resources will be used selectively.

The project will not be built by reproducing a complete tutorial line by line.

### 9.4 Codex — AI Coding Assistant

**Primary responsibilities:**

- Assist with implementing clearly defined algorithms.
- Help write and debug Python code.
- Support unit testing and validation.
- Refactor code where necessary.
- Assist with plotting and animation.
- Improve code readability and reproducibility.
- Help prepare technical documentation.

Codex should implement decisions established through prior reasoning rather than independently determine the project's direction.

### 9.5 Learning and Collaboration Principles

The following principles will guide development:

1. Understand unfamiliar concepts before implementing them.
2. Formulate hypotheses before conducting experiments.
3. Attempt to reason through major algorithms independently.
4. Use AI to support technical work rather than replace technical judgement.
5. Review and understand AI-generated code.
6. Avoid unnecessary infrastructure and abstraction.
7. Prefer controlled experiments over visually impressive but poorly justified results.
8. Investigate unexpected outcomes rather than modifying models solely to obtain desirable results.
9. Document assumptions and limitations transparently.
10. Maintain a strict focus on the seven-day project scope.

A short independent reasoning period, approximately 15 minutes when appropriate, will be encouraged before delegating major implementation tasks.

## 10. Seven-Day Development Plan

| Day | Phase | Key Activities | Expected Deliverable |
|---|---|---|---|
| 1 | Research and planning | Refine hypotheses, understand mathematical foundations, select parameters and experiments | Finalized research design |
| 2 | SIR modelling | Implement differential equations, solve numerically, visualize epidemic curves | Working deterministic baseline |
| 3 | Network simulation | Generate networks, analyze topology, implement stochastic transmission | Working network-based outbreak simulation |
| 4 | Interventions | Implement selected intervention strategies and controlled experiments | Intervention comparison framework |
| 5 | Monte Carlo analysis | Run repeated experiments, aggregate results, evaluate uncertainty | Statistical findings and comparison tables |
| 6 | Visualization | Produce animations, charts, and optional Tableau dashboard | Portfolio-ready visualizations |
| 7 | Validation and publication | Test reproducibility, finalize notebook, document methodology, prepare GitHub presentation | Completed portfolio project |

The schedule represents a target rather than a guarantee.

If implementation complexity exceeds expectations, optional functionality will be deferred instead of expanding the project indefinitely.

## 11. Scope Management

### Minimum Viable Research Project

The following components are considered essential:

- Working deterministic SIR model.
- Working stochastic network-based SIR simulation.
- At least two distinct network structures.
- At least one intervention strategy.
- Repeated simulation experiments.
- Quantitative comparison of outcomes.
- At least one animated visualization.
- Reproducible Jupyter Notebook.
- Documented findings and limitations.
- GitHub-ready README.

### Extended Scope

Subject to available time:

- All four proposed network structures.
- Multiple intervention strategies.
- Centrality-based vaccination.
- SEIR model extension.
- Additional sensitivity analyses.
- Advanced interactive visualizations.
- Tableau Public dashboard.

### Out of Scope

The following are excluded from the initial project:

- Full-stack web application development.
- User authentication and account management.
- Persistent database infrastructure.
- Real-time public health data integration.
- Production-grade epidemiological forecasting.
- Geographic disease surveillance.
- Complex cloud deployment.
- Claims of clinical or policy validity without external validation.

Patient Zero is an educational and computational research simulation, not a validated public health forecasting system.

## 12. Validation and Success Criteria

The project will be considered technically successful when:

- The deterministic SIR model behaves consistently with its mathematical assumptions.
- The simulated population is conserved under the defined closed-population model.
- Infection and recovery transitions obey the implemented rules.
- Network generation is reproducible using controlled random seeds.
- Simulation outcomes can be replicated.
- Intervention experiments use consistent comparison conditions.
- Results are supported by appropriate quantitative metrics.
- Monte Carlo summaries accurately reflect repeated runs.
- The notebook executes successfully from a clean kernel.
- The final documentation explains the models, assumptions, findings, and limitations.

The project will be considered educationally successful when the project owner can independently explain the modelling choices, key algorithms, experimental results, and major limitations.

## 13. Risks and Mitigation Strategies

| Risk | Mitigation |
|---|---|
| Scope expansion beyond seven days | Prioritize minimum viable research objectives |
| Excessive computational runtime | Begin with smaller populations and benchmark performance |
| Misleading comparisons between models | Document assumptions and calibrate parameters appropriately |
| High stochastic variability | Use repeated trials and report uncertainty |
| Unreliable simulation logic | Validate transitions, conservation, and edge cases |
| Excessive reliance on AI-generated code | Require conceptual understanding and active technical review |
| Overcomplicated file organization | Maintain a notebook-first structure |
| Excessive time spent on visualization | Complete core experiments before presentation enhancements |

## 14. Final Deliverables

The intended final outputs are:

1. **Patient_Zero.ipynb:** A complete computational research notebook containing theory, implementation, experiments, and conclusions.
2. **README.md:** A concise, polished technical overview suitable for GitHub.
3. **Simulation Animations:** Visual demonstrations of disease transmission.
4. **Statistical Visualizations:** Comparative charts and uncertainty analysis.
5. **Experimental Results:** Reproducible aggregated simulation outputs.
6. **Optional Tableau Dashboard:** An interactive presentation of experimental findings.
7. **LinkedIn Project Showcase:** A short technical narrative accompanied by selected visualizations or a demonstration video.

## 15. Portfolio and Publication Strategy

Patient Zero is the introductory project in a five-part technical portfolio series:

| Order | Project | Primary Technical Focus |
|---|---|---|
| 01 | Patient Zero | Epidemiological modelling, graph theory, stochastic simulation |
| 02 | Puzzle Solver | Constraint satisfaction, search algorithms, graph traversal |
| 03 | Snake AI | Deep reinforcement learning and sequential decision-making |
| 04 | NFL Motion Intelligence | Computer vision, object tracking, spatial analytics |
| 05 | Digital Ecosystem | Agent-based modelling, emergent behaviour, ecological simulation |

Each project will aim to demonstrate a different computational approach while maintaining a consistent emphasis on experimentation, technical understanding, and clear communication.

Patient Zero will establish the initial documentation and publication format for the series.

The LinkedIn presentation will emphasize the research question, methodology, experimental findings, visual demonstrations, and lessons learned rather than simply announcing that a project was completed.

## 16. Conclusion

Patient Zero is intended to be a focused exploration of how mathematical models, graph structures, and stochastic processes can be combined to study complex population-level behaviour.

The project will demonstrate the practical application of epidemiological modelling, graph theory, computational simulation, experimental design, and statistical analysis within a manageable seven-day development cycle.

Its success will be measured not only by the completion of working simulations and polished visualizations, but also by the depth of technical understanding gained through the process.

**The guiding principle is to build a project that is understood, experimentally justified, reproducible, and thoughtfully presented, rather than simply a project that works.**

---

**Project Status:** Proposal / Pre-Implementation  
**Next Milestone:** Finalize research hypotheses, essential network structures, intervention scenarios, and experimental parameters before beginning implementation.