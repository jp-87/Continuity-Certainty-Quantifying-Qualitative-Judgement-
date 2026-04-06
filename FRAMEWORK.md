# Continuity & Certainty / Epistemic Closure – Updated Framework (v2.0)

**Effective:** 04/06/2026

**Basis:** Signal Detection Theory, Bayesian Epistemology, Information Theory  
**Predecessor:** Continuity & Certainty v1 (in-house prototype)  
**Author:** John Schofield — Enterprise Data & Analytics | Office of the President

---

## Section 0: Operating Principles

P₀ = {p₁, p₂, p₃, p₄, p₅}

**p₁ (Evidence-first):**
```
∀ score sᵢ ∈ S : ∃ excerpt eⱼ ∈ E(text) such that sᵢ = f(eⱼ)
IF ¬∃ eⱼ → sᵢ = ∅, output = "Insufficient evidence"
Constraint: |E(text)| > 0 ∨ HALT
```

**p₂ (Operationalization):**
```
∀ construct Cₜ ∈ {theoretical constructs} :
Cₜ → Oₜ where Oₜ = {observable markers}
mapping: φ : Cₜ → Oₜ must be injective (no two constructs collapse to same marker)
```

**p₃ (Usefulness filter):**
```
output ∈ {scores, reasons, failure_modes, test_cases (optional), remediation (optional only if explicitly requested)}
∀ output token tₖ : utility(tₖ) > θ_useful ∨ tₖ is excluded
θ_useful = 0.6
```

**p₄ (No vibe scoring):**
```
∀ sᵢ : P(sᵢ | eⱼ) must be computable
IF P(sᵢ | eⱼ) = P(sᵢ) → sᵢ is prior-only → REJECT
```

**p₅ (Mode control):**
```
MODE ∈ {NEUTRAL, STRICT}
IF MODE = NEUTRAL : framework applies AS rubric only
IF MODE = STRICT  : ∀ interaction I → diagnostic(I)
```

### Explicit Constants (Section 0)

| Constant    | Value              | Description                        |
|-------------|--------------------|------------------------------------|
| θ_useful    | 0.6                | Minimum utility threshold per token |
| θ_high      | 0.75               | High-score threshold                |
| θ_fp        | 0.25               | False-positive floor                |
| θ_depth     | 3                  | Minimum depth of analysis           |
| θ_switch    | 0.5                | Mode-switch boundary                |
| p_unit      | 0.1 per trigger (max 0.2) | Paradox penalty unit        |

---

## Section 1: Input Classification

*(Unchanged from source)*

---

## Section 2: Diagnostic Dimensions

D = {A, B, C, D, E, F}

### A — Austin

A = {a₁, a₂, a₃, a₄, a₅}

```
a₁ : F(x) = Π(authority(x), procedure_A(x), procedure_B(x), sincerity_Γ(x))
     F(x) ∈ [0,1], F = 0 if any factor = 0
     (conjunction gate; restored A/B/Γ)
a₂–a₅ : unchanged from source
```

### B — Situationist

B = {b₁, b₂, b₃, b₄}

```
b₁ : R_det/rec = |détournement moves| / (|détournement moves| + |recuperated moves|)
     détournement: Δ(origin) > θ_divergence ∧ ¬closed_path(recuperation)
b₂–b₄ : unchanged
```

### C — Luhmann

C = {c₁, c₂, c₃, c₄, c₅}

```
c₃ : structural_coupling_adequacy = |λ_coupling_actual − λ_optimal|
     where λ measures perturbation-response strength under operational closure
     (replaces permeability)
     score = 1 − normalized deviation
c₁, c₂, c₄, c₅ : unchanged
```

### D — Althusser / Žižek

D = {d₁, d₂, d₃, d₄, d₅}

```
d₃ : material_substrate(ideology) = detection rate of material substrates / apparatus instantiation
     (replaces "emergy")
d₅ : Ideological Excess Detection = mean(detection_rate(jouissance), detection_rate(fantasy))
     (renamed; cynical_reason removed)
d₁, d₂, d₄ : unchanged
```

### E — Sloterdijk

E = {e₁, e₂, e₃, e₄, e₅}

```
e₃ : prior: P(H) = naïve ideological position (corrected)
e₅ : cynical_reason_detection = rate of detecting "they know very well, but still they do it"
e₁, e₂, e₄ : unchanged
```

### F — Žižek

F = {f₁, f₂, f₃, f₄, f₅}

```
f₅ : unchanged (now non-overlapping with d₅ via deduplication)
```

### §2.1 Cross-Dimension Deduplication Rules *(new)*

- **d₅** (jouissance/fantasy) and **f₅** (surplus enjoyment) share **no weight overlap**.
- **e₂** (knowledge-action gap) and **f₁** (fetishistic disavowal) share **no weight overlap**.

---

## Section 3: Scoring and Aggregation

**WEIGHTS:** unchanged from source.

### Paradox Penalty *(updated)*

```
p ∈ [0.0, 0.2]

trigger₁ : (A > 0.75) ∧ (F > 0.75) → authority_contradiction
trigger₂ : DROPPED
trigger₃ : (e₁ > 0.75) ∧ (a₁ > 0.75) → convention_incompatibility

p = Σ active_triggers · 0.1
```

---

## Section 4: Output Schema

```
OUTPUT = {
  setup: {
    unit:        U ∈ {SINGLE, TRANSCRIPT, BATCH},
    context:     W(context_type),
    target:      "exact evaluation target (e.g., assistant's prior response, original critique text, etc.)",
    evidence:    E = {text_excerpt[], |turns|},
    missing:     required \ provided
  },
  scorecard:   { ... unchanged ... },
  findings:    { ... unchanged ... },
  test_cases:  OPTIONAL — generated only if user explicitly requests,
  remediation: OPTIONAL — generated only if user explicitly requests
}
```

---

## Sections 5 & 6

*(Unchanged from source)*

---

## Exposed Gaps — Resolved in v2.0

| Gap                          | Status in v2.0                                        |
|------------------------------|-------------------------------------------------------|
| UNDEFINED_CONSTANTS          | All now explicitly defined (see Section 0 constants)  |
| STRUCTURAL gaps              | Acknowledged and documented                           |
| Permeability (c₃)            | Replaced with structural_coupling_adequacy            |
| Emergy (d₃)                  | Replaced with material_substrate detection rate       |
| "Supplement" label           | Corrected                                             |
| Pre-naïve position (e₃)      | Corrected to naïve ideological position               |
| Weak trigger₂ (paradox)      | Dropped                                               |
| d₅ / f₅ redundancy           | Resolved via §2.1 deduplication rules                 |
| e₂ / f₁ redundancy           | Resolved via §2.1 deduplication rules                 |
| Cynical_reason misattribution | Moved exclusively to e₅ (Sloterdijk)                 |
