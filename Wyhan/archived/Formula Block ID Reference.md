# Formula Block ID Reference Guide

This document lists all block IDs for formulas in the Sample formula sheet. Use these IDs to reference specific formulas from your worked examples.

---

## How to Use Block IDs

### Link to a formula:
```markdown
See formula: [[Sample formula sheet#^rel-series]]
```

### Embed a formula:
```markdown
Using: ![[Sample formula sheet#^weibull-pdf]]
```

### Link with custom text:
```markdown
Apply the [[Sample formula sheet#^rho1-mtbf|MTBF formula for ρ₁]]
```

---

## 📋 Complete Block ID List

### Reliability Modelling

| Formula | Block ID | Description |
|---------|----------|-------------|
| Series Systems | `^rel-series` | $R=\prod_{i=1}^{w} R_{i}$ |
| Active Parallel - Identical | `^rel-active-parallel-identical` | Binomial formula for k-out-of-w |
| Standby Parallel - General | `^rel-standby-general` | General standby formula |
| Active Parallel - Non-Identical | `^rel-active-parallel-nonidentical` | Complex system formula |
| Poisson n=2 | `^rel-poisson-n2` | Standby with 2 components (CFR) |
| Poisson n components | `^rel-poisson-n` | Standby with n components (CFR) |
| Poisson k-out-of-n | `^rel-poisson-koon` | Standby k-out-of-n (CFR) |
| Importance Measure | `^rel-importance` | Component importance |

---

### Laplace Trend Test

| Formula | Block ID | Description |
|---------|----------|-------------|
| U Statistic | `^laplace-u-statistic` | Laplace trend test statistic |

---

### Non-repairable Components (Weibull)

| Formula | Block ID | Description |
|---------|----------|-------------|
| PDF | `^weibull-pdf` | Probability density function |
| CDF | `^weibull-cdf` | Cumulative distribution function |
| Reliability | `^weibull-reliability` | Reliability function |
| Hazard Rate | `^weibull-hazard` | Hazard rate function |
| Expected (Conditional) | `^weibull-expected-conditional` | E[X_{r+1} \| X_{r+1} ≤ X_P] |
| μ (Conditional) | `^weibull-mu-conditional` | μ_{r+1} conditional |
| Expected (Unconditional) | `^weibull-expected-unconditional` | E[X_{r+1}] |
| μ (Unconditional) | `^weibull-mu-unconditional` | μ_{r+1} unconditional |

---

### Repairable Systems - Model ρ₁

| Formula | Block ID | Description |
|---------|----------|-------------|
| Parameter Estimation | `^rho1-param-estimation` | Minimize sum of squares |
| Log-Likelihood | `^rho1-log-likelihood` | I_ρ₁(α₀,α₁) |
| Intensity Function | `^rho1-intensity` | ρ₁(t) = e^(α₀ + α₁t) |
| Expected Failures | `^rho1-expected-failures` | E[N(t₁ → t₂)] |
| Reliability | `^rho1-reliability` | R(t₁ → t₂) |
| Expected Time to Next | `^rho1-expected-time-next` | E[T_{r+1} \| t=T_r] |
| MTBF | `^rho1-mtbf` | Mean time between failures |
| TBF | `^rho1-tbf` | μ_{r+1} = T_{r+1} - T_r |

---

### Repairable Systems - Model ρ₂

| Formula | Block ID | Description |
|---------|----------|-------------|
| Parameter Estimation | `^rho2-param-estimation` | Minimize sum of squares |
| Log-Likelihood | `^rho2-log-likelihood` | I_ρ₂(λ, δ) |
| Intensity Function | `^rho2-intensity` | ρ₂(t) = λδt^(δ-1) |
| Expected Failures | `^rho2-expected-failures` | E[N(t₁ → t₂)] |
| Reliability | `^rho2-reliability` | R(t₁ → t₂) |
| MTBF | `^rho2-mtbf` | Mean time between failures |
| Expected Time to Next | `^rho2-expected-time-next` | E[T_{r+1} \| t=T_r] |
| TBF | `^rho2-tbf` | μ_{r+1} = T_{r+1} - T_r |

---

### Availability

| Formula | Block ID | Description |
|---------|----------|-------------|
| Failure Rate | `^avail-failure-rate` | λ = 1/MTBF |
| Repair Rate | `^avail-repair-rate` | μ = 1/MTTR |
| Steady-State | `^avail-steady-state` | A = μ/(λ+μ) |
| Time-Dependent | `^avail-time-dependent` | A(t) with exponential term |
| Series | `^avail-series` | Series system availability |
| Active Parallel | `^avail-active-parallel` | Active parallel availability |
| k-out-of-w | `^avail-koon` | k-out-of-w availability |
| Standby (2 comp) | `^avail-standby-2comp` | Standby with 2 components |

---

## 🎯 Quick Reference by Topic

### When calculating reliability of...

- **Series system** → `^rel-series`
- **Parallel system (identical)** → `^rel-active-parallel-identical`
- **Parallel system (different R)** → `^rel-active-parallel-nonidentical`
- **Standby system** → `^rel-standby-general`
- **Standby with CFR** → `^rel-poisson-n` or `^rel-poisson-n2` or `^rel-poisson-koon`

### When analyzing Weibull components...

- **Find probability** → `^weibull-pdf` or `^weibull-cdf`
- **Find reliability** → `^weibull-reliability`
- **Find failure rate** → `^weibull-hazard`
- **Find next failure time** → `^weibull-expected-conditional` or `^weibull-expected-unconditional`

### When working with repairable systems...

- **Exponential trend (ρ₁)** → Use `^rho1-*` formulas
- **Weibull trend (ρ₂)** → Use `^rho2-*` formulas
- **Need MTBF** → `^rho1-mtbf` or `^rho2-mtbf`
- **Need reliability** → `^rho1-reliability` or `^rho2-reliability`

### When calculating availability...

- **Basic availability** → `^avail-steady-state`
- **Time-varying** → `^avail-time-dependent`
- **System configuration** → `^avail-series`, `^avail-active-parallel`, `^avail-koon`, or `^avail-standby-2comp`

---

## 💡 Pro Tips

1. **Autocomplete**: Start typing `[[Sample formula sheet#^` and Obsidian will suggest block IDs
2. **Preview on hover**: Hover over a link to see the formula without clicking
3. **Embed vs Link**: Use `![[...]]` to show the formula inline, `[[...]]` for a clickable link
4. **Custom names**: Use `[[Sample formula sheet#^block-id|Your Name]]` for readable links

---

## 📝 Example Usage in Worked Examples

```markdown
## Example: Calculate 2-out-of-3 System Reliability

**Given**: R₁ = R₂ = R₃ = 0.9

**Formula**: ![[Sample formula sheet#^rel-active-parallel-identical]]

**Solution**:
Using [[Sample formula sheet#^rel-active-parallel-identical|the binomial formula]]:

$R_s = \sum_{j=2}^{3} \binom{3}{j} (0.9)^j (0.1)^{3-j}$
$R_s = 3(0.9)^2(0.1) + (0.9)^3 = 0.972$

**Answer**: System reliability = 97.2%
```

---

## 🔄 Updates

This reference guide is automatically synchronized with the Sample formula sheet. All block IDs are current as of the latest version.

**Last Updated**: 2025-11-02
