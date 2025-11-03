## Definition

**k-out-of-n Redundancy** refers to system configurations where **k items out of a total of n items are required to survive** to ensure system survival.

This is also known as **Active Parallel Redundancy**.

---

## System Diagram

```
    [1] ───┐
           │
    [2] ───┼──→ k/n ──→ System Output
           │
    [n] ───┘
```

The system has n components operating in parallel. The system functions as long as at least k of these components are working.

---

## Reliability Functions

### For Identical Components

When all components have the same reliability ($R_1 = R_2 = ... = R_n$):

$R_s = \sum_{j=k}^{n} \binom{n}{j} R_i^j (1 - R_i)^{n-j}$

Where:
- $\binom{n}{j} = \frac{n!}{j!(n-j)!}$ is the binomial coefficient
- $R_i$ is the reliability of each identical component
- $j$ represents the number of working components
- The sum goes from $k$ to $n$ (all cases where at least k components work)

**Interpretation:**
- This is a binomial probability formula
- We sum over all possible cases where j components work (where j ≥ k)
- Each term represents: (ways to choose j working components) × (probability j work) × (probability n-j fail)

---

### For Non-Identical Components

When components have different reliabilities ($R_1 \neq R_2 \neq ... \neq R_n$):

$R_s = \left[\sum_{t}\left(\prod_{i} R_i \prod_{j} F_j\right)\right] + \prod_{y=1}^{n} R_y$

Where:
- The sum is over all possible combinations $t$ where at least k components work
- $\prod_i R_i$ is the product of reliabilities for working components
- $\prod_j F_j$ is the product of failure probabilities for failed components ($F_j = 1 - R_j$)
- The last term $\prod_{y=1}^{n} R_y$ represents the case where all components work

**Note:** This formula requires enumeration of all valid combinations and is more complex to calculate. Refer to course notes for the full derivation.

---

## Special Cases

### 1-out-of-n System (Active Parallel)
Only 1 component needs to work for system survival:

$R_s = 1 - \prod_{i=1}^{n} (1 - R_i)$

This is maximum redundancy - all components run simultaneously, and the system survives as long as at least one component is working.

**Note**: This same formula applies to **Standby Parallel** systems (where components are on standby rather than all running). The mathematical formula is identical, but the operational principle differs. See [[Standby Redundancy Explanation]] for standby-specific details.

### n-out-of-n System (Series)
All components must work for system survival:

$R_s = \prod_{i=1}^{n} R_i$

This is no redundancy (series configuration).

### 2-out-of-3 System
Common example: At least 2 out of 3 components must work:

$R_s = \binom{3}{2}R^2(1-R)^1 + \binom{3}{3}R^3(1-R)^0$

$R_s = 3R^2(1-R) + R^3 = 3R^2 - 2R^3$

---

## Practical Applications

- **Voting systems**: 2-out-of-3 voting for safety-critical decisions
- **Aircraft engines**: Multi-engine aircraft that can fly with some engines failed
- **Power systems**: Multiple generators where some can fail
- **Data centers**: Redundant servers where only a subset needs to be operational

---

## Key Takeaways

1. k-out-of-n provides **partial redundancy** between series (n-out-of-n) and full parallel (1-out-of-n)
2. Increasing n (more components) generally increases reliability if k remains fixed
3. For identical components, use the **binomial formula**
4. For non-identical components, must **enumerate all valid combinations**
5. This configuration balances cost (number of components) vs. reliability
