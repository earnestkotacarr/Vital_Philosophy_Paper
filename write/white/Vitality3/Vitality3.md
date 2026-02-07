# Vitality as a Formal Theory of Play: Dynamic Engagement and Symbolic Abstraction as Dual Capacities of Autonomous Development

**Version 3 — Draft**

*"The creation of something new is not accomplished by the intellect but by the play instinct." — C.G. Jung*

---

## Abstract

We propose Vitality as a formal theory of autonomous development grounded in play. Play — across species and developmental stages — exhibits two complementary capacities: *dynamic bidirectional engagement* (oscillating between influencing and being influenced) and *symbolic abstraction* (operating on meanings and invariants rather than raw percepts). We formalize the first as Empowerment–Plasticity oscillation (Abel et al. 2025) and the second as algebraic constraint learning that extracts discrete, composable, transformation-invariant representations. Their integration — bidirectional engagement generating disciplined interaction, symbolic abstraction extracting reusable structure that becomes substrate for further engagement — constitutes a developmental loop producing open-ended growth without external rewards. We present the best available mechanisms for each capacity, then subject them to two structural critiques: entropic objectives cannot be the highest-level goal for autonomy, and the missing symbolic layer creates a self-reinforcing trap with entropy-based methods. These critiques are not objections to Vitality — they define the research program it points toward.

---

## 1. Play

### 1.1 Observation: Play Is Not Recreation

- Play appears across species wherever nervous systems support flexible behavior.
- Evidence:
  - Piaget: play central to cognitive construction.
  - Trevarthen: intersubjective play founds social cognition.
  - Panksepp: dedicated neural circuitry irreducible to other motivational systems.
- Play has *structure*: not random exploration, but a regime characterized by two complementary capacities.

### 1.2 First Capacity: Dynamic Bidirectional Engagement

- Behavioral observation (rough-and-tumble play):
  - Animals oscillate between influence and receptivity.
  - Pure domination (only pins) → game ends.
  - Pure submission (only pinned) → game ends.
  - Game persists ⟺ both oscillate between affecting and being affected.
- Formalization:
  - **Affecting** (empowerment): actions reliably influence future observations.
  - **Being affected** (plasticity): observations reliably reshape future actions.
- Pathologies:
  - Pure empowerment → rigidity.
  - Pure plasticity → puppetry.
  - Play lives where both are simultaneously high and dynamically balanced.
- Oscillatory structure: perturb → observe → update → re-perturb.
- When oscillation collapses → developmental engine stalls.

### 1.3 Why Both Directions: Klopf's Critique of Cybernetics

- **Klopf (1982)**: Cybernetics (Wiener, Ashby) built a science of *homeostasis* — negative feedback toward set-points.
- But living systems are also *self-amplifying*: seek stimulation, escalate challenges, pursue novelty.
- Klopf's *heterostasis*: drive toward more, not back to baseline.
- **Sepulchre (2022)**: Robust adaptive systems require *both* positive and negative feedback coupled.
  - Negative feedback only → converges to fixed point.
  - Positive feedback only → explodes.
  - Development, learning, play → both coupled.
- Connection to E–P:
  - **Empowerment**: positive feedback (self-amplifying, extends influence).
  - **Plasticity**: negative feedback (self-regulating, accommodates perturbation).
  - Vitality: regime where both are active and coupled.

**Definition (Autonomy).** Autonomy is self-regulation AND self-amplification (homeostasis + heterostasis). An autonomous system maintains itself (viability) while expanding its capacities (vitality).

### 1.4 Second Capacity: Symbolic Abstraction

- Behavioral observation (pretend play):
  - Child picks up stick, calls it a sword.
  - Operation: abstract functional role → map onto novel substrate → operate on abstraction.
- This is symbolic computation:
  - Extract structural invariants from experience.
  - Recombine in novel configurations.
  - Piaget: accommodation → assimilation at higher levels.
- Coupling to dynamic capacity:
  - Active probing discovers transformation-invariant features.
  - Extracted symbols become new control targets.
  - Example: child abstracts "tool" → seeks control over tool-use at higher abstraction level.

### 1.5 The Developmental Loop

**Definition (Play as Developmental Loop).** Play implements a self-organizing developmental cycle:

(a) **Bidirectional engagement** generates disciplined interaction near competence boundary.
(b) **Symbolic abstraction** extracts reusable, transformation-invariant, composable features.
(c) **Projection**: symbols become new E–P substrates—agent oscillates at higher abstraction level.
(d) **Repeat**.

