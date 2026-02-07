# Vitality as the Mechanization of Play: The Dual Capacities of Dynamic Engagement and Symbolic Abstraction

**Version 3**

*"The creation of something new is not accomplished by the intellect but by the play instinct acting from inner necessity. The creative mind plays with the objects it loves." — C.G. Jung*

---

## Abstract

We propose Vitality as a formal theory of autonomous development grounded in play. Play — across species and developmental stages — exhibits two complementary capacities: *dynamic bidirectional engagement* (oscillating between influencing and being influenced) and *symbolic abstraction* (operating on meanings and invariants rather than raw percepts). We formalize the first as Empowerment–Plasticity oscillation (Abel et al. 2025) and the second as algebraic constraint learning that extracts discrete, composable, transformation-invariant representations. Their integration — bidirectional engagement generating disciplined interaction, symbolic abstraction extracting reusable structure that becomes substrate for further engagement — constitutes a developmental loop producing open-ended growth without external rewards. We present the best available mechanisms for each capacity, then subject them to two structural critiques: entropic objectives cannot be the highest-level goal for autonomy, and the missing symbolic layer creates a self-reinforcing trap with entropy-based methods. These critiques are not objections to Vitality — they define the research program it points toward.

---

## 1. Play

### 1.1 Observation: Play Is Not Recreation

Play appears across species wherever nervous systems support flexible behavior. The evidence is compelling: Piaget demonstrated that play is central to cognitive construction; Trevarthen showed that intersubjective play founds social cognition, explicitly characterizing it through *vitality affects* and *vitality dynamics* — the reciprocal, temporally structured emotional exchanges between infant and caregiver that scaffold all later development; Panksepp identified dedicated neural circuitry for play that cannot be reduced to other motivational systems. Play has structure — it is not random exploration, but rather a specific behavioral regime characterized by two complementary capacities. The term "vitality" itself has deep roots in developmental psychology, grounding our formalism in the empirical study of dynamic, reciprocal engagement.

### 1.2 First Capacity: Dynamic Bidirectional Engagement

Consider rough-and-tumble play: animals oscillate between influence and receptivity. If one player only pins (pure domination), the game ends. If one player is only pinned (pure submission), the game ends. The game persists if and only if both participants oscillate between affecting and being affected.

We formalize this as two complementary capacities. **Affecting** (empowerment) is the capacity for actions to reliably influence future observations. **Being affected** (plasticity) is the capacity for observations to reliably reshape future actions. The pathologies are instructive: pure empowerment leads to rigidity, pure plasticity to puppetry. Play lives where both capacities are simultaneously high and dynamically balanced.

The oscillatory structure is straightforward: perturb the world, observe the result, update your behavior, re-perturb. When this oscillation collapses, the developmental engine stalls.

### 1.3 Why Both Directions: Klopf's Critique of Cybernetics

Klopf (1982) observed that classical cybernetics — Wiener, Ashby — built a science of homeostasis, negative feedback toward set-points. But living systems are also self-amplifying: they seek stimulation, escalate challenges, pursue novelty. Klopf called this *heterostasis*, the drive toward more rather than back to baseline.

Sepulchre (2022) showed that robust adaptive systems require both positive and negative feedback coupled together. Negative feedback alone converges to a fixed point. Positive feedback alone explodes. Development, learning, and play all require both, coupled.

**Definition (Autonomy).** Autonomy is self-regulation AND self-amplification (homeostasis + heterostasis) operating together as a coupled system. This is not viability. Viability — the maintenance of organismic integrity through negative feedback alone — is purely reactive. A thermostat is viable. Viability requires outside perturbation to produce any behavior; it is self-regulating but not self-amplifying. It keeps you alive but does not generate its own movement.

