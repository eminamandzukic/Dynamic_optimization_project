# Inventory-Constrained Dynamic Auction Optimization

A Python simulation for studying **dynamic bidding decisions under inventory constraints**. The project investigates how a purchasing agent can control costs while maintaining minimum stock levels across repeated auctions involving milk/dairy, eggs, poultry, and beef.

## Project overview

In each auction round, an agent chooses whether to bid for available products. Its decisions depend on current inventory, available quantities, competitor behavior, and replenishment costs. The goal is to balance **inventory safety** against **purchasing costs** as market conditions evolve.

The project compares the following approaches:

| Approach | Information available | Method |
| --- | --- | --- |
| **All-Seeing Agent** | Observes competitor bids | Lyapunov drift-plus-penalty bidding |
| **Partially-Blind Agent** | Observes competitor inventories but not their bids | Lyapunov bidding with online price estimates from incremental ordinary least squares (OLS) |
| **Offline ILP Benchmark** | Uses future prices and quantities | Integer linear programming reference solution |

The simulation also models different competitor strategies and tracks inventory, cumulative spending, auction wins, and inventory constraint violations.

## Features

- Multi-product auction simulation with inventory depletion and minimum stock thresholds
- Two online bidding strategies under different information assumptions
- Offline optimization benchmark for comparison
- Synthetic simulation data, with optional Eurostat agricultural data preprocessing
- Interactive **Streamlit dashboard** for configuring experiments and visualizing outcomes
- Command-line experiments, saved plots, and run summaries

## Technologies

**Python · NumPy · pandas · SciPy · Matplotlib · Plotly · Streamlit**

## Getting started

Clone the repository and move into the project directory:

```bash
git clone https://github.com/eminamandzukic/Dynamic_optimization_project.git
cd Dynamic_optimization_project/dynamic-auction-optimizer-main
```

Create a virtual environment and install dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

### Interactive dashboard

```bash
streamlit run app.py
```

### Command-line experiments

Compare the two online agents and generate plots:

```bash
python -m scripts.run --compare --n_rounds 150 --plot
```

Run a single agent:

```bash
python -m scripts.run --mode partially_blind --n_rounds 150
```

Outputs are saved in timestamped folders under `results/`. Eurostat input files are optional; the basic simulation can run with fallback data.

For other command-line options, hyperparameters, and algorithmic details, consult the [technical README](dynamic-auction-optimizer-main/README.md).

## Repository structure

| Path | Purpose |
| --- | --- |
| [`Project_report.pdf`](Project_report.pdf) | Full project report |
| [`dynamic-auction-optimizer-main/`](dynamic-auction-optimizer-main/) | Application source code |
| [`agents/`](dynamic-auction-optimizer-main/agents/) | Bidding agents, competitor strategies, and ILP benchmark |
| [`env/`](dynamic-auction-optimizer-main/env/) | Auction simulation environment |
| [`scripts/run.py`](dynamic-auction-optimizer-main/scripts/run.py) | Command-line experiment runner |
| [`app.py`](dynamic-auction-optimizer-main/app.py) | Streamlit application |

## Further documentation

See the [project report](Project_report.pdf) for the project write-up and the [technical README](dynamic-auction-optimizer-main/README.md) for implementation details, mathematical formulations, data sources, and experiment settings.