Result: open-ended growth without external rewards or hand-designed curricula.

---

## 2. Vitality: Formalizing Play

### 2.1 Setup

- Agent state space: $\mathcal{X}$, partitioned into $Y_t$ (internal) and $W_t$ (world).
- Interface $\lambda$: actions $A_{1:T}$, observations $O_{1:T}$.
- Policies $\pi$ induce trajectory distributions.

### 2.2 Formalizing Bidirectional Engagement

**Definition (Empowerment).**
$$E_t(\lambda) := I(A \leadsto O;\, \lambda)_t$$
Channel capacity for actions to influence future observations.

**Definition (Plasticity).**
$$P_t(\lambda) := I(O \leadsto A;\, \lambda)_t$$
Channel capacity for observations to reshape future actions.

**Proposition (Abel Tradeoff).**
$E_t + P_t \leq m_t(\lambda)$, where $m_t(\lambda)$ is interface-dependent upper bound.

**Definition (Vitality Score, time-local).**
$$V_t(\lambda) := \frac{2\,E_t\, P_t}{E_t + P_t}$$
Harmonic mean: requires both positive, penalizes extremes, maximum at $E_t = P_t$.

### 2.3 Temporal Morphogens

**Definition (Internalization).**
Interface capacities (fast measurements) internalized as slow state:
$$\mathcal{E}_{t+1} = (1 - \alpha_E)\mathcal{E}_t + \alpha_E\, E_t(\lambda), \qquad \mathcal{P}_{t+1} = (1 - \alpha_P)\mathcal{P}_t + \alpha_P\, P_t(\lambda)$$

- $\mathcal{E}_t$: slow "skill/commitment" morphogen.
- $\mathcal{P}_t$: slow "reconfigurability" morphogen.

**Structure:**

- Fast-loop modulation:
  $$\text{adaptation strength} \propto f(\mathcal{P}_t), \qquad \text{stability/precision} \propto g(\mathcal{E}_t)$$

- Reaction–diffusion structure:
  - $\mathcal{E}$: activator (stabilizing).
  - $\mathcal{P}$: inhibitor (destabilizing).
  - Different timescales: $\alpha_P \ll \alpha_E$ (slow to recruit, fast to act).

- Result: temporal Turing patterns—alternating plateau (exploit) and burst (explore) phases.
- Developmental transitions emerge as bifurcations between behavioral regimes.

### 2.4 Formalizing Symbolic Abstraction

- Given observations $\{o_t\}$ from interaction, learn:
  - Encoder $\phi: \mathcal{O} \to \mathcal{Z}$.
  - Factored latent space $\mathcal{Z} = \mathcal{Z}_1 \times \cdots \times \mathcal{Z}_k$.

- Requirements:
  1. **Group-theoretic decomposition**: each $\mathcal{Z}_i$ transforms independently under subgroup $G_i$.
  2. **Transformation invariance**: each factor captures structural invariant reusable across contexts.
  3. **Discretizability**: factors naturally discretizable (finite groups, discrete orbits) → vocabulary of *perceptual symbols*.

**Definition (Symbolic Inventory).**
$\mathcal{S}_t = \{(\mathcal{Z}_i, G_i, \phi_i)\}_{i=1}^{k_t}$ grows over development.

### 2.5 The Integrated Definition

**Definition (Vitality, Version 3).**
A system exhibits Vitality over horizon $T$ if:

1. **High dynamic engagement**: $\bar{V}_T$ sustained above threshold (balanced bidirectional coupling).
2. **Growing symbolic inventory**: $|\mathcal{S}_T| > |\mathcal{S}_0|$ (reusable abstractions extracted from interaction).
3. **Loop closure**: learned symbols become E–P substrates (empowerment–plasticity computed over symbolic space, not just raw sensorimotor channels).

**Distinguishing feature:**

- Condition (3) distinguishes this from "intrinsic motivation + representation learning."
- The loop closes: symbols recruited into control → generate new interactions → extract further abstractions.

### 2.6 Pathologies

| Pathology | Why excluded |
|-----------|-------------|
| Frozen agent | $\mathcal{P}_t \to 0 \Rightarrow V_t \to 0$ (no negative feedback) |
| Rewrite-soup | $\mathcal{E}_t \to 0 \Rightarrow V_t \to 0$ (no positive feedback) |
| Novelty chaser | No symbolic extraction despite exploration |
| Compressor | No bidirectional engagement driving feature selection |
| Static optimizer | No projection of symbols back into E–P — development stops |