Genuine autonomy requires both directions coupled. The E–P oscillator exhibits this: when empowerment and plasticity are coupled as a Turing-style dynamical system, the system self-regulates (E regulates P, P regulates E) and self-amplifies (each enhances the other's growth). The oscillator generates its own developmental dynamics without requiring external perturbation. Vitality is this autonomous regime: the E–P engine sustains itself through bidirectional co-regulation, producing self-generated movement. Viability keeps you alive. Vitality makes you autonomous.

### 1.4 Second Capacity: Symbolic Abstraction

Consider pretend play: a child picks up a stick and calls it a sword. The operation is abstract the functional role, map it onto a novel substrate, operate on the abstraction. This is symbolic computation in its most basic form: extract structural invariants from experience, recombine them in novel configurations. Piaget called this accommodation leading to assimilation at higher levels.

The symbolic capacity couples naturally to the dynamic capacity. Active probing discovers transformation-invariant features. Once extracted, these symbols become new control targets. For example, once a child abstracts "tool," they begin seeking control over tool-use at this higher level of abstraction, not just control over individual graspable objects.

### 1.5 The Developmental Loop

**Definition (Play as Developmental Loop).** Play implements a self-organizing developmental cycle:

(a) **Bidirectional engagement** generates disciplined interaction near competence boundary.
(b) **Symbolic abstraction** extracts reusable, transformation-invariant, composable features.
(c) **Projection**: symbols become new E–P substrates—agent oscillates at higher abstraction level.
(d) **Repeat**.

Result: open-ended growth without external rewards or hand-designed curricula.

### 1.6 The Dual-Dual Structure

The two capacities generate a dual-dual architecture. The first duality is dialectical: E and P are mutually regulating opposites whose oscillation constitutes the developmental dynamic. The second is the dual-laws model (Ohmura et al.): feedback error is independently reducible at two levels through orthogonal control mechanisms. Together these produce a natural three-layer phenomenology.

#### Super-Conscious: The E–P Dialectic

The bidirectional engagement layer. Empowerment and plasticity co-regulate each other as a Turing-style oscillator — the pre-symbolic drive that selects what is worth attending to and generates the developmental dynamic. This is the first duality: E without P is rigidity, P without E is dissolution, and the system lives in their oscillation.

#### Conscious: The Symbolic Index Layer

The supervenience level in the dual-laws model. Multiple supervenient functions are combined according to an *index sequence* — a discrete ordering of representational indices that determines which equations govern the system. The indices are for representations: each one selects a particular structured description of the world, and the sequence determines which descriptions are active. Modifying this sequence is Type 2 processing: discrete, exploratory, symbolic. This is where algebraic constraint learning operates — the agent manipulates *which representations to deploy* rather than their continuous solutions.

#### Sub-Conscious: The Neuronal Dynamics Layer

The base level. Neurons and synapses continuously adjust to satisfy whichever equations the index layer specifies. This is Type 1 processing: continuous, goal-directed, subsymbolic. The dual-laws insight is that both levels operate independently on the same error signal through orthogonal degrees of freedom.

Since Type 2 is inherently discrete, it plausibly becomes advanced in organisms with sophisticated linguistic capacities — language itself being an index system. There is no reason to think Type 2 is uniquely human, but its elaboration likely tracks the capacity for discrete symbolic recombination.

---

## 2. Vitality: Formalizing Play

### 2.1 Setup

We work with an agent whose state space $\mathcal{X}$ is partitioned into internal state $Y_t$ and world state $W_t$. The agent interacts through an interface $\lambda$ consisting of actions $A_{1:T}$ and observations $O_{1:T}$. Policies $\pi$ induce trajectory distributions over this joint space.

### 2.2 Formalizing Bidirectional Engagement

**Definition (Empowerment).**
$$E_t(\lambda) := I(A \leadsto O;\, \lambda)_t$$
Channel capacity for actions to influence future observations.

**Definition (Plasticity).**
$$P_t(\lambda) := I(O \leadsto A;\, \lambda)_t$$
Channel capacity for observations to reshape future actions.

**Proposition (Abel Tradeoff).**
$E_t + P_t \leq m_t(\lambda)$, where $m_t(\lambda)$ is interface-dependent upper bound.

**Vitality as Co-Regulatory Regime.** Vitality is the Turing-esque dynamical pattern where empowerment and plasticity co-regulate each other: E regulates P (influencing the world shapes what reconfigures you), P regulates E (reconfigurability sustains influence in non-stationary environments). This is a specific behavioral regime, not just a number.

**Definition (Vitality Measure, time-local).**
$$V_t(\lambda) := \frac{2\,E_t\, P_t}{E_t + P_t}$$
This harmonic mean measures the strength of the co-regulatory regime at time $t$. It requires both E and P positive, penalizes extremes, and reaches maximum when $E_t = P_t$.

### 2.3 Temporal Morphogens

**Definition (Internalization).**
Interface capacities (fast measurements) internalized as slow state:
$$\mathcal{E}_{t+1} = (1 - \alpha_E)\mathcal{E}_t + \alpha_E\, E_t(\lambda), \qquad \mathcal{P}_{t+1} = (1 - \alpha_P)\mathcal{P}_t + \alpha_P\, P_t(\lambda)$$

Here $\mathcal{E}_t$ is a slow "skill/commitment" morphogen and $\mathcal{P}_t$ is a slow "reconfigurability" morphogen.

**Knowledge as self-persisting information.** The morphogens are not merely statistics about past interaction — they are *knowledge* in the constructionist sense. Following Piaget's insight that knowledge is not stored data but self-maintaining structure, we recognize that $\mathcal{E}_t$ and $\mathcal{P}_t$ are the agent's consolidated developmental history, actively maintaining themselves through the E–P loop. They persist not because they are written to memory, but because they regulate the very interactions that regenerate them. This is knowledge as self-persisting information: the morphogens ARE what the agent has learned, and they persist precisely because they shape how the agent continues to engage with the world.

**Structure.** The morphogens modulate the fast loop: adaptation strength is proportional to $f(\mathcal{P}_t)$ while stability and precision are proportional to $g(\mathcal{E}_t)$. This creates a reaction–diffusion structure where $\mathcal{E}$ acts as activator (stabilizing) and $\mathcal{P}$ acts as inhibitor (destabilizing). The different timescales — $\alpha_P \ll \alpha_E$, making plasticity slow to recruit but fast to act — produce temporal Turing patterns: alternating plateau phases (exploit, high $\mathcal{E}$, low $\mathcal{P}$) and burst phases (explore, recruited $\mathcal{P}$). Developmental transitions emerge as bifurcations between behavioral regimes.

### 2.4 Formalizing Symbolic Abstraction

Given observations $\{o_t\}$ from interaction, we learn an encoder $\phi: \mathcal{O} \to \mathcal{Z}$ mapping into a factored latent space $\mathcal{Z} = \mathcal{Z}_1 \times \cdots \times \mathcal{Z}_k$. The requirements are threefold: (1) **group-theoretic decomposition**, where each $\mathcal{Z}_i$ transforms independently under a subgroup $G_i$; (2) **transformation invariance**, where each factor captures a structural invariant reusable across contexts; and (3) **discretizability**, where factors are naturally discretizable (finite groups, discrete orbits), yielding a vocabulary of *perceptual symbols*.

**Definition (Symbolic Inventory).**
$\mathcal{S}_t = \{(\mathcal{Z}_i, G_i, \phi_i)\}_{i=1}^{k_t}$ grows over development.

### 2.5 The Integrated Definition

**Definition (Vitality, Version 3).**
A system exhibits Vitality over horizon $T$ if it sustains the E–P co-regulatory regime with the following properties:

1. **High dynamic engagement**: $\bar{V}_T$ sustained above threshold, indicating strong bidirectional coupling between empowerment and plasticity.
2. **Growing symbolic inventory**: $|\mathcal{S}_T| > |\mathcal{S}_0|$ (reusable abstractions extracted from the interaction data generated by E–P oscillation).
3. **Loop closure**: learned symbols become new E–P substrates, so empowerment–plasticity dynamics shift to operate over symbolic space, not just raw sensorimotor channels.

The distinguishing feature is condition (3). This is not simply "intrinsic motivation + representation learning." The loop closes: symbols are recruited into control, which generates new interactions, which extract further abstractions.

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

Abel et al. (2025) formalize plasticity as the dual of empowerment within generalized directed information. They define channel capacities in both directions — forward ($A \to O$) and reverse ($O \to A$) — and prove a tight tradeoff: $E + P \leq m(\lambda)$. The interface has finite bidirectional capacity, and any allocation must respect this bound.

Internalizing E and P as slow morphogens yields reaction–diffusion structure. The plateau phase (high $\mathcal{E}$, low $\mathcal{P}$) corresponds to exploitation. The burst phase (recruited $\mathcal{P}$) corresponds to exploration. This maps directly onto the explore–exploit oscillation familiar from reinforcement learning, but here it emerges from the coupled morphogen dynamics rather than being imposed externally. Developmental transitions emerge as bifurcations in this dynamical system.

### 3.2 For Symbolic Abstraction

The algebraic constraint learning framework (Ohmura et al.) biases feature discovery toward group-theoretic decompositions. It separates conditionally independent transformations, yielding features that are operationally meaningful, naturally discretizable, and composable.

Discrete codebook methods provide complementary techniques. VQ-VAE constructs discrete latent representations via vector quantization. Discrete Codebook World Models (Scannell et al. 2025) preserve ordinal relationships while maintaining discreteness. GFlowNets (Bengio et al. 2023) navigate discrete combinatorial structure with neural guidance, allowing flexible exploration of symbolic spaces.

DreamCoder (Ellis et al. 2021) bootstraps compositional program libraries through wake-sleep cycles. Its discrete, composable building blocks grow over time, providing a model of how symbolic inventories can expand through use.

### 3.3 For the Integration

The integration of dynamic engagement with symbolic abstraction is the core novelty. Current representation learning and intrinsic motivation frameworks fail because they address one side without the other.

#### E–P as Selection Pressure for Representation Learning

Representation learning suffers from an underdetermination problem: in unsupervised settings, infinitely many representations compress the data equally well. There is no principled selection criterion beyond reconstruction error or contrastive loss. The result is that learned features may be statistically optimal but behaviorally useless.

E–P provides the missing selection pressure. A feature $z$ is valuable if and only if it expands both $E$ (controllability via $z$) and $P$ (sensitivity to $z$). This is a functional criterion: features must support bidirectional coupling. It filters out features that compress well but don't enable better engagement.

The formal mechanism is straightforward. At time $t$, the agent has symbolic inventory $\mathcal{S}_t = \{z_1, \ldots, z_k\}$. For each symbol $z \in \mathcal{S}_t$, compute $E_t(\lambda_z)$ and $P_t(\lambda_z)$ — the empowerment and plasticity available when controlling or observing through $z$. Features with high vitality $V_t(\lambda_z) = 2E_t(\lambda_z)P_t(\lambda_z)/(E_t(\lambda_z)+P_t(\lambda_z))$ are retained and elaborated. Features with low $V_t(\lambda_z)$ are pruned or not extracted in the first place. This implements developmental filtering: the dynamic layer shapes what the symbolic layer learns.

#### Symbols as New E–P Substrates

Once extracted, symbols $z \in \mathcal{S}_t$ become new control and observation targets. The E–P dynamics shift from sensorimotor space $(A, O)$ to symbolic space $(Z_A, Z_O)$. The agent now seeks to influence and be influenced at the level of abstractions, not raw percepts.

A Piaget-style example clarifies this. At the sensorimotor stage, E–P operates over raw actions (grasp, release) and observations (visual flow, tactile feedback). At the object stage, the agent abstracts "graspable object," and E–P now operates over object-level actions ("grab the cup") and object-level observations ("cup moved"). At the relational stage, the agent abstracts "containment," and E–P operates over relational actions ("put A in B") and relational observations ("A is inside B"). Each level's symbols become the substrate for the next level's E–P oscillation.

This closes the loop. Symbols extracted from E–P data at level $n$ become E–P targets at level $n+1$. This is recursive abstraction: the mechanism that generates symbols also consumes them. Contrast this with static representation learning, where features are extracted once and used for downstream tasks but not fed back into the feature-extraction process itself.

#### Hierarchical Developmental Dynamics

The developmental trajectory looks like this:
$$\text{sensorimotor} \xrightarrow{\text{E–P + abstraction}} \text{object} \xrightarrow{\text{E–P + abstraction}} \text{relational} \xrightarrow{\text{E–P + abstraction}} \text{social}$$

At each level $\ell$, E–P oscillates over the current symbolic inventory $\mathcal{S}_\ell$, generating interaction data at level $\ell$. The algebraic constraint learner extracts new symbols $\mathcal{S}_{\ell+1} \supset \mathcal{S}_\ell$, and E–P shifts to operate over $\mathcal{S}_{\ell+1}$.

This produces an emergent curriculum. The agent naturally explores near its competence boundary. High-$V$ regions become new training grounds. Developmental transitions are bifurcations in the coupled E–P–symbolic system. No external curriculum is needed — the loop generates its own scaffolding.

**Proposition (Integration as Core Novelty).**
Neither intrinsic motivation alone (empowerment without symbolic extraction) nor representation learning alone (symbolic extraction without intrinsic selection pressure) produces open-ended development. The integration—E–P selects features, features become new E–P substrates—closes the developmental loop.

---

## 4. Problems with These Mechanisms

The mechanisms in Section 3 are the best we have. They are also structurally limited in ways that define the research agenda.

### 4.1 The Entropic Problem

E and P are mutual information quantities. $V_t$ inherits every limitation of information-theoretic optimization. These are not engineering complaints—they are theorem-level structural limitations.

**Problem 1: Representation presupposition (Shannon 1949).** Computing $I(A \leadsto O)$ requires well-defined random variables and probability spaces. But choosing the right variables is the hard problem. Shannon explicitly excluded semantics from information theory. The consequence is that information theory assumes the representation problem is already solved. V3's algebraic learner partially addresses this by providing variables, but the bootstrap remains: initial E–P must operate over raw sensorimotor variables whose structure is assumed.

**Problem 2: Intractability (McAllester & Stratos 2020, Theorem 1).** Any distribution-free lower bound on MI estimated from $N$ samples cannot be larger than $O(\ln N)$. The number of samples required is exponential in the true MI. For small discrete codebooks this softens (finite sums, Blahut-Arimoto becomes tractable), but $n$-step empowerment scales as $|A|^n$, and compositional state spaces explode combinatorially. This is a proven limitation, not a solvable optimization problem.

**Problem 3: Structural poverty.** Entropy collapses all structure into a scalar. It cannot distinguish algebraic from topological from causal constraints. $V_t = 2EP/(E+P)$ is a single number, blind to the compositional structure of $\mathcal{S}_t$ that it supposedly governs. The harmonic mean does not know about the group theory of the symbolic inventory.

**Problem 4: Causal blindness (Bareinboim et al. 2022, Causal Hierarchy Theorem).** Mutual information is symmetric by definition: $I(X;Y) = I(Y;X)$. But causation is directional. The Causal Hierarchy Theorem states that observational data underdetermines interventional and counterfactual quantities. E and P are Layer 1 (associational) — they can be inflated by confounders and distributional drift. Genuine influence and sensitivity require interventional structure, which MI does not capture.

### 4.2 The Self-Reinforcing Trap

The trap has two exits, both blocked. Without symbols, you are stuck with entropy — your only objectives are statistical. Without non-entropic objectives, there is no pressure to learn symbols — continuous approximations are always locally sufficient. The subsymbolic-entropic paradigm is self-reinforcing: it defines both representation and objective in terms that exclude the structures that would reveal its limits.

V3 attacks both exits. E–P provides the dynamics, algebraic constraints provide the symbols. But the tension between the entropic core (E and P are mutual information) and the algebraic periphery ($\mathcal{S}_t$ has non-entropic structure) remains unresolved. The harmonic mean does not know about the group theory. This is not a bug. It points toward what must be built next.

---

## 5. What Needs to Be Done

The problems in Section 4 are real and foundational, not engineering complaints. Here is what must be built.

### 5.1 A Causal, Computationally Tractable Bidirectional Intrinsic Motivation

E–P gets the structure right: bidirectional, oscillatory, self-regulating plus self-amplifying. But the current realization in mutual information is both causally blind and intractable at scale.

The requirements for a successor are clear. It must be causal: grounded in interventional quantities ($P(O|\text{do}(A))$ not $P(O|A)$), so that influence and sensitivity are genuine rather than confounded. And it must be computationally tractable: not requiring exponential samples or variational bounds that change qualitative behavior.

A promising direction is Gunji and Pegios, "Natural-Born Intelligence as the Invocation of Emotion = Politics," which connects bidirectional engagement to non-information-theoretic quantities that might sidestep the MI trap entirely.

### 5.2 Representation Learning That Does Both Indexing and Feature Extraction

The requirements are twofold: the system must index the world into discrete, addressable, manipulable symbols (codebook or vocabulary construction), and it must extract features that are transformation-invariant and algebraically structured (not just compressed statistics).

Current methods fail at the intersection. VQ-VAE indexes but doesn't extract algebraic structure. Ohmura's algebraic constraints extract structure but don't produce an indexed vocabulary. What's needed is a system that builds a discrete inventory of structurally meaningful features, where the indexing and the structure are the same thing.

### 5.3 Integration: Representation Learning Constrained by the Mother-of-All-Values Intrinsic Motivation

This is the deepest open problem. The dynamic engagement component — E–P, or its causal successor — should function as a higher-order constraint on representation learning, not just supplying selection pressure for features but determining what kind of representations are worth having in the first place.

Intrinsic motivation is the mother of all values, the master landscape that all representation learning descends into. Features are valuable not because they compress data, not because they reconstruct observations, but because they expand the agent's capacity for bidirectional engagement with the world.

Representation learning should be constitutively constrained by E–P expansion. The objective for feature extraction should not be reconstruction or contrastive prediction, but E–P expansion itself. The symbolic and dynamic components are not just coupled — they are aspects of a single process. The agent simultaneously learns what to attend to and how to engage with what it attends to.

### 5.4 Clarifying Autonomy

The notion of autonomy underlying all of this must be made explicit.

**Definition (Autonomy, explicit).**
**Autonomy = self-regulation + self-amplification.**

This is not just homeostasis (Wiener, Ashby). Not just heterostasis (Klopf). Both, coupled, in the same system.

This definition distinguishes autonomy from viability. Viability is purely negative feedback — self-regulation without self-amplification. A thermostat is viable. It maintains a set-point through reactive correction, but it does not generate its own movement. Viability requires external perturbation to produce behavior. An organism can be viable (persist as a coherent entity through homeostatic regulation) without being autonomous in the sense we mean here.

Genuine autonomy requires the E–P oscillator. When empowerment and plasticity are coupled as a dynamical system, that coupled system is autonomous. E regulates P (influencing the world shapes what can reconfigure you), and P regulates E (reconfigurability sustains influence in non-stationary environments). The oscillator self-regulates through this bidirectional coupling. Simultaneously, E and P mutually amplify each other: expanded empowerment generates richer feedback for plasticity, and expanded plasticity enables more sophisticated empowerment. The E–P engine generates its own developmental dynamics. It does not wait for perturbation — it produces self-generated movement.

Vitality is this autonomous regime. The E–P oscillator sustains itself through bidirectional co-regulation. $V_t$ measures the strength of this regime, but vitality itself is the pattern of E–P co-regulation, not the score. Viability keeps you alive. Vitality makes you autonomous.

The convergence is striking. Sepulchre's control-across-scales work demands this dual structure. Klopf diagnosed its absence in cybernetics. Play provides it naturally: a regime where self-regulation and self-amplification are co-constitutive, not in tension.

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
