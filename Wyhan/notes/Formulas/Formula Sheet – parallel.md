
---

## Reliability Modelling

```horizontal

**Series Systems**
<span style="font-size:0.6em; position:relative; top:-8px;">All components must work; used in RBD analysis.</span>
$R=\prod_{i=1}^{w} R_{i}$

**Active Parallel Systems (k-out-of-w) - Identical**
<span style="font-size:0.6em; position:relative; top:-8px;">At least k of w identical components must work (binomial expansion).</span>
$R=\sum_{j=k}^{w} \frac{w!}{j!(w-j)!} R_{i}^{j}\left(1-R_{i}\right)^{w-j}$

**Active Parallel Systems - Non-Identical**
<span style="font-size:0.6em; position:relative; top:-8px;">System succeeds if any component succeeds.</span>
$R=1-\prod_{i=1}^{w}\left(1-R_{i}\right)$

**Active Parallel Systems (k-out-of-w) - Non-Identical**
<span style="font-size:0.6em; position:relative; top:-8px;">$R{i}​$: probability ${i}$ works; $F{i}=1−R{i}$​: probability $i$ fails</span>
$R=\left[\sum_{t}\left(\prod_{i} R_{i} \prod_{j} F_{i}\right)\right]+\prod_{y=1}^{w} R_{y}$

---

**Poisson Models** *(for Standby Systems with CFR)*

**n=2 Identical Components**
<span style="font-size:0.6em; position:relative; top:-8px;">Two standby components with constant failure rate (Eq 2.18).</span>
$R=(1+\lambda t) e^{-\lambda t}$

**n Identical Components**
<span style="font-size:0.6em; position:relative; top:-8px;">Closed-form Poisson representation for n standby components (Eq 2.19).</span>
$R=e^{-\lambda t}\sum_{i=0}^{n-1} \frac{(\lambda t)^{i}}{i!}$

**k-out-of-n System w/ n=k identical components**
<span style="font-size:0.6em; position:relative; top:-8px;">Generalized k-out-of-n standby system (Eq 2.20).</span>
$R=e^{-k \lambda t} \sum_{i=0}^{n-k} \frac{(k \lambda t)^{i}}{i!}$

**Importance Measure**
<span style="font-size:0.6em; position:relative; top:-8px;">Birnbaum's component importance; computed by partial differentiation of $R_S$.</span>
$l_{i}=\frac{\partial R_{S}}{\partial R_{i}}$

```

> [!question]- Active Parallel Systems – Note
> $\sum_t(\dots)$: sum over all combinations that lead to a working system  
$\prod_y R_y$: case where all components work (always successful)
> **Example (3 components in parallel):**
> 
> $R = (R_1F_2F_3) + (F_1R_2F_3) + (F_1F_2R_3) + (R_1R_2F_3) + (R_1F_2R_3) + (F_1R_2R_3)+ (R_1R_2R_3)$

> [!danger]- Poisson Reliability – Correct vs Incorrect Forms  
> The **formula sheet version** contains a sign and structure error.  
> It shows:
> 
> **❌ Incorrect (formula sheet misprint):**  
> $R = 1 - \displaystyle\sum_{i=0}^{n-1} \frac{(-\lambda t)^i e^{-\lambda t}}{i!}$  
> This form is wrong because:
> 
> - The $(-\lambda t)^i$ term introduces alternating signs.
>     
> - Subtracting from 1 changes the meaning (it no longer represents a probability).
>     
> - It does **not** correspond to the Poisson reliability function.
>     
> 
> ---
> 
> **✅ Correct (lecture slides and course notes):**  
> $R(t) = e^{-\lambda t} \displaystyle\sum_{i=0}^{n-1} \frac{(\lambda t)^i}{i!}$  
> This is the valid **Poisson reliability function** for _n_ identical standby components (constant failure rate $\lambda$).
> 
> - Represents the probability that **fewer than $n$ failures** have occurred by time $t$.
>     
> - Derived directly from the Poisson distribution’s cumulative form: $P[N(t) \le n-1]$.
>     
> - Always satisfies $R(0)=1$ and $R(\infty)=0$.
>     
> 
> ---
> 
> 💡 **Remember:** use the **positive-sum form** $e^{-\lambda t}\sum(\lambda t)^i/i!$ — never the version with negative powers or a subtraction from 1.