---

## 3. Best Mechanisms We Have

### 3.1 For Bidirectional Engagement

- **Abel et al. (2025)**: Plasticity as formal dual of empowerment within generalized directed information.
  - Channel capacities: forward ($A \to O$) and reverse ($O \to A$).
  - Tight tradeoff: $E + P \leq m(\lambda)$.
  - Interface has finite bidirectional capacity; any allocation respects this bound.
- **Morphogen dynamics**: Internalizing E and P as slow morphogens yields reaction–diffusion structure.
  - Plateau phase: high $\mathcal{E}$, low $\mathcal{P}$ (exploit).
  - Burst phase: recruited $\mathcal{P}$ (explore).
  - Maps directly onto explore–exploit oscillation.
  - Developmental transitions emerge as bifurcations.

### 3.2 For Symbolic Abstraction

- **Algebraic constraint learning (Ohmura et al.)**:
  - Biases feature discovery toward group-theoretic decompositions.
  - Separates conditionally independent transformations.
  - Features: operationally meaningful, naturally discretizable, composable.
- **Discrete codebook methods**:
  - VQ-VAE: discrete latent representations via vector quantization.
  - Discrete Codebook World Models (Scannell et al. 2025): preserve ordinal relationships.
  - GFlowNets (Bengio et al. 2023): navigate discrete combinatorial structure with neural guidance.
- **DreamCoder (Ellis et al. 2021)**:
  - Bootstraps compositional program libraries through wake-sleep.
  - Discrete, composable building blocks grow over time.

### 3.3 For the Integration

The integration of dynamic engagement with symbolic abstraction is the core novelty. Current representation learning and intrinsic motivation frameworks fail because they address one side without the other.

#### E–P as Selection Pressure for Representation Learning

- **The underdetermination problem in representation learning**:
  - Unsupervised learning: infinitely many representations compress data equally well.
  - No principled selection criterion beyond reconstruction error or contrastive loss.
  - Result: learned features may be statistically optimal but behaviorally useless.
- **E–P provides the missing selection pressure**:
  - Feature $z$ is valuable iff it expands *both* $E$ (controllability via $z$) and $P$ (sensitivity to $z$).
  - This is a *functional* criterion: features must support bidirectional coupling.
  - Filters out features that compress well but don't enable better engagement.
- **Formal mechanism**:
  - At time $t$, agent has symbolic inventory $\mathcal{S}_t = \{z_1, \ldots, z_k\}$.
  - Compute $E_t(\lambda_z)$ and $P_t(\lambda_z)$ for each symbol $z \in \mathcal{S}_t$ (empowerment/plasticity when controlling/observing $z$).
  - Features with high $V_t(\lambda_z) = 2E_t(\lambda_z)P_t(\lambda_z)/(E_t(\lambda_z)+P_t(\lambda_z))$ are retained and elaborated.
  - Features with low $V_t(\lambda_z)$ are pruned or not extracted in the first place.
  - This implements *developmental filtering*: the dynamic layer shapes what the symbolic layer learns.

#### Symbols as New E–P Substrates

- **Hierarchical projection**:
  - Once extracted, symbols $z \in \mathcal{S}_t$ become new control and observation targets.
  - E–P dynamics shift from sensorimotor space $(A, O)$ to symbolic space $(Z_A, Z_O)$.
  - Agent now seeks to influence and be influenced at the level of abstractions, not raw percepts.
- **Example (Piaget-style)**:
  - Sensorimotor stage: E–P over raw actions (grasp, release) and observations (visual flow, tactile feedback).
  - Object stage: abstracts "graspable object." Now E–P operates over object-level actions ("grab the cup") and object-level observations ("cup moved").
  - Relational stage: abstracts "containment." Now E–P operates over relational actions ("put A in B") and relational observations ("A is inside B").
  - Each level's symbols become the substrate for the next level's E–P oscillation.
- **Closure of the loop**:
  - Symbols extracted from E–P data at level $n$ become E–P targets at level $n+1$.
  - This is *recursive abstraction*: the mechanism that generates symbols also consumes them.
  - Contrast with static representation learning: features are extracted once and used for downstream tasks, but not fed back into the feature-extraction process itself.

#### Hierarchical Developmental Dynamics

- **Developmental trajectory**:
  $$\text{sensorimotor} \xrightarrow{\text{E–P + abstraction}} \text{object} \xrightarrow{\text{E–P + abstraction}} \text{relational} \xrightarrow{\text{E–P + abstraction}} \text{social}$$
