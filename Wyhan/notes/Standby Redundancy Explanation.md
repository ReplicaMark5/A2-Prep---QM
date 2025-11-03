## Definition

**Passive (Standby) Redundancy** is a reliability configuration where one component operates continuously as the primary unit, while backup components remain on standby. These standby components are only activated when the primary component fails.

**Key Characteristics**:
- One component operates at a time
- Standby components do not fail while inactive (idealized assumption)
- Switching mechanism activates backup when primary fails
- Modeling is more complex because activation time is a variable

---

## System Diagram

```
Primary ──→ [1] ─┐
                 │
Standby ─→ [2] ─┼──→ Switch (S) ──→ System Output
                 │
Standby ─→ [n] ─┘
```

The switch (S) detects primary failure and activates a standby component.

---

## General Formula

For **any components** (identical or non-identical, with any reliability function):

$R = 1 - \prod_{i=1}^{w} (1 - R_i)$

Where:
- $R_i$ is the reliability of component $i$
- $w$ is the total number of components
- This assumes perfect switching and no standby failures

**Interpretation**:
- This is equivalent to a parallel system formula
- System fails only when ALL components fail
- Works for any reliability distributions

**When to Use**: When components have different reliabilities or non-constant failure rates.

---

## Special Case: Constant Failure Rate (CFR)

When we can assume:
- **Constant failure rate**: $\lambda = \frac{1}{\mathrm{MTBF}}$
- **Identical components**: All components have the same $\lambda$
- **Perfect switching**: Instantaneous and error-free

We can use simplified **Poisson-based formulas** that account for time:

---

### For n=2 Components

$R_s = (1 + \lambda t) e^{-\lambda t}$

Where:
- $\lambda$ is the constant failure rate
- $t$ is the mission time
- $\lambda = \frac{1}{\mathrm{MTBF}}$

**Interpretation**:
- First term $(1 + \lambda t)$ accounts for both components working or one failing during $t$
- Second term $e^{-\lambda t}$ is the exponential reliability function
- Special case of the general n-component formula with n=2

---

### For n Components

$R_s = e^{-\lambda t} \sum_{i=0}^{n-1} \frac{(\lambda t)^i}{i!}$

Where:
- $n$ is the total number of identical components
- Sum represents Poisson probability that fewer than n failures occur by time $t$

**Interpretation**:
- This is the complement of the Poisson CDF
- System survives if fewer than $n$ failures occur
- Each term $\frac{(\lambda t)^i}{i!}$ represents probability of exactly $i$ failures

**Derivation Connection**: This comes from the Poisson process representing the number of failures over time with constant rate $\lambda$.

---

### For k-out-of-n System

When the system requires **at least k components to survive** (not just 1):

$R_s = e^{-k\lambda t} \sum_{i=0}^{n-k} \frac{(k\lambda t)^i}{i!}$

Where:
- $k$ is the minimum number of components needed
- $n$ is the total number of components
- This is a hybrid: standby redundancy with k-out-of-n requirement

**Interpretation**:
- Effective failure rate becomes $k\lambda$ (since k components must survive)
- Sum goes from 0 to $n-k$ (maximum allowable failures)
- Combines standby logic with k-out-of-n reliability

---

## Active vs. Passive Comparison

| Aspect | Active Parallel | Passive (Standby) |
|--------|----------------|-------------------|
| **Operation** | All components operate simultaneously | Only one operates, others on standby |
| **Failures** | Components fail even when not in use | Standby components ideally don't fail |
| **Switching** | No switching needed | Requires switching mechanism |
| **Complexity** | Simpler to model | More complex (time-dependent) |
| **Reliability** | Generally lower (all components aging) | Generally higher (standbys preserved) |
| **Formula** | $R = 1 - \prod(1-R_i)$ or binomial | Same general form, but CFR special cases |

---

## When to Use Which Formula

### Use General Formula
- Components have **non-constant failure rates** (e.g., Weibull distribution)
- Components are **non-identical** (different $R_i$)
- Simple reliability calculation needed without time dependency

### Use CFR Poisson Formulas
- Constant failure rate assumption holds (exponential distribution)
- All components are **identical**
- Need **time-dependent reliability** $R(t)$
- More accurate modeling of standby behavior over time

---

## Practical Applications

- **Backup generators**: Main power with standby generator
- **Spare tires**: Primary tires with spare in trunk
- **Redundant pumps**: Active pump with standby backup
- **IT systems**: Primary server with hot/cold standby
- **Aircraft hydraulics**: Primary system with emergency backup

---

## Key Takeaways

1. **Standby redundancy** preserves backup components until needed
2. **General formula** works for any reliability, but doesn't account for time
3. **CFR formulas** (Poisson models) provide time-dependent reliability for identical components
4. **Perfect switching** is an idealized assumption (real switches can fail)
5. Standby typically provides **better reliability** than active parallel for same number of components
6. The **n=2 case** has a simple closed-form solution: $(1 + \lambda t)e^{-\lambda t}$