---

## Laplace Trend Test

$U = \frac{\sum_{i=1}^{r-1} T_i - \frac{(r-1)T_r}{2}}{T_r \sqrt{\frac{1}{12(r-1)}}}$

> [!tip]- Laplace Trend Test — Model Selection Guide
> Expand to view decision flow.
> > ![[Laplace Trend Test – Model Selection#^laplace-flow]]

---

# Repairable Systems (NHPP)


> [!tip]-
> *Becomes **HPP** when $\alpha_1 = 0$ (log-linear) or $\delta = 1$ (power-law).*
> ✅ *Analytically solvable for the next expected event time:*  
> Log-linear → $E[T_{r+1} \mid T_r] = \dfrac{\ln[(r+1)\alpha_1 + e^{\alpha_0}] - \alpha_0}{\alpha_1}$  
> Power-law → $[T_{r+1} \mid T_r] = \left( \dfrac{1 + \lambda T_r^{\delta}}{\lambda} \right)^{1/\delta}$  
> ❌ *Not applicable for residual-life calculations* — NHPP models the **count of failures** in a repairable process, not the lifetime of a single component.
> 
> Mean Time Between Failures – MTBF --> Used for **repairable systems** (HPP / NHPP)
> 

> [!note]- **Event Times → Repairable Systems**
> 
> Whenever you see:
> - $T_1, T_2, T_3, \ldots, T_r$
> - $E[T_{r+1} \mid T_r]$
> - $N(t_1 \rightarrow t_2)$  
> - Phrases like “expected number of failures,” “next expected failure,” or “time between failures”
>
> ➤ You are working with **Repairable Systems**, modeled using **Poisson processes**:
> - **HPP (Homogeneous Poisson Process)** → constant failure rate  
> - **NHPP (Non-Homogeneous Poisson Process)** → time-varying failure rate (log-linear or power-law)
>
> These models describe **failure events over time** for a system that is **repaired and put back into service** after each failure.

### Model ρ₁ (Log Linear)

```horizontal

**Parameter Estimation:**

$\min(\bar{\alpha}_0,\bar{\alpha}_1) = \sum_{i=1}^{r} [E[N(0 \rightarrow T_i)] - N(0 \rightarrow T_i)]^2$

**Log-Likelihood Function:**

$I_{\rho_1}(\alpha_0,\alpha_1) = r\alpha_0 + \alpha_1 \sum_{i=1}^{r} T_i - \frac{e^{\alpha_0}(e^{\alpha_1 T_r} - 1)}{\alpha_1}$

**Intensity Function:**
<span style="font-size:0.6em; position:relative; top:-8px;">Instantaneous failure rate (ROCOF).</span>
$\rho_1(t) = e^{\alpha_0 + \alpha_1 t}$

**Expected Number of Failures:**
<span style="font-size:0.6em; position:relative; top:-8px;">Predict number of failures between two times.</span>
$E[N(t_1 \rightarrow t_2)] = \frac{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}{\alpha_1}$

---

**Reliability Function:**
<span style="font-size:0.6em; position:relative; top:-8px;">Probability of no failures between $t_1$ and $t_2$.</span>
$R(t_1 \rightarrow t_2) = \exp\!\left(-\frac{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}{\alpha_1}\right)$

**Expected Time to Next Failure:**
<span style="font-size:0.6em; position:relative; top:-8px;">Time of next event given last observed event.</span>
$E[T_{r+1} \mid t=T_r] = \frac{\ln[(r+1)\alpha_1 + e^{\alpha_0}] - \alpha_0}{\alpha_1}$

**Mean Time Between Failures:**
<span style="font-size:0.6em; position:relative; top:-8px;">Expected time between events.</span>
$\mathrm{MTBF}_{\rho_1}(t_1 \rightarrow t_2) = \frac{\alpha_1 (t_2 - t_1)}{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}$

**Time Between Failures:**
<span style="font-size:0.6em; position:relative; top:-8px;">Duration between successive failures.</span>
$\mu_{r+1} = T_{r+1} - T_r$

```

---

### Model ρ₂ (Power Law)

```horizontal

**Parameter Estimation:**

$\min(\bar{\lambda}, \bar{\delta}) = \sum_{i=1}^{r} [E[N(0 \rightarrow T_i)] - N(0 \rightarrow T_i)]^2$

**Log-Likelihood Function:**

$I_{\rho_2}(\lambda, \delta) = r(\ln \lambda + \ln \delta) - \lambda T_r^{\delta} + (\delta - 1)\sum_{i=1}^{r} \ln T_i$

**Intensity Function:**
<span style="font-size:0.6em; position:relative; top:-8px;">Instantaneous failure rate (ROCOF).</span>
$\rho_2(t) = \lambda \delta t^{\delta - 1}$

**Expected Number of Failures:**
<span style="font-size:0.6em; position:relative; top:-8px;">Predict number of failures between two times.</span>
$E[N(t_1 \rightarrow t_2)] = \lambda (t_2^{\delta} - t_1^{\delta})$

---

**Reliability Function:**
<span style="font-size:0.6em; position:relative; top:-8px;">Probability of no failures between $t_1$ and $t_2$.</span>
$R(t_1 \rightarrow t_2) = e^{-\lambda (t_2^{\delta} - t_1^{\delta})}$

**Mean Time Between Failures:**
<span style="font-size:0.6em; position:relative; top:-8px;">Expected time between events.</span>
$\mathrm{MTBF}_{\rho_2}(t_1 \rightarrow t_2) = \frac{t_2 - t_1}{\lambda (t_2^{\delta} - t_1^{\delta})}$

**Expected Time to Next Failure:**
<span style="font-size:0.6em; position:relative; top:-8px;">Time of next event given last observed event.</span>
$E[T_{r+1} \mid t=T_r] = \left(\frac{1 + \lambda T_r^{\delta}}{\lambda}\right)^{1/\delta}$

**Time Between Failures:**
<span style="font-size:0.6em; position:relative; top:-8px;">Duration between successive failures.</span>
$\mu_{r+1} = T_{r+1} - T_r$

```

---

## Availability

*(MTBF = Mean Time Between Failures, MTTR = Mean Time To Repair)*

```horizontal

### Basic Availability Formulas

**Failure Rate:**
<span style="font-size:0.6em; position:relative; top:-8px;">Converts mean time between failures to a failure rate (ROCOF).</span>
$\lambda = \frac{1}{\mathrm{MTBF}}$

**Repair Rate:**
<span style="font-size:0.6em; position:relative; top:-8px;">Converts mean time to repair to a repair rate.</span>
$\mu = \frac{1}{\mathrm{MTTR}}$

**Steady-State Availability:**
<span style="font-size:0.6em; position:relative; top:-8px;">Proportion of time the item is functional (long-run average).</span>
$A = \frac{\mathrm{MTBF}}{\mathrm{MTBF}+\mathrm{MTTR}} = \frac{\mu}{\lambda+\mu}$

**Time-Dependent Availability:**
<span style="font-size:0.6em; position:relative; top:-8px;">Probability system is operational at time t; converges to steady-state as t → ∞.</span>
$A(t) = \frac{\mu}{\lambda+\mu}+\frac{\lambda}{\lambda+\mu} e^{-(\lambda+\mu) t}$

**Series System Availability:**
<span style="font-size:0.6em; position:relative; top:-8px;">All components must be operational.</span>
$A_{\text{Series}} = \prod_{i=1}^{w} \frac{\mu_{i}}{\lambda_{i}+\mu_{i}}$

---

### Parallel Configuration

**Active Parallel System Availability:**
<span style="font-size:0.6em; position:relative; top:-8px;">System works if any one component works.</span>
$A_{\text{Active}} = 1-\prod_{i=1}^{w} \frac{\lambda_{i}}{\lambda_{i}+\mu_{i}}$

**Active k-out-of-w System Availability:**
<span style="font-size:0.6em; position:relative; top:-8px;">System succeeds if ≥ k of w components function.</span>
$A_{\text{Active,k/w}} = 1-\frac{1}{(\lambda+\mu)^{w}} \sum_{i=0}^{k-1}\binom{w}{i} \mu^{i} \lambda^{w-i}$

**Standby Parallel (2 components) Availability:**
<span style="font-size:0.6em; position:relative; top:-8px;">One unit on standby while the other operates.</span>
$A_{\text{Standby,2}} = \frac{\mu^{2}+\mu \lambda}{\mu^{2}+\mu \lambda+\lambda^{2}}$

```
