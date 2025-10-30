# Chapter 15 – Six Sigma (DMAIC)

> [!summary] Purpose  
> Six Sigma is not just a toolset. It’s a **thinking system for eliminating variation** and driving consistent performance.  
> It uses the **DMAIC** method (Define → Measure → Analyze → Improve → Control) to solve problems *scientifically* rather than by intuition.  

> [!danger] IMPORTANT  
> When the goal is to **design something new**, not improve what exists, use **DFSS / DMADV** instead.

---

## 1. The Big Idea — Why Six Sigma Exists

At its core, Six Sigma is built on one insight:  
**variation** is the enemy of quality.

Every time a product, service, or process behaves inconsistently, waste and defects appear.  
Six Sigma’s job is to make processes **predictable and stable** by understanding and controlling their sources of variation.

> [!learn] LEARN THIS  
> - “Sigma” (σ) = standard deviation → how much variation exists.  
> - “Six Sigma” means the process operates so close to perfection that only **3.4 defects per million** opportunities remain.  
> - The goal is not perfection — it’s **consistency**.

---

## 2. The Mindset — Quality as a Management System

Six Sigma is both a **philosophy** and a **project method**.

- **Philosophy:** Every process can be measured, analysed, and improved using facts.  
- **Method:** DMAIC provides a structured path from problem to solution.

This makes Six Sigma a *learning engine* for organisations — it combines statistics with management discipline.

> [!tip]  
> Six Sigma succeeds because it links quality improvement directly to **financial and customer outcomes**, not just compliance.

---

## 3. Voice of the Customer (VOC) → Critical to Quality (CTQ)

> [!bug] EXAM CRITICAL — Application Focus
> Speaker 2: "Theory + Application — understand foundations AND how you would apply it"
> Expect questions on translating customer needs to CTQs in scenarios
^exam-critical-application

Quality always starts with the **customer's definition of value**.
Six Sigma converts this "voice of the customer" (VOC) into **measurable performance requirements** called *CTQs* — *Critical to Quality characteristics.*

Example:
> VOC: "I want my online order to arrive fast."
> CTQ: Delivery within 48 hours, 99% of the time.

> [!learn]
> Six Sigma treats customer needs as data points, not opinions.
> CTQs become the measurable "targets" the process must meet.

---

## 4. The DMAIC Logic — Step by Step Understanding

> [!bug] EXAM CRITICAL — DMAIC Steps
> Know each phase's purpose and typical tools
> Contrast with DMADV (design vs improve)
^exam-critical-dmaic

Think of DMAIC as the *scientific method for business problems.*

---

### **Define — Clarify the real problem**

Teams identify what's wrong, who it affects, and what success would look like.

- Define scope, goals, and customer requirements.
- Tools: SIPOC diagram, VOC analysis, project charter.

**Question:** *What is the problem, and why is it worth solving?*

> [!important] LEARN THIS
> A well-defined problem is measurable, bounded, and customer-linked.

---

### **Measure — See reality with data**

The team gathers reliable data to describe the current process and its baseline performance.

- Map the process → identify inputs (Xs) and outputs (Ys).  
- Validate measurement systems.  
- Quantify the current sigma level.

**Question:** *How is the process performing right now?*

> [!tip]  
> Measurement turns assumptions into evidence — and often reveals that the “obvious cause” isn’t the true one.

---

### **Analyze — Find the root causes**

Here the data is explored to understand why variation exists.

- Use tools like histograms, box plots, correlation, regression, and ANOVA.  
- Look for patterns linking *inputs (Xs)* to *outputs (Ys)*.  
- Identify the *vital few* causes driving most of the problem.

**Question:** *Which process factors actually influence performance?*

> [!learn]  
> Root causes must be **proven with data**, not assumed from experience.

---

### **Improve — Fix the system**

Once causes are known, develop and test solutions that remove them.

- Run experiments (DOE) or pilot improvements.  
- Quantify how the fix improves the key metric (CTQ).  
- Plan for cultural or operational resistance.

**Question:** *What specific changes will produce measurable improvement?*

> [!tip]  
> Improvement = turning insight into action while managing human resistance to change.

---

### **Control — Hold the gains**

The last step ensures improvements become part of normal operations.

- Establish control charts and standard operating procedures (SOPs).  
- Update FMEAs and train staff.  
- Audit performance over time.

**Question:** *How do we keep the process from sliding back?*

> [!learn] LEARN THIS  
> Control means *sustained discipline*, not extra policing.  
> The goal is to make the right way the **easy way**.

---

## 5. DMAIC as a Flow of Thought

> [!graph]
> ```
> DEFINE → MEASURE → ANALYZE → IMPROVE → CONTROL  
>  ↓          ↓          ↓           ↓           ↓  
> What?    How bad?     Why?       How to fix?  How to keep?
> ```

Each step answers a different question.  
Together, they turn vague frustration (“This process is messy”) into specific, measurable improvement.

