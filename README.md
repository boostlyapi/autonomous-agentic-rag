# autonomous-agentic-rag

Agentic retrieval-augmented generation (RAG) workflows have many choices to tune, from retrieval strategies to agent instructions. This notebook-based project explores an evaluation loop that revises standard operating procedures (SOPs), tests the revisions, and compares their trade-offs using a healthcare trial-design example.

## Features

- Coordinate specialist agents with LangGraph to produce multi-source documents under a shared SOP.
- Prepare knowledge stores from sources such as PubMed literature and FDA guidance.
- Evaluate outputs across multiple criteria, including accuracy, feasibility, and compliance.
- Use diagnostician and SOP architect agents to identify weaknesses and propose revised procedures.
- Compare tested SOPs on a Pareto front so a human can choose among the trade-offs.

## Installation

Use a Python environment compatible with the dependencies listed in the notebooks. From your local project directory:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install jupyterlab nbconvert ipykernel
jupyter lab
```

On Windows, activate the environment with `.venv\Scripts\activate` instead.

Open the workflow notebook and follow its dependency-installation and environment-configuration cells. The workflow uses LangChain, LangGraph, Ollama for local models, and LangSmith for evaluation and tracing. Install Ollama separately and download the models specified by the notebook before running model-dependent cells.

## Usage

Start with an interactive run in JupyterLab. Configure the model assignments, prepare the knowledge stores, and run the specialist-agent workflow before starting the outer evolution loop. Review the evaluation results and Pareto analysis to choose an SOP.

For a non-interactive run after setup, use Jupyter's notebook execution command. Replace the placeholder below with the actual notebook path; this is a Jupyter command, not a project-specific CLI.

```bash
NOTEBOOK="path/to/workflow.ipynb"
jupyter nbconvert \
  --to notebook \
  --execute "$NOTEBOOK" \
  --ExecutePreprocessor.timeout=-1 \
  --output run-results.ipynb
```

The command writes an executed notebook with cell outputs. Runtime depends on the selected models, source data, and number of SOP trials configured in the notebook.

**Keep a human in the decision loop.** The healthcare example is an experimental workflow, not clinical advice. Review source material and generated claims before use. Do not send sensitive healthcare data to external models or tracing services without appropriate authorization.

## License

MIT. This project is based on [FareedKhan-dev/autonomous-agentic-rag](https://github.com/FareedKhan-dev/autonomous-agentic-rag). Retain the upstream copyright notice and MIT license text in copies or substantial portions of the original software.
