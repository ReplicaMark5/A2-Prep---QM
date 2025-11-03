

---

## Reliability Modelling

**Series Systems** [[k-out-of-n Redundancy Explanation#n-out-of-n System (Series)|ℹ️]]

$R=\prod_{i=1}^{w} R_{i}$ ^rel-series

**Active Parallel Systems (k-out-of-w) - Identical** [[k-out-of-n Redundancy Explanation#For Identical Components|ℹ️]]

$R=\sum_{j=k}^{w} \frac{w!}{j!(w-j)!} R_{i}^{j}\left(1-R_{i}\right)^{w-j}$ ^rel-active-parallel-identical

**Standby Parallel Systems (General)** [[Standby Redundancy Explanation#General Formula|ℹ️]] [[k-out-of-n Redundancy Explanation#1-out-of-n System (Active Parallel)|Also see 1-out-of-n]]

$R=1-\prod_{i=1}^{w}\left(1-R_{i}\right)$ ^rel-standby-general

**Active Parallel Systems (k-out-of-w) - Non-Identical** [[k-out-of-n Redundancy Explanation#For Non-Identical Components|ℹ️]]

$R=\left[\sum_{t}\left(\prod_{i} R_{i} \prod_{j} F_{i}\right)\right]+\prod_{y=1}^{w} R_{y}$ ^rel-active-parallel-nonidentical

---

**Poisson Models** *(for Standby Systems with CFR)*

**n=2 Components** [[Standby Redundancy Explanation#For n=2 Components|ℹ️]]

$R=(1+\lambda t) e^{-\lambda t}$ ^rel-poisson-n2

**n Components** [[Standby Redundancy Explanation#For n Components|ℹ️]]

$R=1-\sum_{i=0}^{n-1} \frac{(-\lambda t)^{i} e^{-\lambda t}}{i!}$ ^rel-poisson-n

**k-out-of-n System** [[Standby Redundancy Explanation#For k-out-of-n System|ℹ️]]

$R=e^{-k \lambda t} \sum_{i=0}^{n-k} \frac{(k \lambda t)^{i}}{i!}$ ^rel-poisson-koon

**Importance Measure**

$l_{i}=\frac{\partial R_{S}}{\partial R_{i}}$ ^rel-importance

---

## Laplace Trend Test

$U = \frac{\sum_{i=1}^{r-1} T_i - \frac{(r-1)T_r}{2}}{T_r \sqrt{\frac{1}{12(r-1)}}}$ ^laplace-u-statistic

---

## Non-repairable Components

### Weibull Distribution

**Probability Density Function:**

$f_{X}(x) = \frac{\beta}{\eta}\left(\frac{x}{\eta}\right)^{\beta-1} \cdot \exp \left(-\left(\frac{x}{\eta}\right)^{\beta}\right)$ ^weibull-pdf

**Cumulative Distribution Function:**

$F_{X}(x) = 1-\exp \left(-\left(\frac{x}{\eta}\right)^{\beta}\right)$ ^weibull-cdf

**Reliability Function:**

$R_{X}(x) = \exp \left(-\left(\frac{x}{\eta}\right)^{\beta}\right)$ ^weibull-reliability

**Hazard Rate Function:**

$h_{X}(x) = \frac{\beta}{\eta}\left(\frac{x}{\eta}\right)^{\beta-1}$ ^weibull-hazard

### Expected Time to Next Failure

**Conditional Expected Value (truncated):**

$E\left[X_{r+1} \mid X_{r+1} \leq X_{P}\right] = \frac{\int_{x}^{X_{P}} x \cdot f_{X}(x) \, dx}{\int_{x}^{X_{P}} f_{X}(x) \, dx}$ ^weibull-expected-conditional

$\mu_{r+1} = E\left[X_{r+1} \mid X_{r+1} \leq X_{P}\right] - x$ ^weibull-mu-conditional

**Unconditional Expected Value:**

$E\left[X_{r+1}\right] = \frac{\int_{0}^{\infty} x \cdot f_{X}(x) \, dx}{\int_{0}^{\infty} f_{X}(x) \, dx}$ ^weibull-expected-unconditional

> [!note]- Simplification
> Since $\int_{0}^{\infty} f_{X}(x) \, dx = 1$ (total probability), this simplifies to:
>
> $E[X] = \int_{0}^{\infty} x \cdot f_{X}(x) \, dx$

$\mu_{r+1} = E\left[X_{r+1}\right] - x$ ^weibull-mu-unconditional

---

## Repairable Systems (NHPP Models)

### Model ρ₁ (Exponential Trend / Log-Linear Intensity)

**Parameter Estimation:**

$\min(\bar{\alpha}_0,\bar{\alpha}_1) = \sum_{i=1}^{r} [E[N(0 \rightarrow T_i)] - N(0 \rightarrow T_i)]^2$ ^rho1-param-estimation

**Log-Likelihood Function:**

$I_{\rho_1}(\alpha_0,\alpha_1) = r\alpha_0 + \alpha_1 \sum_{i=1}^{r} T_i - \frac{e^{\alpha_0}(e^{\alpha_1 T_r} - 1)}{\alpha_1}$ ^rho1-log-likelihood

**Intensity Function:**

$\rho_1(t) = e^{\alpha_0 + \alpha_1 t}$ ^rho1-intensity

**Expected Number of Failures:**

$E[N(t_1 \rightarrow t_2)] = \frac{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}{\alpha_1}$ ^rho1-expected-failures

**Reliability Function:**

$R(t_1 \rightarrow t_2) = \exp\!\left(-\frac{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}{\alpha_1}\right)$ ^rho1-reliability

**Expected Time to Next Failure:**

$E[T_{r+1} \mid t=T_r] = \frac{\ln[(r+1)\alpha_1 + e^{\alpha_0}] - \alpha_0}{\alpha_1}$ ^rho1-expected-time-next

**Mean Time Between Failures:**

$\mathrm{MTBF}_{\rho_1}(t_1 \rightarrow t_2) = \frac{\alpha_1 (t_2 - t_1)}{e^{\alpha_0 + \alpha_1 t_2} - e^{\alpha_0 + \alpha_1 t_1}}$ ^rho1-mtbf

**Time Between Failures:**

$\mu_{r+1} = T_{r+1} - T_r$ ^rho1-tbf

---

### Model ρ₂ (Weibull Intensity / Power Law)

**Parameter Estimation:**

$\min(\bar{\lambda}, \bar{\delta}) = \sum_{i=1}^{r} [E[N(0 \rightarrow T_i)] - N(0 \rightarrow T_i)]^2$ ^rho2-param-estimation

**Log-Likelihood Function:**

$I_{\rho_2}(\lambda, \delta) = r(\ln \lambda + \ln \delta) - \lambda T_r^{\delta} + (\delta - 1)\sum_{i=1}^{r} \ln T_i$ ^rho2-log-likelihood

**Intensity Function:**

$\rho_2(t) = \lambda \delta t^{\delta - 1}$ ^rho2-intensity

**Expected Number of Failures:**

$E[N(t_1 \rightarrow t_2)] = \lambda (t_2^{\delta} - t_1^{\delta})$ ^rho2-expected-failures

**Reliability Function:**

$R(t_1 \rightarrow t_2) = e^{-\lambda (t_2^{\delta} - t_1^{\delta})}$ ^rho2-reliability

**Mean Time Between Failures:**

$\mathrm{MTBF}_{\rho_2}(t_1 \rightarrow t_2) = \frac{t_2 - t_1}{\lambda (t_2^{\delta} - t_1^{\delta})}$ ^rho2-mtbf

**Expected Time to Next Failure:**

$E[T_{r+1} \mid t=T_r] = \left(\frac{1 + \lambda T_r^{\delta}}{\lambda}\right)^{1/\delta}$ ^rho2-expected-time-next

**Time Between Failures:**

$\mu_{r+1} = T_{r+1} - T_r$ ^rho2-tbf

---

## Availability

*(MTBF = Mean Time Between Failures, MTTR = Mean Time To Repair)*

### Basic Formulas

**Failure Rate:**

$\lambda = \frac{1}{\mathrm{MTBF}}$ ^avail-failure-rate

**Repair Rate:**

$\mu = \frac{1}{\mathrm{MTTR}}$ ^avail-repair-rate

**Steady-State Availability:**

$A = \frac{\mathrm{MTBF}}{\mathrm{MTBF}+\mathrm{MTTR}} = \frac{\mu}{\lambda+\mu}$ ^avail-steady-state

**Time-Dependent Availability:**

$A(t) = \frac{\mu}{\lambda+\mu}+\frac{\lambda}{\lambda+\mu} e^{-(\lambda+\mu) t}$ ^avail-time-dependent

**Series System Availability:**

$A_{\text{Series}} = \prod_{i=1}^{w} \frac{\mu_{i}}{\lambda_{i}+\mu_{i}}$ ^avail-series

### Parallel Configuration

**Active Parallel System Availability:**

$A_{\text{Active}} = 1-\prod_{i=1}^{w} \frac{\lambda_{i}}{\lambda_{i}+\mu_{i}}$ ^avail-active-parallel

**Active k-out-of-w System Availability:**

$A_{\text{Active,k/w}} = 1-\frac{1}{(\lambda+\mu)^{w}} \sum_{i=0}^{k-1}\binom{w}{i} \mu^{i} \lambda^{w-i}$ ^avail-koon

**Standby Parallel (2 components) Availability:**

$A_{\text{Standby,2}} = \frac{\mu^{2}+\mu \lambda}{\mu^{2}+\mu \lambda+\lambda^{2}}$ ^avail-standby-2comp