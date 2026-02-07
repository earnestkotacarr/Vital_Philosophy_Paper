# Vitality3 Paper Revision - Task Plan

## Context
Revise the Vitality3 paper drafts at `write/white/Vitality3/Vitality3.md` and `write/white/Vitality3/Vitality3.tex`. Revision notes are at `write/white/Vitality3/v3_revision_notes.md`. The existing drafts already incorporate most revision notes (Klopf, Sepulchre, autonomy definition, abstract todos, no constructor theory, colloquial tone). Ralph should cross-reference what exists and improve it. Keep .md and .tex in sync at all times. This is an internal paper — colloquial tone is fine.

## CRITICAL: Follow V2 White Paper Structure
The paper MUST follow the structural style of `write/white/Vitality2/Vitality2_171225.tex`. That means:
- **Short, technical white paper** — NOT a long philosophy essay
- **Formal definitions** in definition environments, **propositions** with proofs/sketches
- **Tight subsections** with formal statements, not long narrative paragraphs
- **Mathematical rigor first**, prose explains the math — not the other way around
- V2 is ~365 lines of .tex. V3 should be comparable length — concise, dense, formal
- Study V2's section structure: Introduction → Formal Setup → definitions → interface capacities → morphogens → dynamic measure → pathologies → discussion. V3 content differs (play, E-P, symbolic abstraction, problems, todos) but the FORMAT should match V2's terse, definition-heavy white paper style
- **Do NOT write a philosophy paper.** Write a technical white paper with colloquial asides.

## Source files to read for context
- `write/white/Vitality3/v3_revision_notes.md` — revision instructions
- `write/white/Vitality3/v3_synthesis.md` — synthesis of V3 vision
- `write/white/Vitality3/critique_symbols_and_entropy.md` — the two structural critiques
- `write/white/Vitality3/critique_followup_research.md` — follow-up research
- `write/white/Vitality3/EarnestKotaCarr_BOOSTNAIS.pdf` — BOOST NAIS application grounding everything in play
- `write/white/Vitality2/Vitality2_171225.tex` — V2 paper (structural reference only)

| Task | Description | Complete |
|------|-------------|----------|
| 0 | Read all source files and current drafts. Cross-reference revision notes against what already exists. Identify gaps. | false |
| 1 | Tighten Section 1 (Play). The Klopf/Sepulchre subsection is good but could be sharper. Make sure the autonomy = self-regulation + self-amplification definition lands hard here, not just in Section 5. | false |
| 2 | Tighten Section 2 (Formalization). The math is fine. Make the prose around it more direct. The Klopf connection paragraph in 2.3 is a bit redundant with 1.3 — consolidate or differentiate. | false |
| 3 | Tighten Section 3 (Best Mechanisms). This is the thinnest section. Flesh out how E-P oscillation actually works as selection pressure for representation learning. The integration subsection (3.3) needs more substance — it's the core novelty. | false |
| 4 | Improve Section 4 (Problems). The self-reinforcing trap (4.2) is the strongest part. Make sure the four entropy problems in 4.1 are crisp and punchy — these are theorem-level results, not opinions. Reference the actual theorems. | false |
| 5 | Rewrite Section 5 (Todos) if needed. Should have: (a) causal + tractable bidirectional IM — mention Gunji/Pegios, (b) representation learning doing both indexing AND feature extraction, (c) integration where IM is the mother-of-all-valleys constraint on representation learning, (d) autonomy = self-regulation + self-amplification made explicit. Check current draft against this. | false |
| 6 | Final pass: cut any remaining bloat, ensure colloquial internal-paper tone throughout, verify .md and .tex are perfectly synced. | false |
