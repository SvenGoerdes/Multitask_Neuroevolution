# Multitask Neuroevolution: NEAT vs. HA-NEAT on Brax Locomotion

Code for the master's thesis *"Heterogeneous Activation NEAT for Multi-Task Continuous Control"* (Sven Goerdes, NOVA IMS, MDSAA / Data Science). This repository is a fork of [TensorNEAT](https://github.com/EMI-Group/tensorneat) (GPU-accelerated NEAT in JAX, EMI-Group) extended with:

- **HA-NEAT** — Heterogeneous Activation NEAT: nodes can carry different activation functions, with activation mutation protected by historical-marker reassignment and speciation.
- **Multi-task Brax evaluation** — a *single* evolved network is evaluated on **Hopper and Walker2D simultaneously**, using zero-padded observations and sliced actions, with normalized fitness aggregation.
- **Experiment tooling** — a config-driven grid runner, MLflow tracking, genome re-evaluation, plotting, and statistical analysis scripts.

## Research question

Does activation-function heterogeneity (HA-NEAT) help a single network solve multiple continuous-control tasks compared to standard NEAT (tanh only)? Three conditions are compared:

| Condition | Algorithm | Activations | Notes |
|---|---|---|---|
| Baseline | NEAT | tanh only | Standard mutation |
| Treatment | HA-NEAT | tanh, sigmoid, relu, sin, identity | Historical-marker reassignment, speciation protection |
| Ablation | HA-NEAT (tanh only) | tanh only | Tests whether activation diversity is the active ingredient |

**Environments:** Hopper (11 obs, 3 act) + Walker2D (17 obs, 6 act). The network is sized to the largest task (17 inputs → 6 outputs); Hopper observations are zero-padded and its actions sliced. Default fitness aggregation is `normalized_min` = `min(norm_hopper, norm_walker2d)`, which forces improvement on the weakest task.

## What the fork adds (code)

| Component | Location |
|---|---|
| `HANEATMutation` (activation mutation + marker reassignment) | `src/tensorneat/genome/operations/mutation/ha_neat.py` |
| `OriginConn` / origin node genes (historical markers) | `src/tensorneat/genome/gene/conn/origin.py`, `.../node/origin.py` |
| `MultiTaskBraxEnv`, `TaskSpec`, fitness aggregators (`NormalizedMin`, `NormalizedWeightedSum`, …) | `src/tensorneat/problem/rl/multi_task.py` |
| Pipeline with MLflow + per-task fitness tracking | `src/tensorneat/pipeline.py` |
| Git-state capture into saved genomes | `src/tensorneat/common/git_state.py` |
| Config-driven experiment grid runner | `main.py` + `config*.yaml` |
| Genome re-evaluation & visualization | `eval/` |
| Main-study analysis (stats, curves, complexity) | `analysis/`, `text/figures/` |
| Tests for aggregation and origin genes | `test/` |

## Installation

Requires Python ≥ 3.10. Uses [uv](https://docs.astral.sh/uv/) as package manager.

```bash
uv pip install -e .
uv run pytest test/
```

Key dependencies: `jax`, `brax`, `mujoco-mjx`, `gymnax`, `flax`, `optax`, `networkx`, `sympy`, `mlflow`.

## Running experiments

```bash
uv run python main.py --config config.yaml
```

- Any list-valued key in the config (e.g. `pop_size: [1024, 2048]`, `seed: [42, 123]`) becomes a Cartesian sweep dimension.
- `--skip-existing` resumes a grid by skipping runs whose result `.npz` already exists; `--shard i/N` splits the grid across parallel launches.
- Use the `mjx` backend (default). `generalized` is faster but lets Walker2D exploit floor penetration.
- Each run logs per-generation metrics to MLflow (`mlflow.db`, SQLite) — per-task raw and normalized fitness, species count, genome complexity. View with:

```bash
mlflow ui --backend-store-uri sqlite:///mlflow.db
```

Best genomes are saved to `results/<experiment_name>/<run_name>.npz` (nodes, connections, fitness, git state, full run config).

## Evaluation & analysis workflow

Training fitness is a single stochastic episode per genome, so reported numbers always come from re-evaluation over multiple episodes:

```bash
# 1. Re-evaluate saved genomes (30 episodes, mjx backend) → eval/outputs/*.json
uv run python eval/evaluate_genomes.py --results_dir results/<experiment> --n_eval 30 --backend mjx

# 2. Training curves from MLflow
uv run python text/figures/plot_training_curves.py --experiment_name <experiment> --db_path mlflow.db

# 3. Re-evaluation bar charts
uv run python text/figures/plot_evaluation_results.py --input eval/outputs/<file>.json

# 4. Statistics (Mann-Whitney U, permutation test, Cohen's d)
uv run python text/figures/statistical_test.py --input eval/outputs/<file>.json --algo_a neat --algo_b ha_neat
```

The thesis's primary experiment ("main study": population 200, 750 generations, 30 seeds × 3 conditions) has its dedicated analysis pipeline in `analysis/` (`report_pop200.py`, `training_curves_pop200.py`, `network_complexity_pop200.py`, …) driven by `config_pop200.yaml`.

## Repository layout

```
main.py                  # config-driven experiment grid runner
config.yaml              # current experiment config (+ config_*.yaml variants)
src/tensorneat/          # library — Pipeline > Algorithm > Genome > Problem
  pipeline.py            #   setup/step/auto_run + MLflow tracking
  algorithm/neat/        #   NEAT with SpeciesController
  genome/                #   genes, mutations (incl. HANEATMutation), crossover, distance
  problem/rl/            #   BraxEnv, MultiTaskBraxEnv, gymnax
  common/                #   activation/aggregation functions, State, git_state
eval/                    # batch re-evaluation of .npz genomes → JSON
results/                 # best genomes per run (.npz, gitignored)
analysis/                # main-study analysis scripts + outputs
text/figures/            # plotting + statistical test scripts
test/                    # pytest suite (aggregation, origin genes)
docs/FEATURE_LOG.md      # chronological log of implemented features
REFERENCE.md             # detailed internals (HA-NEAT mechanism, aggregation, pipeline)
thesis/                  # master's thesis LaTeX; final PDF builds from thesis/nova/ (NOVA-IMS template)
```

## Upstream: TensorNEAT

All GPU-accelerated NEAT infrastructure comes from [TensorNEAT](https://github.com/EMI-Group/tensorneat) (GECCO 2024 Best Paper Award, [arXiv:2404.01817](https://arxiv.org/abs/2404.01817)). If you use this code, please cite:

```bibtex
@article{10.1145/3730406,
  author = {Wang, Lishuang and Zhao, Mengfei and Liu, Enyu and Sun, Kebin and Cheng, Ran},
  title = {TensorNEAT: A GPU-accelerated Library for NeuroEvolution of Augmenting Topologies},
  year = {2025},
  publisher = {Association for Computing Machinery},
  url = {https://doi.org/10.1145/3730406},
  doi = {10.1145/3730406},
  journal = {ACM Trans. Evol. Learn. Optim.},
  month = apr
}
```

HA-NEAT is based on Hagg et al. (2017), *Evolving Parsimonious Networks by Mixing Activation Functions*; NEAT on Stanley & Miikkulainen (2002).

## License

GNU General Public License v3.0 — see [LICENSE](LICENSE) (inherited from upstream TensorNEAT).
