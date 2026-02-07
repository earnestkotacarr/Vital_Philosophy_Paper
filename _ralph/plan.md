# Vitality3 Paper Revision - Round 2

## Context
The V3 drafts at `write/white/Vitality3/Vitality3.md` and `write/white/Vitality3/Vitality3.tex` were restructured in Round 1 but went too far — they now read like an extended bulleted list, not a coherent readable paper. This round fixes that and corrects a conceptual error.

Keep .md and .tex in sync at all times. Internal paper — colloquial tone is fine.

## CRITICAL STYLE NOTE
V2 (`write/white/Vitality2/Vitality2_171225.tex`) is the structural reference. But V2 uses **prose paragraphs with occasional formal definitions** — it does NOT read like a bulleted list. Read V2 again carefully: it flows as readable paragraphs, with definition/proposition environments used sparingly for key formal statements. The current V3 overuses bullet points and formal environments, making it choppy and unreadable. **Fix this: restore coherent flowing prose. Use formal definition environments ONLY for the 3-4 most important definitions (Vitality, Autonomy, maybe Symbolic Inventory). Everything else should be readable paragraphs.**

## THREE PROBLEMS TO FIX

### Problem 1: Too list-like
The paper reads like an extended bulleted list. Every section was converted to bullet points. This is wrong. A white paper has **flowing prose** with math woven in. Bullet points should be rare — used only for enumerations where items are genuinely parallel (like the pathologies table). Convert all bullet-soup back to coherent paragraphs. The paper should READ well, like V2 does.

### Problem 2: Wrong autonomy/vitality definition
The current Definition 1 says: "Autonomy is self-regulation AND self-amplification (homeostasis + heterostasis). An autonomous system maintains itself (viability) while expanding its capacities (vitality)."

This is WRONG. Here's the correction:
- **Autonomy** = self-regulation + self-amplification. That part is right.
- **Vitality** is NOT just "the measure of how well both are working." Vitality is the specific **Turing-esque dynamical form** where E and P **co-regulate each other**. E regulates P, P regulates E — the reaction-diffusion pattern IS vitality. Vitality is not a score. It's the regime of coupled co-regulation. The harmonic mean V_t is a *measure* of vitality, but vitality itself is the dynamical pattern of E-P co-regulation (the Turing pattern).
- Fix this throughout — vitality is the dynamical co-regulatory regime, not just a number.

### Problem 3: Add constructionist knowledge idea
In the morphogen section (temporal morphogens / internalization), add the constructionist idea that **knowledge is information that self-persists**. The temporal morphogens (slow E, slow P) are exactly this — they are internalized information that persists and shapes future interaction. This is the Piagetian constructionist insight: knowledge isn't stored data, it's self-maintaining structure. The morphogens ARE knowledge in this sense — they are the agent's consolidated developmental history, actively maintaining themselves through the E-P loop. This should be woven into the morphogen discussion naturally, not as a bolted-on paragraph.

## Source files
- `write/white/Vitality3/v3_revision_notes.md` — original revision instructions
- `write/white/Vitality2/Vitality2_171225.tex` — V2 paper (READ THIS for prose style, not just structure)
- `_ralph/activity.md` — log of Round 1 work

| Task | Description | Complete |
|------|-------------|----------|
| 0 | Read V2 carefully for PROSE STYLE (not just structure). Read current V3 drafts. Understand what needs to change. | false |
| 1 | Fix the autonomy/vitality definition error throughout the paper. Vitality = the Turing-esque co-regulatory E-P regime, not just a score. Autonomy = self-regulation + self-amplification. Make sure these are correct everywhere. | false |
| 2 | Convert ALL bullet-point-soup sections back to flowing prose paragraphs. Keep formal definition environments ONLY for 3-4 key definitions. Everything else should read as coherent paragraphs like V2. The paper must READ well. | false |
| 3 | Add constructionist knowledge-as-self-persisting-information to the morphogen section. Weave it in naturally — morphogens ARE knowledge in the constructionist sense. | false |
| 4 | Final pass: read the whole paper start to finish. Does it flow? Is it readable? Is the tone right (colloquial but rigorous)? Verify .md and .tex are synced. | false |
