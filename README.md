# Repolex Knowledge Graph of sphinx-contrib/cheader

RDF knowledge graph data for [sphinx-contrib/cheader](https://github.com/sphinx-contrib/cheader), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/cheader
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f05c8c6efa2e04b4071aca3b25cb6c2cb5056689
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f05c8c6efa2e04b4071aca3b25cb6c2cb5056689
│           └── chunk-001.nq.gz
├── blob
│   ├── 28170d1b7fc7de97b5ce69fe5b5b7cc598328291.nq.gz
│   ├── 3eefcb9dd5b38e2c1dc061052455dd97bcd51e6c.nq.gz
│   ├── 68a49daad8ff7e35068f2b7a97d643aab440eaec.nq.gz
│   ├── 8e7e2bc0d26ebc39199523caf9850ff62f3d650a.nq.gz
│   ├── b0cea1c155536a3bec95cdfb346babb69fcd6ab2.nq.gz
│   ├── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
│   ├── e147b9c6acc353ea9ef86dda12188cd343b22a26.nq.gz
│   ├── e4f279c07ac4bb5711b07d89a7983ac9df112cf9.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── ff1afabd6def2b31fc7309551a68ab74971debd6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f05c8c6efa2e04b4071aca3b25cb6c2cb5056689.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/cheader](https://github.com/sphinx-contrib/cheader)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
