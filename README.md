# Backtracking Search Algorithm (BSA) — Metaheuristic Optimization

A from-scratch **NumPy** implementation of the **Backtracking Search Algorithm (BSA)**, an evolutionary metaheuristic for continuous global optimization, benchmarked on four standard test functions with a rigorous multi-run statistical protocol.

---

## Overview

BSA is a population-based evolutionary optimizer that uses a **historical population** (memory of a previous generation) to guide the search, combined with mutation, a crossover step controlled by a mix-rate, boundary handling, and greedy selection. This project implements each component manually and evaluates the algorithm across a suite of well-known benchmark landscapes.

---

## Benchmark Functions

| Function | Characteristics | Search bounds |
|----------|-----------------|---------------|
| **Ackley** | Many local minima, near-flat outer region | [-32.768, 32.768] |
| **Rastrigin** | Highly multimodal, regular minima | [-5.12, 5.12] |
| **Schwefel** | Deceptive, global optimum far from local ones | [-500, 500] |
| **Rosenbrock** | Narrow curved valley (banana function) | [-5, 10] |

Each has a known global optimum, allowing convergence quality to be measured directly.

---

## Algorithm Components

- **`init_population`** — random uniform initialization within bounds.
- **Historical population** — a shuffled previous generation that steers the search direction.
- **`mutation`** — perturbs individuals using a scaled difference between the current and historical populations.
- **`crossover`** — a mix-rate-controlled binary map that selectively combines mutant and parent components.
- **`boundary_control`** — re-samples components that leave the feasible region.
- **Greedy selection** — keeps a trial individual only if it improves fitness; tracks the running global best.

---

## Experimental Protocol

| Parameter | Value |
|-----------|-------|
| Dimensions | 30 |
| Population size | 30 |
| Max evaluations | 20,000 |
| Independent runs per function | 30 |
| Mix-rate | 1 |

For each function the script runs **30 independent trials** and reports the **mean** and **standard deviation** of the achieved global minima, along with **total and average runtime** — a statistically sound evaluation that captures both solution quality and computational cost.

---

## Repository Contents

```
.
├── Meta-heuristic_Code.py     # BSA implementation + benchmark experiments
├── Meta-heuristic_Report.docx # Project report and analysis
└── README.md
```

---

## Getting Started

### Prerequisites

```bash
pip install numpy
```

### Run

```bash
python Meta-heuristic_Code.py
```

The script optimizes each benchmark function across 30 runs and prints per-run results followed by aggregate statistics (mean, standard deviation, and runtime).

---

## Author

[Nurlan Abdullazada](https://github.com/nurlan-abdullazada)
