## Problem Statement

You are required to conduct a reliability analysis for an F1 race car. The components included in the analysis are: **FS, FRB, FLB, BS, BRB, BLB, GB, EN**.

**Design Specification:**
- The car can continue with **≥1 front brake** and **≥1 rear brake** working
- Front brakes (FRB, FLB) connect to **FS** (front suspension)
- Rear brakes (BRB, BLB) connect to **BS** (back suspension)
- The car stops if **any** suspension, **GB** (gearbox), or **EN** (engine) fails

**Given Component Models** (distance $t$ in km) and parameters:

- $f_{\text{FS}}(\alpha_0,\alpha_1) = f_{\text{FS}}(-10.0096, 0.001399)$ — NHPP ρ₁
- $f_{\text{BS}}(\lambda,\delta) = f_{\text{BS}}(2.28 \times 10^{-7}, 2.05686)$ — NHPP ρ₂
- $f_{\text{FRB}} = f_{\text{FLB}} = \text{Weibull}(\beta=2.22, \eta=1152)$
- $f_{\text{BRB}} = f_{\text{BLB}} = \text{Weibull}(\beta=3.4, \eta=630)$
- $f_{\text{GB}} = \text{Weibull}(\beta=2.14, \eta=2795)$
- $f_{\text{EN}} = \text{Weibull}(\beta=3.82, \eta=1458)$

---

## Tasks

1. Match component reliabilities at **305 km**
2. Compute the **car system** reliability at **305 km**
3. Compute the expected distance to **first breakdown** assuming an upper bound of **6000 km**

---

## Solution

### Step 1: Component Reliabilities at 305 km

We need three different reliability formulas from our formula sheet:

#### Weibull Reliability

