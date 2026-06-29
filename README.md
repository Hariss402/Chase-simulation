# Dynamic Chase Simulation Framework

A configurable **pursuit-evasion simulation framework** built from scratch in Python that models a dynamic police chase on a directed weighted graph. The simulator incorporates adaptive path planning, changing road conditions, and real-time decision making using **Dijkstra's shortest path algorithm implemented from scratch**.

Unlike many graph-based projects, the core pathfinding and simulation logic is implemented using **only Python's standard library**, without relying on external graph algorithm libraries.

---

## Overview

The simulator models a city as a directed weighted graph where:

* **Car A (Burglars)** attempts to escape by reaching an exit node using the shortest available route.
* **Car B (Police)** joins the chase after a delay and continuously adapts its route to intercept the burglars.
* Dynamic road events such as traffic congestion, temporary road blockages, and one-way restrictions force both vehicles to recompute their routes during the simulation.

Each simulation produces a complete step-by-step execution log, enabling further analysis and experimentation.

---

## Features

* Directed weighted graph simulation
* Dijkstra's shortest path algorithm implemented from scratch
* Dynamic path replanning during runtime
* Traffic congestion events with temporary edge weight increases
* Temporary road blockages
* Temporary one-way road restrictions
* Adaptive police pursuit strategy
* Detailed simulation logging in JSON format
* The analysis was done over 1000 independent simulation runs

---

## Simulation Workflow

```text
Load Graph
    │
    ▼
Initialize Vehicles
    │
    ▼
Compute Initial Paths
    │
    ▼
Simulation Loop
    │
    ├── Move Car A
    ├── Move Car B
    ├── Generate Dynamic Events
    ├── Resolve Expired Events
    ├── Recompute Shortest Paths
    ├── Check Capture / Escape
    └── Save Current State
    │
    ▼
End Simulation
```

---

## Dynamic Road Events

During every timestep, the environment may change through randomly generated events.

| Event               | Effect                                  | Duration    |
| ------------------- | --------------------------------------- | ----------- |
| Traffic Jam         | Temporarily increases edge weight       | 3 timesteps |
| Road Blockage       | Temporarily removes an edge             | 4 timesteps |
| One-way Restriction | Removes the reverse direction of a road | 6 timesteps |

Whenever these events occur, both vehicles adapt their routes according to their individual decision-making strategies.

---

## Output

Each execution generates a `simulation.json` file containing the complete simulation history.

For every timestep, the simulator records:

* Current position of both vehicles
* Current edge traversal progress
* Dijkstra path being followed
* Active dynamic events
* Capture status
* Escape status

This structured output makes it easy to perform further analysis or build visualizations on top of the simulation engine.

---

## Statistical Analysis

Beyond individual simulations, the framework was executed **1000 independent times** to estimate overall system behaviour.

The collected statistics include:

* Police interception rate
* Burglar escape rate
* Average chase duration

Running the simulation repeatedly transforms the project from a single chase scenario into a reusable experimentation framework for studying pursuit-evasion behaviour under dynamic environments.

---

## Repository Structure

```text
.
├── Chase_simulation.ipynb      # Complete simulation implementation
├── graph_with_metadata.json    # Directed weighted city graph
├── simulation.json             # Example output generated after one simulation run
├── README.md
```

---

## Technologies Used

* Python
* Standard Library

  * json
  * random

No external graph-processing or pathfinding libraries were used for the implementation of the simulation or Dijkstra's algorithm.

---

## Possible Extensions

The framework has been intentionally designed so additional functionality can be added without modifying the core simulation engine.

Possible future improvements include:

* Interactive graph visualization
* Web-based user interface
* Multiple police vehicles
* Multiple escape vehicles
* Heatmaps showing high-risk regions
* Reinforcement learning agents
* Strategic police station placement analysis
* Traffic policy experiments
* Performance benchmarking on larger graphs

---

## Learning Outcomes

This project provided hands-on experience with:

* Graph data structures
* Shortest path algorithms
* Dynamic graph modifications
* Event-driven simulation
* Pursuit-evasion systems
* Monte Carlo experimentations
* JSON-based simulation logging

---

## Running the Project

Clone the repository and open the notebook.

```bash
git clone <repository-url>
cd <repository-folder>
```

Open:

```text
Chase_simulation.ipynb
```

and execute the notebook from top to bottom.

The simulation will generate a fresh `simulation.json` file after every run.
