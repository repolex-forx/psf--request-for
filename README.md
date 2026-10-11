# Repolex Knowledge Graph of psf/request-for

RDF knowledge graph data for [psf/request-for](https://github.com/psf/request-for), parsed by [repolex](https://repolex.ai).

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
rlex download psf/request-for
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9f42ba4f023927efb5465a4a098f82fb5b1c512f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9f42ba4f023927efb5465a4a098f82fb5b1c512f
│           └── chunk-001.nq.gz
├── blob
│   ├── 45a4677fbd56c05efeddfac7fac8a5bbf8e64c79.nq.gz
│   ├── 63656afe445c81a1127a833e9fac65720d6ded77.nq.gz
│   ├── 8398af940ed72c019f15111de69bd06327cf61d2.nq.gz
│   ├── 9f1a085e3e5521c406db6b3850d7f8d9cc4a11a9.nq.gz
│   ├── a1f58d127fcc96175d4e118d0d5a4e06604ff3ed.nq.gz
│   └── f7daa97404b7451c1d4e46bea04de1957fb3028e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9f42ba4f023927efb5465a4a098f82fb5b1c512f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
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

[psf/request-for](https://github.com/psf/request-for)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
