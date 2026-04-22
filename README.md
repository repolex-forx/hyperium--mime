# Repolex Knowledge Graph of hyperium/mime

RDF knowledge graph data for [hyperium/mime](https://github.com/hyperium/mime), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download hyperium/mime
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ce5062d216bf757a0ed3fc70f0fe255d1c8d74ae
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── ce5062d216bf757a0ed3fc70f0fe255d1c8d74ae.nq.gz
│   └── repolex
│       └── ce5062d216bf757a0ed3fc70f0fe255d1c8d74ae
│           └── chunk-001.nq.gz
├── blob
│   ├── 106de1a1e6a2bee8764ff8b5e01d33df6de4d4bc.nq.gz
│   ├── 16fe87b06e802f094b3fbb0894b137bca2b16ef1.nq.gz
│   ├── 20022b775b369444cc1c02801843c44aeb579536.nq.gz
│   ├── 36b841897ef2277b4b7b20120fcd7b2a1d83a5b2.nq.gz
│   ├── 3fbc3a312370f9f23e0d5e200575537e516a6d09.nq.gz
│   ├── 4fffb2f89cbd8f2169ce9914bd16bd43785bb368.nq.gz
│   ├── 557b7e5fc97e430e88aafc9dd42fac4f3decf50d.nq.gz
│   ├── 7d47781a0d30339ca40858a33e8682d6059ce967.nq.gz
│   ├── b7c64f64f6b0fa723f047bb1b207cab2c730d19c.nq.gz
│   ├── c9ae86c48ee661260bbf45f356448a459826bfa5.nq.gz
│   ├── da1d3c0f654a9ad29045efc643f451b93618c91a.nq.gz
│   └── dba63140780408d103410e3cb8d67a097a623224.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ce5062d216bf757a0ed3fc70f0fe255d1c8d74ae.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

14 directories, 21 files
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

## Source repository

[hyperium/mime](https://github.com/hyperium/mime)

---
*Parsed on 2026-04-22 by [repolex](https://repolex.ai)*
