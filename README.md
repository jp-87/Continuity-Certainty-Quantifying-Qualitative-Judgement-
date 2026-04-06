# Continuity & Certainty — Quantifying Qualitative Judgement

AI attempts to quantify an inherently qualitative judgment using peer-reviewed concepts. It formalizes six theoretical frameworks from three different academic disciplines into a single computable diagnostic prompt.

**Current version:** [v2.0 Framework](FRAMEWORK.md) *(effective 04/06/2026)*

## Overview

The framework is grounded in Signal Detection Theory, Bayesian Epistemology, and Information Theory. It provides a structured rubric for evaluating the epistemic quality and ideological coherence of discourse across six diagnostic dimensions:

| Dimension | Theorist(s)          |
|-----------|----------------------|
| A         | Austin               |
| B         | Situationist         |
| C         | Luhmann              |
| D         | Althusser / Žižek    |
| E         | Sloterdijk           |
| F         | Žižek                |

## Changelog

### v2.0 (04/06/2026)
- All previously undefined constants now explicitly defined (θ_useful, θ_high, θ_fp, θ_depth, θ_switch, p_unit)
- `c₃` replaced permeability with structural_coupling_adequacy (Luhmann)
- `d₃` replaced "emergy" with material substrate detection rate (Althusser)
- `d₅` renamed to Ideological Excess Detection; cynical_reason removed
- `e₃` prior corrected to naïve ideological position (Sloterdijk)
- `e₅` now exclusively holds cynical_reason detection
- Paradox penalty trigger₂ dropped; trigger₃ added (convention_incompatibility)
- Cross-dimension deduplication rules added (§2.1) to eliminate d₅/f₅ and e₂/f₁ weight overlap
- test_cases and remediation made strictly optional in output schema

### v1.0
- Initial in-house prototype
