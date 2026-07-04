# [L-example · R000] 🔬 example-model · IDR: yes · 🕐 (synthetic)
> NotebookLM: https://notebooklm.google.com/  _(example notebook — replace with your own)_

**This is a sanitized EXAMPLE of an Interactive Deep Research (IDR) report.** All tools,
numbers, and links below are synthetic placeholders to show the format — not real research.

## Objective
Pick a build-cache tool for a mid-size monorepo: fast cold builds, low config, OSS license.

## NotebookLM workflow
1. Create a notebook; add the candidate projects' READMEs, docs, and a few blog posts as sources.
2. Ask grounded questions ("cold vs warm cache times?", "remote-cache setup cost?") — every answer
   cites a source, so claims are checkable, not vibes.
3. Export the grounded findings into the comparison matrix below.
4. Record the notebook's counter delta (queries run) as proof the research actually happened.

## Comparison matrix (synthetic)
```csv
Tool,Repo,⭐ Stars,License,Cold build,Config effort,Remote cache,Score,Crown
FooCache,github.com/example/foocache,12000,MIT,🟢 fast,🟢 low,🟢 yes,92,👑
BarBuild,github.com/example/barbuild,8400,Apache-2.0,🟡 medium,🟢 low,🟢 yes,81,
BazPipe,github.com/example/bazpipe,3100,MIT,🟢 fast,🔴 high,🟡 partial,74,
QuxMake,github.com/example/quxmake,900,BSD-3,🔴 slow,🟢 low,🔴 no,58,
```
Rules of the standard: real repo links, real star counts, **exactly one 👑 crown**, and a score
with visible provenance (every score cell traceable to a matrix column).

## Verdict
**FooCache** 👑 — fastest cold builds with the lowest config effort and native remote cache; MIT.
Runner-up BarBuild if Apache-2.0 is a hard requirement. Score provenance: cold-build (35) +
config (25) + remote-cache (20) + license/stars (12).

## Proof
- Notebook queries run: 14 (counter delta 0 → 14)
- Sources ingested: 9 (4 READMEs, 3 docs, 2 posts)
- Matrix cells all traceable to a cited source.
