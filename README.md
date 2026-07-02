# demo_repo

A throwaway scratch git repo used by [`coding-agent-demo`](https://github.com/dalenguyen/coding-agent-demo) as the working directory for the coding agent.

It exists so the agent has a clean, version-controlled sandbox to make changes in (create files, run tests, commit) without touching the parent project's own source. The contents are deliberately minimal — what matters is that it's a real git repo the agent can edit.

## How it's used

The parent repo's [`agent.py`](https://github.com/dalenguyen/coding-agent-demo/blob/main/agent.py) takes a path to a git repo as its first argument and operates on it as the working tree. `demo_repo` is the default scratch target. Reset it between takes:

```bash
git -C demo_repo clean -fdxq && git -C demo_repo checkout -q -- .
```

(The `-x` matters — the agent sometimes creates its own gitignored `.venv/` inside the repo.)

## See also

- [dalenguyen/coding-agent-demo](https://github.com/dalenguyen/coding-agent-demo) — the agent code, backends, and usage