- At each level $\ell$:
  - E–P oscillates over current symbolic inventory $\mathcal{S}_\ell$.
  - Generates interaction data at level $\ell$.
  - Algebraic constraint learner extracts new symbols $\mathcal{S}_{\ell+1} \supset \mathcal{S}_\ell$.
  - E–P shifts to operate over $\mathcal{S}_{\ell+1}$.
- **Emergent curriculum**:
  - Agent naturally explores near its competence boundary.
  - High-$V$ regions become new training grounds.
  - Developmental transitions are bifurcations in the coupled E–P–symbolic system.
  - No external curriculum needed—the loop generates its own scaffolding.

**Proposition (Integration as Core Novelty).**
Neither intrinsic motivation alone (empowerment without symbolic extraction) nor representation learning alone (symbolic extraction without intrinsic selection pressure) produces open-ended development. The integration—E–P selects features, features become new E–P substrates—closes the developmental loop.

---

## 4. Problems with These Mechanisms

- The mechanisms in Section 3 are the best we have.
- They are also structurally limited in ways that *define the research agenda*.

### 4.1 The Entropic Problem

E and P are mutual information quantities. $V_t$ inherits every limitation of information-theoretic optimization. These are not engineering complaints—they are theorem-level structural limitations.

- **Problem 1: Representation presupposition (Shannon 1949)**.
  - Computing $I(A \leadsto O)$ requires well-defined random variables and probability spaces.
  - But choosing the right variables *is* the hard problem.
  - Shannon explicitly excluded semantics from information theory.
  - Consequence: information theory assumes the representation problem is already solved.
  - V3's algebraic learner partially addresses this by providing variables, but the bootstrap remains: initial E–P operates over raw sensorimotor variables whose structure is assumed.
- **Problem 2: Intractability (McAllester & Stratos 2020, Theorem 1)**.
  - *Any distribution-free lower bound on MI estimated from $N$ samples cannot be larger than $O(\ln N)$.*
  - The number of samples required is exponential in the true MI.
  - For small discrete codebooks this softens (finite sums, Blahut-Arimoto tractable).
  - But $n$-step empowerment scales as $|A|^n$, and compositional state spaces explode combinatorially.
  - This is a proven limitation, not a solvable optimization problem.
- **Problem 3: Structural poverty**.
  - Entropy collapses all structure into a scalar.
  - Cannot distinguish algebraic from topological from causal constraints.
  - $V_t = 2EP/(E+P)$ is a single number—blind to the compositional structure of $\mathcal{S}_t$ that it supposedly governs.
  - The harmonic mean does not know about the group theory of the symbolic inventory.
- **Problem 4: Causal blindness (Bareinboim et al. 2022, Causal Hierarchy Theorem)**.
  - $I(X;Y) = I(Y;X)$ by definition. Mutual information is symmetric.
  - But causation is directional.
  - *Causal Hierarchy Theorem: Observational data underdetermines interventional and counterfactual quantities.*
  - E and P are Layer 1 (associational)—can be inflated by confounders and distributional drift.
  - Genuine influence and sensitivity require interventional structure, which MI does not capture.

### 4.2 The Self-Reinforcing Trap

- **The trap structure**:
  - Without symbols → stuck with entropy (your only objectives are statistical).
  - Without non-entropic objectives → no pressure to learn symbols (continuous approximations are always locally sufficient).
  - The subsymbolic-entropic paradigm is self-reinforcing: it defines both representation and objective in terms that exclude the structures that would reveal its limits.
- **V3's position**:
  - V3 attacks both exits—E–P for dynamics, algebraic constraints for symbols.
  - But the tension between the entropic core (E, P are MI) and the algebraic periphery ($\mathcal{S}_t$ has non-entropic structure) is unresolved.
  - The harmonic mean does not know about the group theory.
  - This is not a bug—it points toward what must be built next.

---

## 5. What Needs to Be Done

- The problems in Section 4 are real and foundational, not engineering complaints.
- Here is what must be built.

### 5.1 A Causal, Computationally Tractable Bidirectional Intrinsic Motivation

- **What E–P gets right**: bidirectional, oscillatory, self-regulating + self-amplifying structure.
- **What E–P gets wrong**: current realization in mutual information is both causally blind and intractable at scale.
- **Requirements for successor**:
  - **Causal**: grounded in interventional quantities ($P(O|\text{do}(A))$ not $P(O|A)$), so influence and sensitivity are genuine, not confounded.
  - **Computationally tractable**: not requiring exponential samples or variational bounds that change qualitative behavior.
