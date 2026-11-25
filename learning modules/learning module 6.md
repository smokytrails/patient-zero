# LEARNING MODULE 6

## 1. What is an Experiment?
- independent variables:
    - network topology
    - initial infected percentage
    - transmission rate
    - recovery rate
    - vaccination strategy
    - vaccination coverage
- dependent variables (outbreak information)
    - peak infected
    - final outbreak size
    - outbreak duration
- controlled variables (population)

## 2. Replication and Experimental Uncertainty
- even when all experimental settings are the same, there's no certainty that the outcomes won't differ
- our eventual Monte Carlo repetitions per configuration will help estimate average outcomes and quantify uncertainty

## 3. Baseline
- no-vaccination baseline for every topology and disease parameter combination
- we compare vaccination strategy and coverage effectiveness using the following formula (where the "sizes" are the mean final outbreak size):

    $Reduction (\%) = (Baseline \ Size - Intervention \ Size) \times 100 \ / \ Baseline \ Size$

## 4. Random vs Degree-targeted Vaccination
- with vaccinations:
    - S: susceptible
    - I: infected
    - R: 
        - recovered
        - vaccinated $\rightarrow$ complete protection against infection
- even though we're placing vaccinated individuals within the R category, we need to track them separately to maintain the integrity of the final recovered count
- vaccination methods:
    - random vaccination:
        - easy to implement
        - no knowledge of network structure required
        - useful baseline for more sophisticated strategies
    - degree-targeted vaccination:
        - prioritizes individuals with highest number of connections
        - requires information about the contact network
        - doesn't take into account contact frequency, contact duration, etc.

## 5. Vaccination Coverage
- proportion of the total population vaccinated
- coverage levels:
    - $0\%$
    - $10\%$
    - $20\%$
    - $30\%$
- random and targeted vaccinations need to be compared for the same coverage level

## 6. Design Issues and Considerations
- we choose initial infected individuals after choosing who's vaccinated - pre-outbreak vaccination scenario
- we also need to distinguish vaccinated and naturally recovered individuals

## 7. Experimental Hypotheses
- H1: vaccination coverage
- H2: vaccination strategy
- H3: network topology