---

## 6. Roles and Structure — The Human Engine

> [!bug] EXAM CRITICAL — Six Sigma Roles
> Know role hierarchy and responsibilities
> Links to organizational roles in Chapter 8/Lecture 16
^exam-critical-roles

Six Sigma runs through **defined roles**, each with a purpose.

| **Role** | **Core Function** |
|-----------|------------------|
| **Leadership** | Set vision and allocate resources. |
| **Champions** | Sponsor projects and remove barriers. |
| **Master Black Belt** | Expert coaches who train and mentor Black Belts. |
| **Black Belt** | Lead complex projects full time. |
| **Green Belt** | Lead smaller projects part time. |
| **Team Members / SMEs** | Provide operational expertise and data. |
| **Process Owner** | Maintains the improved process long term. |

> [!learn]
> Hierarchy ensures accountability. Each level owns a part of the improvement chain.

---

## 7. The Seven Classic Quality Tools (used across DMAIC)

> [!example] Quality Tools — Also covered in Chapter 16
>
> These tools are introduced here in the context of DMAIC.
> Detailed application for Root Cause Analysis covered in [[Chapter 16]]
>
> 1. **Check Sheet** – Collects frequency data.
> 2. **Histogram** – Displays distribution of variation.
> 3. **Pareto Chart** – Identifies the vital few causes.
> 4. **Cause-and-Effect Diagram** – Organises possible causes.
> 5. **Flow Chart** – Maps the process steps.
> 6. **Scatter Diagram** – Tests variable relationships.
> 7. **Control Chart** – Monitors performance over time.
>
> **Mnemonic:** CHaPS FC²
> Check Sheet • Histogram • Pareto • Scatter • Flow • Cause-Effect • Control
>
> These tools don't fix problems — they *reveal patterns* so DMAIC decisions are based on facts.

---

## 8. DFSS / DMADV — When Six Sigma Designs, Not Fixes

> [!example] DFSS/DMADV Introduction — Expanded in Chapter 17
>
> Brief overview here; full details covered in [[Chapter 17]]
>
> **DFSS** (*Design for Six Sigma*) is the **philosophy** of building quality into new designs.
> **DMADV** (*Define–Measure–Analyze–Design–Verify*) is the **method** that executes DFSS.
>
> | DMAIC (Improve) | DMADV / DFSS (Design) |
> |------------------|------------------------|
> | Improves existing process | Designs a new one |
> | Ends with Control | Ends with Verify |
> | Data from current process | Data from customer needs |
> | Example: Reduce invoice errors | Example: Design new online platform |
>
> **Key difference:** DMAIC fixes defects *after* they appear.
> DMADV prevents them *before* they exist.
>
> **Note:** DFSS/DMADV is covered in detail in Chapter 17 – Continuous Innovation.

---

## 9. Six Sigma vs. Juran’s Breakthrough Sequence

Juran’s earlier “Breakthrough Sequence” shares the same logic but on a larger, organisational scale.

| **Six Sigma (DMAIC)** | **Breakthrough Sequence** |
|-------------------------|---------------------------|
| Tactical project level | Strategic system level |
| Define–Measure–Analyze–Improve–Control | Prove need → Identify project → Diagnose → Remedy → Control |
| Data/statistical focus | Change management focus |

> [!tip]  
> Six Sigma is the *toolkit*, Breakthrough is the *philosophy of change* behind it.

---

## 10. Success Factors — Why It Works (and When It Fails)

Six Sigma only works when:
1. Leadership actively supports it (not just funds it).  
2. Teams are trained and measured on results.  
3. Data systems are reliable.  
4. Improvements are piloted before rollout.  
5. Culture adapts — you don’t “shock the system.”

> [!learn] LEARN THIS  
> Six Sigma succeeds when it becomes **how people think**, not just a project label.

---

## 11. Deployment Journey (Juran Roadmap)

1. **Decide** – Confirm strategic fit and leadership commitment.  
2. **Prepare** – Train initial Champions and Belts.  
3. **Launch** – Run pilot projects.  
4. **Expand** – Scale across the organisation.  
5. **Sustain** – Embed Six Sigma in culture and metrics.

> [!tip]  
> The point of deployment is not the certificates — it’s the **habit of using data to think clearly.**

---

## 12. Summary — The Essence of DMAIC

> [!success] Key Takeaways  
> - Six Sigma = control of variation + customer focus + leadership accountability.  
> - DMAIC = scientific problem-solving logic.  
> - DFSS / DMADV = design quality into new systems.  
> - Roles and structure ensure consistency and accountability.  
> - Sustained success = disciplined culture, not occasional projects.

---

> [!note] Lower-Probability Exam Content  
> - Case examples (GE, Samsung, Telefónica).  
> - Detailed sigma-to-defect conversions.  
> - ROI ratios — skim only for context.

