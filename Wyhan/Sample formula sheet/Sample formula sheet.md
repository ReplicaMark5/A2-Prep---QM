

---

## Reliability Modelling

```horizontal

**Series Systems**

$R=\prod_{i=1}^{w} R_{i}$

**Active Parallel Systems (k-out-of-w)**

$R=\sum_{j=k}^{w} \frac{w!}{j!(w-j)!} R_{i}^{j}\left(1-R_{i}\right)^{w-j}$

**Standby Parallel Systems**

$R=1-\prod_{i=1}^{w}\left(1-R_{i}\right)$

**<span style="color:rgb(196, 51, 2)">Complex Systems</span>**

$R=\left[\sum_{t}\left(\prod_{i} R_{i} \prod_{j} F_{i}\right)\right]+\prod_{y=1}^{w} R_{y}$

---

**Poisson Models**

$R=(1+\lambda t) e^{-\lambda t}$

$R=1-\sum_{i=0}^{n-1} \frac{(-\lambda t)^{i} e^{-\lambda t}}{i!}$

$R=e^{-k \lambda t} \sum_{i=0}^{n-k} \frac{(k \lambda t)^{i}}{i!}$

**Importance Measure**

$l_{i}=\frac{\partial R_{S}}{\partial R_{i}}$

```

---

## Laplace Trend Test

$U = \frac{\sum_{i=1}^{r-1} T_i - \frac{(r-1)T_r}{2}}{T_r \sqrt{\frac{1}{12(r-1)}}}$

---

## Non-repairable Components

```horizontal

**Weibull Distribution**

**Probability Density Function:**

$f_{X}(x) = \frac{\beta}{\eta}\left(\frac{x}{\eta}\right)^{\beta-1} \cdot \exp \left(-\left(\frac{x}{\eta}\right)^{\beta}\right)$

**Cumulative Distribution Function:**

$F_{X}(x) = 1-\exp \left(-\left(\frac{x}{\eta}\right)^{\beta}\right)$

**Reliability Function:**

$R_{X}(x) = \exp \left(-\left(\frac{x}{\eta}\right)^{\beta}\right)$

**Hazard Rate Function:**

$h_{X}(x) = \frac{\beta}{\eta}\left(\frac{x}{\eta}\right)^{\beta-1}$

---

**Expected Time to Next Failure**

**Conditional Expected Value (truncated):**

$E\left[X_{r+1} \mid X_{r+1} \leq X_{P}\right] = \frac{\int_{x}^{X_{P}} x \cdot f_{X}(x) \, dx}{\int_{x}^{X_{P}} f_{X}(x) \, dx}$

$\mu_{r+1} = E\left[X_{r+1} \mid X_{r+1} \leq X_{P}\right] - x$

**Unconditional Expected Value:**

$E\left[X_{r+1}\right] = \frac{\int_{0}^{\infty} x \cdot f_{X}(x) \, dx}{\int_{0}^{\infty} f_{X}(x) \, dx}$

$\mu_{r+1} = E\left[X_{r+1}\right] - x$

```

---

## Repairable Systems

### Model ρ₁ (Exponential Trend Model)

```horizontal

**Parameter Estimation:**

$\min(\bar{\alpha}_0,\bar{\alpha}_1) = \sum_{i=1}^{r} [E[N(0 \rightarrow T_i)] - N(0 \rightarrow T_i)]^2$

**Log-Likelihood Function:**

$I_{\rho_1}(\alpha_0,\alpha_1) = r\alpha_0 + \alpha_1 \sum_{i=1}^{r} T_i - \frac{e^{\alpha_0}(e^{\alpha_1 T_r} - 1)}{\alpha_1}$

**Intensity Function:**

$\rho_1(t) = e^{\alpha_0 + \alpha_1 t}$

**Expected Number of Failures:**

$E[N(t_1 \rightarrow t_2)] = \frac{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}{\alpha_1}$

---

**Reliability Function:**

$R(t_1 \rightarrow t_2) = \exp\!\left(-\frac{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}{\alpha_1}\right)$

**Expected Time to Next Failure:**

$E[T_{r+1} \mid t=T_r] = \frac{\ln[(r+1)\alpha_1 + e^{\alpha_0}] - \alpha_0}{\alpha_1}$

**Mean Time Between Failures:**

$\mathrm{MTBF}_{\rho_1}(t_1 \rightarrow t_2) = \frac{\alpha_1 (t_2 - t_1)}{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}$

**Time Between Failures:**

$\mu_{r+1} = T_{r+1} - T_r$

```

---

### Model ρ₂ (Weibull Trend Model)

```horizontal

**Parameter Estimation:**

$\min(\bar{\lambda}, \bar{\delta}) = \sum_{i=1}^{r} [E[N(0 \rightarrow T_i)] - N(0 \rightarrow T_i)]^2$

**Log-Likelihood Function:**

$I_{\rho_2}(\lambda, \delta) = r(\ln \lambda + \ln \delta) - \lambda T_r^{\delta} + (\delta - 1)\sum_{i=1}^{r} \ln T_i$

**Intensity Function:**

$\rho_2(t) = \lambda \delta t^{\delta - 1}$

**Expected Number of Failures:**

$E[N(t_1 \rightarrow t_2)] = \lambda (t_2^{\delta} - t_1^{\delta})$

---

**Reliability Function:**

$R(t_1 \rightarrow t_2) = e^{-\lambda (t_2^{\delta} - t_1^{\delta})}$

**Mean Time Between Failures:**

$\mathrm{MTBF}_{\rho_2}(t_1 \rightarrow t_2) = \frac{t_2 - t_1}{\lambda (t_2^{\delta} - t_1^{\delta})}$

**Expected Time to Next Failure:**

$E[T_{r+1} \mid t=T_r] = \left(\frac{1 + \lambda T_r^{\delta}}{\lambda}\right)^{1/\delta}$

**Time Between Failures:**

$\mu_{r+1} = T_{r+1} - T_r$

```

---

## Availability

*(MTBF = Mean Time Between Failures, MTTR = Mean Time To Repair)*

```horizontal

**Basic Availability Formulas**

**Failure Rate:**

$\lambda = \frac{1}{\mathrm{MTBF}}$

**Repair Rate:**

$\mu = \frac{1}{\mathrm{MTTR}}$

**Steady-State Availability:**

$A = \frac{\mathrm{MTBF}}{\mathrm{MTBF}+\mathrm{MTTR}} = \frac{\mu}{\lambda+\mu}$

**Time-Dependent Availability:**

$A(t) = \frac{\mu}{\lambda+\mu}+\frac{\lambda}{\lambda+\mu} e^{-(\lambda+\mu) t}$

**Series System Availability:**

$A_{\text{Series}} = \prod_{i=1}^{w} \frac{\mu_{i}}{\lambda_{i}+\mu_{i}}$

---

**Parallel Configuration**

**Active Parallel System Availability:**

$A_{\text{Active}} = 1-\prod_{i=1}^{w} \frac{\lambda_{i}}{\lambda_{i}+\mu_{i}}$

**Active k-out-of-w System Availability:**

$A_{\text{Active,k/w}} = 1-\frac{1}{(\lambda+\mu)^{w}} \sum_{i=0}^{k-1}\binom{w}{i} \mu^{i} \lambda^{w-i}$

**Standby Parallel (2 components) Availability:**

$A_{\text{Standby,2}} = \frac{\mu^{2}+\mu \lambda}{\mu^{2}+\mu \lambda+\lambda^{2}}$

```