![[Formula Sheet#^weibull-reliability]]

#### NHPP ρ₁ (Log-Linear Intensity) Reliability

![[Formula Sheet#^rho1-reliability]]

For reliability from start $(t_1 = 0)$ to distance $t$:

$R(0 \rightarrow t) = \exp\left(-\frac{e^{\alpha_0 + \alpha_1 t} - e^{\alpha_0}}{\alpha_1}\right)$

#### NHPP ρ₂ (Weibull Intensity) Reliability

![[Formula Sheet#^rho2-reliability]]

For reliability from start:

$R(0 \rightarrow t) = e^{-\lambda t^{\delta}}$

---

### Calculating Each Component at t = 305 km

**FS** (NHPP ρ₁: $\alpha_0 = -10.0096$, $\alpha_1 = 0.001399$):

$R_{\text{FS}}(305) = \exp\left(-\frac{e^{-10.0096 + 0.001399(305)} - e^{-10.0096}}{0.001399}\right) = \boxed{0.98304}$

**BS** (NHPP ρ₂: $\lambda = 2.28 \times 10^{-7}$, $\delta = 2.05686$):

$R_{\text{BS}}(305) = e^{-2.28 \times 10^{-7} \times 305^{2.05686}} = \boxed{0.97106}$

**FRB = FLB** (Weibull: $\beta = 2.22$, $\eta = 1152$):

$R_{\text{FRB}}(305) = R_{\text{FLB}}(305) = \exp\left(-\left(\frac{305}{1152}\right)^{2.22}\right) = \boxed{0.94902}$

**BRB = BLB** (Weibull: $\beta = 3.4$, $\eta = 630$):

$R_{\text{BRB}}(305) = R_{\text{BLB}}(305) = \exp\left(-\left(\frac{305}{630}\right)^{3.4}\right) = \boxed{0.91861}$

**GB** (Weibull: $\beta = 2.14$, $\eta = 2795$):

$R_{\text{GB}}(305) = \exp\left(-\left(\frac{305}{2795}\right)^{2.14}\right) = \boxed{0.99131}$

**EN** (Weibull: $\beta = 3.82$, $\eta = 1458$):

$R_{\text{EN}}(305) = \exp\left(-\left(\frac{305}{1458}\right)^{3.82}\right) = \boxed{0.99747}$

---

### Step 2: Brake Subsystems and Car Reliability at 305 km

#### Brake Subsystems (1-out-of-2 Parallel)

![[Formula Sheet#^rel-standby-general]]

For 2 components (1-out-of-2): $R_{1\text{-of-}2} = 1 - (1-R_1)(1-R_2)$

**Front Brakes:**

$R_{\text{FB}} = 1 - (1 - 0.94902)(1 - 0.94902) = 1 - (0.05098)^2 = \boxed{0.99740}$

**Rear Brakes:**

$R_{\text{RB}} = 1 - (1 - 0.91861)(1 - 0.91861) = 1 - (0.08139)^2 = \boxed{0.99338}$

#### Car System (Series Configuration)

![[Formula Sheet#^rel-series]]

The car structure is **all components in series**:

$R_{\text{car}} = R_{\text{FS}} \times R_{\text{BS}} \times R_{\text{GB}} \times R_{\text{EN}} \times R_{\text{FB}} \times R_{\text{RB}}$

**Calculation:**

$R_{\text{car}}(305) = (0.98304)(0.97106)(0.99131)(0.99747)(0.99740)(0.99338)$

$R_{\text{car}}(305) = \boxed{0.93521}$

---

### Step 3: Expected Distance to First Breakdown (MTTF)

**Formula for Mean Time to Failure:**

![[Formula Sheet#^weibull-expected-unconditional]]

Using the concept above for the system:

$E[T] = \int_{0}^{T_{\text{max}}} R_{\text{car}}(t) \, dt$

With upper bound $T_{\text{max}} = 6000$ km:

$E[T] \approx \int_{0}^{6000} R_{\text{car}}(t) \, dt$

This requires numerical integration of the full system reliability function over distance.

**Result (numerical integration):**

$E[T] \approx \boxed{593 \text{ km}}$ (nearest km)

---

## Important Notes

### System Structure

The car reliability structure is:

```
       ┌─ FRB ─┐
FS ──┬─┤       ├─┐
     │ └─ FLB ─┘ │
     │           │
     │  ┌─ BRB ─┐│
BS ──┼──┤       ├┼── GB ── EN ── Output
     │  └─ BLB ─┘│
     └───────────┘
```

All components are in **series** except:
- Front brakes: **1-out-of-2** (parallel)
- Rear brakes: **1-out-of-2** (parallel)

### Why Not Use Single Component MTTF?

- Using a single rear-brake mean (≈566 km) is **NOT valid** for the car
- The rear brakes are configured as **1-out-of-2**, so the system only fails when **both** rear brakes have failed
- The car also depends on FS, BS, GB, and EN in series
- The integral gives the correct system MTTF accounting for all failure modes

---

## Quick Verification Checks

✅ **Parallel subsystems increase reliability:**
- $R_{\text{FB}} = 0.99740 > R_{\text{FRB}} = 0.94902$ ✓
- $R_{\text{RB}} = 0.99338 > R_{\text{BRB}} = 0.91861$ ✓

✅ **Series system reduces reliability:**
- $R_{\text{car}} = 0.93521 <$ any individual component ✓

✅ **MTTF is reasonable:**
- Expected failure at 593 km lies between single rear-brake (~566 km) and both-rear-brakes-failed (~670 km)
- Accounts for all series components (FS, BS, GB, EN) interacting with brake subsystems ✓

---

## Exam Strategy Tips

1. **Always state the system structure first**
   - Draw a simple block diagram
   - Identify series vs. parallel configurations

2. **Write $R_{\text{car}}(t)$ explicitly**
   - Show the formula before substituting numbers
   - This helps catch structural errors

3. **For k-out-of-n parallel systems:**
   - Use $R = 1 - \prod_{i=1}^{w}(1-R_i)$ when $k=1$
   - This is the [[Formula Sheet#^rel-standby-general|1-out-of-n formula]]

4. **Round consistently**
   - Use 5 decimal places for intermediate calculations
   - Round final answer to required precision

5. **For "distance to first breakdown":**
   - Integrate $R_{\text{car}}(t)$ to the specified horizon
   - Use numerical integration (calculator or software)

6. **Avoid shortcuts**
   - Don't use "weakest-link" approximations when parallel elements exist
   - Always use the full system reliability function

---

## Related Formulas

- [[Formula Sheet#^weibull-reliability|Weibull Reliability]]
- [[Formula Sheet#^rho1-reliability|NHPP ρ₁ Reliability]]
- [[Formula Sheet#^rho2-reliability|NHPP ρ₂ Reliability]]
- [[Formula Sheet#^rel-series|Series Systems]]
- [[Formula Sheet#^rel-standby-general|Parallel Systems (1-out-of-n)]]
