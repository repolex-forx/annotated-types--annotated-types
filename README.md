# Repolex Knowledge Graph of annotated-types/annotated-types

RDF knowledge graph data for [annotated-types/annotated-types](https://github.com/annotated-types/annotated-types), parsed by [repolex](https://repolex.ai).

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
rlex download annotated-types/annotated-types
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0735cd3d4c272b88405b6b04009716b691115210
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 0735cd3d4c272b88405b6b04009716b691115210.nq.gz
│   └── repolex
│       └── 0735cd3d4c272b88405b6b04009716b691115210
│           └── chunk-001.nq.gz
├── blob
│   ├── 0bc47c98d9dd58b371bf17dac2b41b692e588a2c.nq.gz
│   ├── 5c54d7bdd03797734ffa1645dc1165c1251e85bf.nq.gz
│   ├── 621947501ef2bff3cda321386976121f83059e91.nq.gz
│   ├── 74e0deeab3f5904260ac2d36d64fbdec7e0ee0bf.nq.gz
│   ├── 8691b84b48869513119832ab621b7855af564ee6.nq.gz
│   ├── 8f9f8af17f4c7c125f8ec6cb15ac33bafb5727b7.nq.gz
│   ├── 908784fb7553c8c3c76db4cbd872e03003d67ba7.nq.gz
│   ├── 92c08094b0b399cd416485a686854b18f24dba5b.nq.gz
│   ├── a27e8abff6432e9e097cb5a344a7f976af9b4bb1.nq.gz
│   ├── d45b2f25afa0b8c10769820dbe5d0288ea3499fe.nq.gz
│   ├── d9164d6883d2dd47cb766b483592ca3730f6f09d.nq.gz
│   ├── d99323a9965f146d5b0888c4ca1bf0727e12b04f.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ed7b62820a41a5cbd94b46ed58c5319632fe87fe.nq.gz
│   ├── f6b63ba5760913db161a34a79fb4a0428987b2ae.nq.gz
│   └── f84300875f72ed64e4e5e58a889b05ae1ba250b4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 0735cd3d4c272b88405b6b04009716b691115210.nq.gz
├── filetree
│   └── 0735cd3d4c272b88405b6b04009716b691115210.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 26 files
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

[annotated-types/annotated-types](https://github.com/annotated-types/annotated-types)

---
*Parsed on 2026-09-28 by [repolex](https://repolex.ai)*
