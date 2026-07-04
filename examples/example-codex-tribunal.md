# Example — Codex Tribunal run (sanitized)

**This is a sanitized EXAMPLE of a Tribunal run.** It shows the *structure* — three independent
judge personas, multiple rounds, an evidence gate, and a synthesized verdict. The architecture
under debate is generic ("a Kanban board UI backed by a git-synced source of truth"); all specific
paths, private repo names, and hostnames are removed.

## Question under debate
> Should the fleet's board UI be the **source of truth**, or a **read-only view** over the
> existing ticket store that is mirrored (git-synced) into the board?

## Personas
- 🏛️ **Architect** — long-term structure, coupling, failure modes.
- 🕵️ **Skeptic** — attacks the proposal; assumes it is wrong until proven otherwise.
- 🛠️ **Pragmatist** — shipping cost, day-2 operations, blast radius.

## Round 1 — opening positions
- **Architect:** The ticket store must stay the source of truth. The board is a projection; making
  the UI authoritative splits state and invites divergence.
- **Skeptic:** "Mirror it" hides a two-way-sync trap. If edits happen in the UI *and* the store,
  you get conflicts. Prove the sync is one-way or this fails.
- **Pragmatist:** A read-only view ships in days and can't corrupt data. Two-way sync is a quarter
  of work and a pager risk.

## Round 2 — evidence gate
Each persona must cite a concrete failure mode, not a preference.
- **Architect:** Dual-write races → tickets in two columns at once (observed class of bug).
- **Skeptic:** Without a per-ticket lock, concurrent mirror + edit double-creates cards.
- **Pragmatist:** Read-only view has zero write path → zero corruption surface. Verified by design.

## Round 3 — rebuttal
- **Skeptic → Pragmatist:** "Read-only" still needs deletes reconciled when tickets close. Answer:
  reconcile on a timer from the store; never write back. Accepted.
- **Architect:** Add an idempotent upsert keyed by ticket id so re-mirrors don't duplicate. Accepted.

## Verdict (2 of 3 required, evidence-gated)
> **Board UI = read-only view.** The ticket store stays authoritative; the board is mirrored
> one-way via idempotent, ticket-id-keyed upserts, reconciled on a timer. No write-back path.
> **Confidence: high** (all three personas converged; each cited a concrete failure mode).

**Why this beats "UI as source of truth":** removes the dual-write race entirely, ships far
cheaper, and keeps a single authoritative store — the same principle the orchestration model uses
everywhere (one owner of state, everything else is a view).
