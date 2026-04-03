# SIM-ANALYSIS — Software Project Failure Simulator

An interactive simulation platform that models how software 
engineering decisions compound into project outcomes over time.

Built as an educational tool for students and early-stage developers to 
develop intuition for project management trade-offs — not through 
textbooks, but by watching failure happen in real time.

## What it does

**Simulator**
Models a 52-week software project as a weighted dependency graph of 8 
modules. Bugs spread between nodes as a contagion — probability driven 
by module coupling, edge weight, and test coverage. Six parameters 
control team productivity, burnout, code stability, and feature velocity.

**Monte Carlo Analysis**
Runs stochastic simulations with parameter noise, producing 
distributional outcomes: success rates, 90% confidence intervals, 
stability trajectories (best/median/worst), and a Bug Propagation 
Network showing which modules are structurally most vulnerable across 
the full probability space.

**Genetic Algorithm Optimizer**
Searches the parameter space for Pareto-optimal configurations — 
combinations where you cannot improve stability without sacrificing 
features, or vice versa. Outputs a fitness convergence chart and 
Pareto frontier with predicted outcomes validated against 100 Monte 
Carlo runs.

## Key concepts modelled

- Bug spread via SIR epidemiological model across a dependency graph
- Logistic sigmoid curve for burnout-productivity collapse
- Quadratic tech debt penalty (compounding, not linear)
- Super-linear bug generation rate with tech debt
- Brooks' Law: diminishing returns on team size (square root above 12)
- Pareto optimality across stability, features, burnout, and bugs

## Scenarios included

| Scenario       | Pressure | Test Coverage | Tech Debt | Coupling |
|----------------|----------|---------------|-----------|----------|
| Startup Crunch | 90%      | 20%           | 60%       | 70%      |
| Enterprise     | 40%      | 80%           | 20%       | 30%      |
| Agile + TDD    | 50%      | 90%           | 15%       | 40%      |
| Legacy System  | 70%      | 30%           | 80%       | 85%      |

## Tech stack

- Vanilla HTML/CSS/JavaScript — no framework, no build step
- D3.js v7 — force-directed graph, all charts
- system-dynamics-sim.js — standalone simulation engine (importable)

## Run it

Just open index.html in a browser. No installation required.

## Files

index.html              → full application (simulator + Monte Carlo + optimizer)
system-dynamics-sim.js  → standalone SimulationEngine class (reusable)
