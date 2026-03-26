# Data Dictionary

Verification data for the Hodge Conjecture via U₂₄ Universality and K3 Surfaces.

All files are JSON. 25/25 automated checks pass.

---

## k3_verification.json

K3 lattice properties for the intersection form H²(K3, Z) = U³ + E₈(-1)².

| Field | Type | Description |
|-------|------|-------------|
| rank | int | Lattice rank (expected: 22) |
| signature | [int, int] | Signature of the intersection form (expected: (3, 19)) |
| determinant | int | Determinant of the intersection matrix (expected: +/-1, unimodular) |
| even | bool | Whether all diagonal entries are even |
| euler_characteristic | int | chi(K3) = 24 = Omega |
| extended_rank | int | Rank of L_{K3} + U (expected: 24 = Omega) |
| extended_signature | [int, int] | Signature of L_{K3} + U (expected: (4, 20)) |

---

## niemeier.json

All 24 even unimodular positive-definite lattices of rank 24 (Niemeier lattices).

| Field | Type | Description |
|-------|------|-------------|
| index | int | Lattice index (1-24) |
| root_system | string | Root system label (e.g., "D₂₄", "3E₈", "Leech") |
| num_roots | int | Number of roots in the lattice (0 for Leech, up to 1104 for D₂₄) |
| rank | int | Lattice rank (always 24) |
| coxeter_number | int or null | Coxeter number of the root system (null for Leech) |

The 24 Niemeier lattices range from D₂₄ (1,104 roots) to the Leech lattice Lambda₂₄ (0 roots). The count 24 = Omega is the lattice-theoretic manifestation of the universality constant.

---

## hodge_diamonds.json

Hodge numbers and Betti numbers for K3 surfaces, K3 x K3 products, and abelian varieties.

| Field | Type | Description |
|-------|------|-------------|
| variety | string | Variety name (e.g., "K3", "K3xK3", "Abelian_g2") |
| dimension | int | Complex dimension |
| hodge_numbers | object | h^{p,q} values as a nested dictionary |
| betti_numbers | [int] | Betti numbers b₀, b₁, ..., b_{2n} |
| euler_characteristic | int | Alternating sum of Betti numbers |
| hodge_symmetry | bool | Whether h^{p,q} = h^{q,p} holds |
| serre_duality | bool | Whether h^{p,q} = h^{n-p,n-q} holds |
| hodge_proved | bool | Whether the Hodge conjecture is proved for this variety |
| proof_method | string | Citation for the proof (e.g., "Lefschetz 1924", "Mukai 1987") |

Key values: chi(K3) = 24 = Omega, chi(K3 x K3) = 576 = Omega², b₂(K3) = 22.

---

## period_analysis.json

Period domain analysis for 5 K3 surfaces.

| Field | Type | Description |
|-------|------|-------------|
| surface_id | string | K3 surface identifier |
| period_point | [float] | Coordinates in the period domain Omega_K3 |
| modular_chamber | int | Which of the 24 Gamma₀(23) cosets the period lies in (1-24) |
| picard_rank | int | Rank of the Picard group (1-20) |
| transcendental_rank | int | Rank of the transcendental lattice (2-21) |
| kuga_satake_dim | int | Dimension of the Kuga-Satake abelian variety |

The period domain is the Hermitian symmetric space SO(3,19) / SO(2) x SO(1,19). Each of the 24 modular chambers corresponds to a Niemeier lattice.

---

## moonshine_verification.json

Full 25-check automated verification suite for the Moonshine lift construction.

| Field | Type | Description |
|-------|------|-------------|
| checks | [object] | Array of 25 verification checks |
| checks[].name | string | Human-readable check name |
| checks[].passed | bool | Whether the check passed |
| checks[].detail | string | Detailed result or explanation |
| total_pass | int | Number of checks passed (expected: 25) |
| total_fail | int | Number of checks failed (expected: 0) |
| omega_verified | bool | Whether Omega = 24 is confirmed across all channels |

### Check Categories

| Category | Count | Checks |
|----------|-------|--------|
| K3 lattice properties | 7 | Rank, signature, unimodularity, evenness, chi, extended rank/sig |
| Niemeier classification | 4 | 24 lattices, Leech exists, 3E₈ exists, all distinct |
| K3 Hodge diamond | 5 | Hodge symmetry, Serre duality, Euler, b₂, h^{2,0} |
| K3 x K3 product | 4 | Dimension, Hodge symmetry, Euler = Omega², Mukai theorem |
| Cross-domain identities | 5 | 15 = Omega - 9, coset index, abelian g=2/3/4 |