- **Promising direction**: Gunji and Pegios, "Natural-Born Intelligence as the Invocation of Emotion = Politics"—connects bidirectional engagement to non-information-theoretic quantities that might sidestep the MI trap entirely.

### 5.2 Representation Learning That Does Both Indexing and Feature Extraction

- **Requirements**:
  - **Indexes** the world into discrete, addressable, manipulable symbols (codebook / vocabulary construction).
  - **Extracts features** that are transformation-invariant and algebraically structured (not just compressed statistics).
- **Current methods fail**:
  - VQ-VAE indexes but doesn't extract algebraic structure.
  - Ohmura's algebraic constraints extract structure but don't produce an indexed vocabulary.
- **What's needed**: A system that builds a discrete inventory of structurally meaningful features, where the indexing and the structure are the same thing.

### 5.3 Integration: Representation Learning Constrained by the Mother-of-All-Valleys Intrinsic Motivation

- **The deepest open problem**.
- **Requirement**: The dynamic engagement component (E–P, or its causal successor) should function as a *higher-order constraint* on representation learning.
  - Not just supplying selection pressure for features.
  - But determining *what kind of representations are worth having in the first place*.
- **The "mother of all valleys"**: Intrinsic motivation is the master landscape that all representation learning descends into.
  - Features are valuable not because they compress data.
  - Not because they reconstruct observations.
  - But because they expand the agent's capacity for bidirectional engagement with the world.
- **Constitutive constraint**: Representation learning should be *constitutively constrained* by E–P expansion.
  - Objective for feature extraction: not reconstruction, not contrastive prediction, but E–P expansion.
  - The symbolic and dynamic components are not just coupled—they're aspects of a single process.
  - The agent simultaneously learns *what to attend to* and *how to engage with what it attends to*.

### 5.4 Clarifying Autonomy

- The notion of autonomy underlying all of this must be made explicit.

**Definition (Autonomy, explicit).**
**Autonomy = self-regulation + self-amplification.**

- Not just homeostasis (Wiener/Ashby).
- Not just heterostasis (Klopf).
- Both, coupled, in the same system.

**The dual structure:**

- Self-regulating side (plasticity, negative feedback, accommodation) keeps the system viable.
- Self-amplifying side (empowerment, positive feedback, assimilation) drives it toward expanded engagement.
- Vitality is the measure of how well both are working.

**Convergence:**

- Sepulchre's control-across-scales work demands this.
- Klopf diagnosed its absence in cybernetics.
- Play provides it naturally: a regime where self-regulation and self-amplification are co-constitutive, not in tension.

---

## References

Abel, D., et al. (2025). Plasticity as the Mirror of Empowerment. *arXiv:2505.10361*.

Ay, N. & Polani, D. (2008). Information Flows in Causal Networks. *Advances in Complex Systems*, 11(1).

Bareinboim, E., et al. (2022). On Pearl's Hierarchy and the Foundations of Causal Inference. *ACM Books*.

Bengio, E., et al. (2023). GFlowNet Foundations. *JMLR*, 24.

Ellis, K., et al. (2021). DreamCoder. *PLDI*.

Gunji, Y.-P. & Pegios, A. Natural-Born Intelligence as the Invocation of Emotion = Politics.

Klopf, A.H. (1982). *The Hedonistic Neuron: A Theory of Memory, Learning, and Intelligence*. Hemisphere.

McAllester, D. & Stratos, K. (2020). Formal Limitations on the Measurement of Mutual Information. *AISTATS*.

Ohmura, Y., et al. Algebraic Structural Feedback Control and Genetic Epistemology.

Panksepp, J. (1998). *Affective Neuroscience*. Oxford University Press.

Pearl, J. (2009). *Causality* (2nd ed.). Cambridge University Press.

Piaget, J. (1952). *The Origins of Intelligence in Children*. International Universities Press.

Scannell, A., et al. (2025). Discrete Codebook World Models. *ICLR*.

Sepulchre, R. (2022). Control Across Scales. *Annual Review of Control, Robotics, and Autonomous Systems*.

Trevarthen, C. (1979). Communication and Cooperation in Early Infancy. In *Before Speech*. Cambridge University Press.

van den Oord, A., et al. (2017). Neural Discrete Representation Learning. *NeurIPS*.
