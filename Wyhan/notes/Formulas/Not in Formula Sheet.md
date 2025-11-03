
> **Note:** These formulas appear in the course slides but are NOT included in the formula sheet. You need to memorize them for the exam.

---

## 1. Probability Density Function (PDF)

**What it measures:** Probability of failure occurring at any specific time

**Formula:**
$$f(t) = \frac{1}{N} \cdot \frac{\Delta n}{\Delta t}$$

**Where:**
- $\Delta n$ = number of failures in the time interval $[t, t + \Delta n]$
- $\Delta t$ = length of time interval
- $N$ = original population

> [!tip] Understanding
> PDF gives the probability of failure occurring during the **following** time unit (instantaneous failure rate).

---

## 2. Failure Distribution Function (CDF)

**What it measures:** Cumulative probability that failure has occurred on or before a specific time

**Formula:**
$$F(t) = \frac{\sum n_i}{N}$$

**Where:**
- $\sum n_i$ = number of failures up to time $t$
- $N$ = original population

> [!tip] Understanding
> This is the **cumulative** probability density - it sums up all failures that have happened by time $t$.

---

## 3. Reliability Function

**What it measures:** Probability of survival up to a specific time

**Formula:**
$$R(t) = 1 - F(t)$$

> [!tip] Understanding
> Reliability is the **complement** of the failure distribution function. If there's a 30% chance of failure by time $t$, there's a 70% chance of survival.

---

## 4. Hazard Function (Hazard Rate)

**What it measures:** Risk of failure at a specific time, given survival up to that time

**Formula:**
$$h(t) = \frac{1}{n(t)} \cdot \frac{\Delta n}{\Delta t} = \frac{f(t)}{R(t)}$$

**Where:**
- $\Delta n$ = number of failures in the time interval $[t, t + \Delta n]$
- $\Delta t$ = length of time interval
- $n(t)$ = population surviving at time $t$

> [!tip] Understanding
> This is the **conditional** probability of failure. It answers: "Given that the component has survived to time $t$, what's the probability it will fail in the next instant?"
>
> **Key relationship:** $h(t) = \frac{f(t)}{R(t)}$ - This connects hazard rate to PDF and reliability.

---

## Quick Memory Tips

1. **PDF** ($f$) = instantaneous failure rate at time $t$
2. **CDF** ($F$) = total failures accumulated by time $t$
3. **Reliability** ($R$) = opposite of CDF = survival probability
4. **Hazard** ($h$) = PDF divided by Reliability = conditional failure risk

**Relationship Chain:**
$$h(t) = \frac{f(t)}{R(t)} = \frac{f(t)}{1-F(t)}$$
