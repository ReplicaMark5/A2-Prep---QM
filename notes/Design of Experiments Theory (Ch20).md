**Chapter 20 — Accurate & Reliable Data: Design of Experiments (DoE)**

> [!example] DOE — Brief mentions in previous chapters
>
> DOE mentioned briefly as a tool in:
> - [[Six Sigma DMAIC Methodology (Ch15)#Improve — Fix the system]] (DMAIC Improve phase)
> - [[DFSS & DMADV Framework (Ch17)#3  DMADV – The DFSS Implementation Method]] (DMADV Design phase)
>
> This chapter provides full theoretical coverage.

> [!summary] Exam focus
> Theory only. Know **purpose, use, importance**, core terms, design choices, and why DoE beats OFAT. High probability.

---

## 1) What DoE is and why it matters

> [!bug] EXAM CRITICAL — Theory Only
> Speaker 2: "If there's a DOE question, it's on theory. How do we use it, why it's important, what do we do with it?"
> **No calculations** — focus on purpose, use, and importance
^exam-critical-doe-theory
---

Core Purpose of DoE

1.  Screen — Find the vital few factors from many suspects.

2.  Characterize — Measure how much each factor matters and how they interact.

3.  Optimize — Find the best settings for maximum/minimum response.


DoE is a **structured way to plan, run, and analyse controlled tests** to learn which inputs drive performance, how they **interact**, and what settings work best, using **the fewest runs**. It enables cause-and-effect claims, avoids spurious correlations, and is economical.

OUTCOME FROM GROK GEMINI CHAT GPT

Purpose: Screening  →  Phase: Design fractional factorial (2⁴⁻¹) → Analyse → Identify key factors
Purpose: Characterisation  →  Phase: Run full factorial + centre points → Measure interactions
Purpose: Optimisation  →  Phase: Use RSM → Fit surface → Find optimum

---

> [!danger] LEARN THIS
> **OFAT vs DoE**: OFAT varies one factor while holding others "constant." It wastes runs, hides interactions, and yields narrow conclusions. DoE plans combinations to estimate **main effects + interactions** efficiently and validly.

---

## 2) Core vocabulary (workhorse terms)

> [!bug] EXAM FOCUS — Terminology
> Know these terms: **factor, level, treatment, interaction, response variable**
> From A2 Prep Guide emphasis on DoE terminology
^exam-focus-doe-terminology

> - **Factor**: a controllable input (e.g., temperature). 
> - **Level**: its setting. 
> - **Response**: the measured output.
> - **Interaction**: joint effect of factors on the response.

> - Inputs by control: **controlled (x)**, **uncontrolled observed (u)**, **uncontrolled unobserved (v)**. 
> - Tools: **replication**, **blocking**, **covariates**, **randomisation**.


> [!tip] Mental map
> Use **replication** to reduce noise, **blocking** to neutralise known nuisance variation, **randomisation** to average unknowns to ~0.

---

## 3) Design mechanics that make DoE work

- **Balance**: equal numbers at each high/low level. Simplifies estimates and keeps effects comparable.
    
- **Orthogonality**: columns of factor signs are independent; interaction columns balance to zero. Effects do not contaminate each other.
    
- **Randomisation**: guards against time/order biases.
    
- **Blocking**: group runs where a nuisance stays fixed; compare factors **within** blocks.
    

> [!learn] Interaction is not optional  
> Detecting **interactions** is central. Lines that change slope or cross across factor levels indicate interaction; OFAT will likely miss this.

---

## 4) Canonical designs and when to use them

**Single-factor**

- **Completely randomised**: one factor only; randomise all runs. Simple, but fragile if conditions drift.
    
- **Randomised block**: one primary factor, blocks absorb nuisance (e.g., machine). Stronger in real ops.
    

**Two+ factors**

- **Factorial**: test **every combination**; learn main effects + interactions. Gold standard for understanding.
    
- **Fractional factorial**: use a **subset** of combinations to **screen many factors** cheaply; assume higher-order interactions negligible.
    
- **Latin square**: one primary factor, two blocking variables; **assumes no interactions**. Efficient but risky if that assumption fails.
    

**Nonlinearity / optimisation**

- **2^k designs** with centre points detect curvature cheaply; escalate to **Response Surface Methods (RSM)** to map optima.
    

> [!question] Quick chooser  
> Many factors, little time → **Fractional**.  
> Few factors, want interactions → **Full factorial**.  
> Known nuisance sources → **Block**.  
> Curvature suspected → **Add centres / RSM**.

---

## 5) Typical sequence you can copy in practice

1. **Screening**: fractional factorial to find the vital few.
    
2. **Follow-up fractional**: confirm and uncover interactions.
    
3. **Full factorial**: characterise effects thoroughly, check curvature.
    
4. **RSM**: fit surfaces, locate optima.
    

> [!example] Detergent case, compressed  
> Compare detergents A/B/C on “whiteness.” Bad designs confound with machine; good designs **block by machine**, randomise order, then extend to factorial to add **temperature** and estimate interactions.

---

## 6) Why OFAT underperforms

- Can’t see interactions, so conclusions become **misleading** if interactions exist.
    
- Needs **more runs** for the same information.
    
- Applies only to the narrow conditions tested. DoE yields **broader, valid conclusions** with fewer runs.
    

---

## 7) Minimal rules you can remember under pressure

- **Define the objective** and the size of effect worth detecting.
    
- **Randomise** run order; **block** obvious nuisances; **replicate** enough to see signal.
    
- Keep designs **balanced and orthogonal** when possible.
    
- Start **simple**, escalate only when needed.
    

> [!warning] Common traps  
> Latin square assumes **no interactions**. OFAT + drifting conditions = false “effects.” Too few replicates = noise masquerades as signal.

---

## 8) One-page checklist before running a DoE

- Problem and response defined? “Good whiteness metric?” ✔︎
    
- Factors listed, ranges safe? ✔︎
    
- Design chosen for goal and constraints? ✔︎
    
- Plan for **randomisation / blocking / replication**? ✔︎
    
- Analysis path clear? (ANOVA for factors/interactions; plots for interaction) ✔︎
    
- Assumptions noted? (e.g., “no interactions” if Latin square) ✔︎
    

---

## 9) Interpreting outcomes fast

- **Main-effects plot**: steep slope = influential factor.
    
- **Interaction plot**: non-parallel or crossing lines = interaction; interpret main effects **with caution**.
    
- **Balanced/orthogonal designs** simplify ANOVA tables and cleanly separate effects.
    

> [!learn] Bottom line  
> DoE = **causal insight at low cost**: define, randomise, block, replicate, check interactions, then optimise. That flow wins exams and projects.

---

https://chatgpt.com/share/6903968f-dd20-8013-a4d9-118e1d1343e9