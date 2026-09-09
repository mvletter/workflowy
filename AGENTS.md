<!-- codebase-memory:start -->
## codebase-memory-mcp (code graph, CLI only)

This repo is indexed by `codebase-memory-mcp` (pinned v0.10.8 in `~/bin`), used only through its CLI: no MCP server, no daemon watcher, no hooks. The graph is a precomputed map, not a source of truth: verify every hit in the source.

- **Index (first use in a worktree, after a merge, and after your own changes):** `codebase-memory-mcp cli index_repository --repo-path .` (about 10 s, incremental on rerun). The `project` field in its output is the project name for the commands below. `.cbmignore` un-skips code directories the built-in skip-list would drop.
- **Impact before changing a shared symbol:** `codebase-memory-mcp cli trace_path --project <name> --function-name <fn> --direction inbound` with `--depth 1` lists the callers you must check before editing; the default depth 3 is the blast radius for your report; go deeper only to find the route or entry point that reaches the symbol. On an ambiguous name pass the `qualified_name` it suggests. `search_graph --project <name> --name-pattern "<regex>" [--label Function|Method|Class|Route]` finds symbols and HTTP routes.
- **Orientation:** `get_architecture --project <name>` for the summary and `detect_changes --project <name>` for the symbols touched by the current diff against main.
- Full command reference and worked examples: the global `codebase-memory` skill.
<!-- codebase-memory:end -->
