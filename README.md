# Repolex Knowledge Graph of explosion/curated-transformers-addons

RDF knowledge graph data for [explosion/curated-transformers-addons](https://github.com/explosion/curated-transformers-addons), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/curated-transformers-addons
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 62578a013e8bb8147fcd2b6ec55d99a7abe11890
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 62578a013e8bb8147fcd2b6ec55d99a7abe11890
│           └── chunk-001.nq.gz
├── blob
│   ├── 082469080a2f6add8ab49d5c356ef4a972ea5d43.nq.gz
│   ├── 13910b04504083726346e0222a8c7914ea4c120c.nq.gz
│   ├── 2a6b7487daa85ae817fbab6bcad6aad0dc527550.nq.gz
│   ├── 343b5417ecc47d5de2e3905a88765c0e9a0228f8.nq.gz
│   ├── 4d4b944a0d00d72a0cdcde076c81e079546a4939.nq.gz
│   ├── a86a58bbcd67e237a518fcfcaa8b4325869c7556.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 62578a013e8bb8147fcd2b6ec55d99a7abe11890.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 13 files
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

[explosion/curated-transformers-addons](https://github.com/explosion/curated-transformers-addons)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
