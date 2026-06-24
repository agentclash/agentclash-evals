# AgentClash Evals

Local pre-deploy agent eval SDKs for AgentClash.

This repo owns the lightweight SDK packages for writing evals like normal tests:

- Python package: `agentclash-evals` / import `agentclash_eval`
- TypeScript package: `@agentclash/evals` alpha spike
- Language-neutral report schemas in `schemas/evaltest`

The main AgentClash repo remains the platform, hosted eval, challenge-pack, CLI, and regression-gate repo:
https://github.com/agentclash/agentclash

## Quick start: Python

```bash
cd python/agentclash_eval
python -m pip install -e ".[dev]"
pytest -q
```

```python
from agentclash_eval import assert_agent
from agentclash_eval.metrics import Contains

def test_agent_output():
    assert_agent("hello world", metrics=[Contains("world")])
```

## Quick start: TypeScript

```bash
cd typescript/evals
npm install
npm test
```

## Design rules

- No auth required for local evals.
- No telemetry by default.
- No hidden network calls.
- Core package keeps dependencies minimal.
- Hosted AgentClash integration is explicit and opt-in.
