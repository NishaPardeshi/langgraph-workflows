
# LangGraph Workflows (Notebook Collection)
<img width="1536" height="1024" alt="langgraph" src="https://github.com/user-attachments/assets/e3c94519-aefb-411a-a29a-e0e1ab3471ba" />

This workspace demonstrates several small workflow patterns implemented with a `StateGraph` style orchestration. Each example is provided as a Jupyter notebook under the `notebooks/` directory and illustrates different workflow topologies and orchestration techniques without using LLMs.

## Notebooks
- [notebooks/conditional_workflow.ipynb](notebooks/conditional_workflow.ipynb) — example of conditional branching inside a StateGraph.
- [notebooks/iterative_workflow.ipynb](notebooks/iterative_workflow.ipynb) — shows loop/iteration patterns over state.
- [notebooks/orchestrator_workflow.ipynb](notebooks/orchestrator_workflow.ipynb) — orchestrator pattern that aggregates results from parallel tasks (cricket batsman example).
- [notebooks/parallel_workflow.ipynb](notebooks/parallel_workflow.ipynb) — demonstrates parallel task execution and result merging.
- [notebooks/sequential_workflow.ipynb](notebooks/sequential_workflow.ipynb) — linear pipeline of tasks updating shared state.

## Common Concepts
- `StateGraph`, `START`, `END`: central primitives used across examples (from the `langgraph` package).
- `TypedDict`-based state shapes: notebooks declare typed state shapes (e.g., `BatsmanState`) for clarity and static hints.
- Task functions: pure functions that accept a state and return a dict of updates.
- Orchestrator/merger nodes: nodes that collect partial updates (or messages) and produce combined outputs or summaries.

## How to Run
1. Activate the workspace Python environment (example using the included `myenv` virtualenv):

```bash
source myenv/bin/activate
```

2. Start Jupyter and open the notebooks directory:

```bash
jupyter notebook notebooks/
```

3. Open any notebook and run the cells. Each notebook compiles a `StateGraph` and invokes it on an example `initial_state`. The notebooks print final states or summaries.

Optional: execute all notebooks headless (requires `nbconvert`):

```bash
pip install nbconvert
jupyter nbconvert --to notebook --execute notebooks/*.ipynb --output executed_notebooks
```

## Example (common initial_state pattern)
Many notebooks use a simple `initial_state` dict with input fields, placeholder `None` values for derived metrics, and an optional `messages` inbox. See each notebook for concrete fields and examples.

## Dependencies
- Python 3.11 or compatible.
- `langgraph` (workspace examples call `StateGraph`, `START`, `END`).
- `jupyter` / `notebook`.

Install basics with:

```bash
source myenv/bin/activate
pip install -r requirements.txt
```

Credits: https://www.youtube.com/@campusx-official

