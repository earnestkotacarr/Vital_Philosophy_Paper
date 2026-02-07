# Vitality 3: Synthesis

## What Vitality 3 IS

Vitality 3 grounds lifelikeness in **play**. Play is not a metaphor — it is a learning loop with two concrete, complementary capacities:

1. **Dynamic bidirectional engagement** (the affecting ↔ affected oscillation). In rough-and-tumble play, animals keep the game alive by balancing influence and receptivity. Formalized as **Empowerment–Plasticity** (Abel et al. 2025): empowerment = I(A→O), plasticity = I(O→A). Their oscillation produces endogenous explore–exploit rhythms. The harmonic mean V_t = 2E_tP_t/(E_t+P_t) captures balanced bidirectionality. Internalized as slow morphogens (E_t, P_t) that constitute first-person time and regulate the fast sensorimotor loop — a Turing-pattern-like reaction–diffusion dynamic between consolidation and rewrite.

2. **Symbolic abstraction** (the reflective/pretend capacity). In pretend play, a child treats a stick as a sword — operating over meanings, roles, and abstractions rather than raw percepts. Formalized as **algebraic constraint learning**: group-theoretic decomposition that extracts conditionally independent, transformation-invariant, reusable features (operational invariants / "perceptual symbols"). These are discrete, composable, and manipulable — symbol-ready for use in control and planning.

**Vitality = the integrated dynamic–symbolic loop.** Bidirectional engagement generates disciplined interaction patterns and self-regulated regime switching. Symbolic abstraction extracts and organizes what was learned into reusable building blocks. The agent then projects those abstractions back as new control targets, and E–P oscillation continues at this higher level. Repeating yields open-ended developmental growth without external rewards or hand-designed curricula.

## How V3 Differs from V2

| | V2 | V3 |
|---|---|---|
| **Grounding** | Viability vs. vitality (staying alive vs. truly living) | Play (the two capacities of play ARE vitality) |
| **Core structure** | Empowerment + plasticity + NTIC audit | E–P oscillation + symbolic abstraction (no NTIC) |
| **NTIC** | Retained as third-person sanity check | **Dropped entirely** |
| **Symbolic layer** | Absent | Central — algebraic constraint learning as the second capacity |
| **Developmental story** | Static criterion (high V_t regime) | Dynamic–symbolic loop: E–P generates interaction → abstraction extracts structure → structure becomes new control targets → E–P continues at higher level |
| **Connection to play** | Implicit (empowerment/plasticity evoke engagement) | Explicit and foundational — play's two capacities are the two components |
| **Self-critique** | None | Paper explicitly identifies limitations of its own entropic mechanisms |

## Paper Outline

**Section 1: Play.** The phenomenon. Two capacities found in play across species: (a) dynamic bidirectional engagement — the affecting/affected oscillation that keeps the game alive; (b) symbolic abstraction — treating objects as stand-ins, operating on meanings rather than percepts. Why play matters for autonomy and development. Play as a developmental engine, not a metaphor.

**Section 2: Vitality — Formalizing Play.** Vitality is the formal dual of play's two capacities. (a) Empowerment–Plasticity as the formalization of bidirectional engagement (Abel's framework, harmonic mean, morphogen internalization, Turing pattern dynamics). (b) Algebraic constraint learning as the formalization of symbolic abstraction (group-theoretic decomposition, operational invariants, symbol-ready representations). The integrated loop: E–P oscillation supplies disciplined actions and selection pressure → algebraic learning extracts reusable structure → structure projects back as new control targets → development.

**Section 3: Best Mechanisms We Have.** The mathematical and computational tools currently available for each component. For bidirectional engagement: Abel's E–P tradeoff geometry, directed information, morphogen dynamics, reaction–diffusion patterns. For symbolic abstraction: Ohmura's algebraic constraints, VQ-VAE codebooks, DreamCoder-style program synthesis, GFlowNets over discrete combinatorial spaces. For the integration: how E–P oscillation provides the missing selection pressure for representation learning, and how learned symbols become new substrates for E–P dynamics.

**Section 4: Problems with These Mechanisms.** The two structural critiques (from critique_symbols_and_entropy.md):

- **The entropic optimization problem.** E and P are mutual information quantities. MI presupposes the representation problem is solved (circular), is computationally intractable at scale (O(ln N) bound — McAllester & Stratos 2020), collapses structure into scalars (structurally impoverished), and lacks causal structure (CHT — Bareinboim et al. 2022). These are theorem-level limitations, not engineering complaints. Even with discretization (V3's symbolic layer helps here), causal blindness and structural impoverishment persist.

- **The symbolic layer is necessary but not yet achieved.** Current dominant frameworks (active inference, predictive coding, empowerment) are committed to subsymbolic-all-the-way-up architectures. Without symbols you're stuck with entropy; without non-entropic objectives you have no pressure to learn symbols. This is a self-reinforcing trap. V3's algebraic constraint learning is a step toward breaking out, but the integration with E–P dynamics is still open.

- **The connection.** These critiques reinforce each other: dropping symbols forces reliance on entropy, and entropy-only objectives provide no pressure to learn symbols. V3 attacks both simultaneously — E–P for the dynamic side, algebraic learning for the symbolic side — but inherits the limitations of each component's current mathematical realization.

**Section 5: Todo.** What remains to be built:
- Interventional Vitality: upgrading E and P from associational MI to interventional MI via do-calculus (all machinery exists; assembly is new)
- Constructor-theoretic Vitality: reformulating from bits to task-repertoires (long-term, requires solving the measure problem)
- Categorical compositional structure: expressing the framework in Smithe/Spivak's compositional language
- Empirical: implementing E–P + algebraic learning on ISI Baby Simulator, benchmarking against infant developmental milestones
- The knowledge threshold: when do morphogens transition from passive information to active knowledge (information that causes itself to persist)?

## Key Intellectual Moves

1. **Play is not decoration — it is the engine.** Play's two capacities (dynamic engagement + symbolic abstraction) map precisely onto the two things missing from current autonomy frameworks (bidirectional intrinsic motivation + compositional representation learning).

2. **The self-reinforcing trap.** The subsymbolic-entropic paradigm is self-reinforcing: without symbols → stuck with entropy → no pressure for symbols. V3 breaks this by attacking both exits simultaneously.

3. **Honest self-critique.** V3 uses the best available mechanisms (E–P, algebraic constraints) and then *explicitly identifies their mathematical limitations* (MI intractability, causal blindness, structural impoverishment). The paper is a position paper that says: here is the right architecture, here are the best tools we have for it, and here is why those tools are not yet sufficient — pointing toward what must come next.

4. **The developmental loop closes.** The novel integration: E–P generates interaction → algebraic learning extracts symbols → symbols become new E–P control targets → development continues at higher abstraction levels. This is the core contribution missing from both intrinsic motivation work (no symbolic extraction) and representation learning work (no principled intrinsic drive).
