**Lecture 15** — Quality Planning, DFSS, and Quality Control

> [!map] Mental model
> **Design sets the ceiling. Control keeps you at the ceiling. Improvement raises the ceiling.**  
> If outcomes are poor, assume a **design** gap first, not worker failure.

---

## 1) Juran's Trilogy in practice

> [!example] Juran's Trilogy — Revision
>
> Revision from [[Lecture 9#🔺 Juran's Trilogy (The Core Framework)]]
> Also covered in: [[Lecture 10]], [[Chapter 4]], [[Chapter 17]]
>
> **Plan → Control → Improve** is the system loop. Design quality into the work, then regulate it in operation, then elevate capability.
>
> - **Plan:** identify customers and needs, translate to requirements, design the product and the process that will deliver it.
> - **Control:** keep actual performance on target with feedback, standards, and action rules.
> - **Improve:** remove chronic waste and variation to reach a higher level of performance.

> [!example] Why design matters
> The **Mars Climate Orbiter** failure = integration and requirements breakdown, not a last-minute inspection miss. “All systems do what they’re designed to do.”

---

## 2) Quality Planning & Design (QbD)

> [!example] Quality Planning — Detailed in Chapter 4
>
> Overview here; full Juran Quality by Design Model covered in [[Chapter 4]]
>
> Prevent defects by **designing them out** early. Verification late in the game is expensive and unreliable.

<p align="center">
  <strong>Quality Planning Spine</strong><br>
  <em>Visual summary of how planning transforms customer needs into verified design.</em>
</p>


```mermaid

%%{init: {"flowchart": { "rankSpacing": 20, "nodeSpacing": 8 }}}%%
flowchart TD
A["Step 1  Customers and Needs"] --> A_note["Identify hidden and explicit needs"]
A_note --> B["Step 2  Translate to Requirements"]
B --> B_note["Convert needs into measurable CTQs and specs"]
B_note --> C["Step 3  Design Product and Process"]
C --> C_note["Match process capability with product requirements"]
C_note --> D["Step 4  Verify Fit"]
D --> D_note["Confirm fit with customer and organization"]
D_note --> E["Result  Quality by Design Achieved"]

classDef step fill:#fde4e4,stroke:#f28b82,stroke-width:0.6px,color:#4a1f1f,font-weight:bold,font-size:11px;
classDef note fill:#fffaf9,stroke:none,color:#7a3e3e,font-size:10px,font-style:italic;
class A,B,C,D,E step;
class A_note,B_note,C_note,D_note note;
```


> [!tip] What to memorize vs understand
> Memorize the **sequence**. Understand the **why:** you are minimizing downstream control and failure costs by increasing upstream clarity and fit.

---

## 3) DFSS / DMADV — designing right the first time

> [!example] DFSS/DMADV — Detailed in Chapter 17
>
> Brief overview here; full DFSS methodology and DMADV phases covered in [[Chapter 17]]
> Also introduced in [[Lecture 12#8. DFSS / DMADV — When Six Sigma Designs, Not Fixes]]
>
> **DMADV:** _Define → Measure → Analyze → Design → Verify_. Use when **creating** or **re-creating** a product/process. Not for minor tweaks.
>
> - **Define:** the opportunity, scope, customer segments, and business case.
> - **Measure:** customer needs and constraints; establish CTQs and baseline feasibility.
> - **Analyze:** translate needs to design parameters; explore alternatives; predict capability.
> - **Design:** select and parameterize the concept; ensure process capability meets CTQs.
> - **Verify:** validate with pilots/prototypes; confirm customer acceptance and operational readiness.
>
> **DMADV vs DMAIC:**
> **DMAIC** improves an **existing** process to target.
> **DMADV** creates a **new** design to meet CTQs when the current system cannot.

---

## 4) Quality Control (QC) — keeping operations on target

> [!example] Quality Control — Detailed in Chapter 6
>
> Overview here; full QC concepts, feedback loops, and process control covered in [[Chapter 6]]
>
> QC = a **feedback loop** that compares actual vs standard and triggers **predefined actions**.
>
> **Cycle:**
> 1. **Choose control subject** — what matters for customers.
> 2. **Establish measurement** — unit, sensor, opportunity counts.
> 3. **Set standards** — legitimate, measurable, attainable, equitable.
> 4. **Measure actual performance.**
> 5. **Compare to standard** — with numeric action rules.
> 6. **Act on the difference** — regulate the process or remove causes.

> [!example] Case pattern (like the Netflix slide)
> Subjects: content quality, platform KPIs, UX.  
> Measures: bitrate, buffer ratio, subtitle accuracy, crash rate, complaint rate.  
> Standards: ≤2% buffering, ≥98–100% subtitle accuracy, app load <2s.  
> Actions: real-time alerts, triage, corrective deployment.

---

## 5) Self-Control and self-managed processes

> [!example] Self-Control — Related to Feedback Loop
>
> Self-control concept builds on the feedback loop from [[Chapter 6#4 The Feedback Loop]]
>
> **Self-control** reduces inspection cost and increases ownership. Design work so the operator can **see the target, see their performance, and has the authority and means to correct**.
>
> Operator needs:
> - **Knowledge of goals** and specs.
> - **Knowledge of actual performance** in real time.
> - **Authority + ability** to adjust either the process or their own conduct.

> [!warning] Watchouts
> “Empowerment” without information, capability, and clear action rules increases risk. Pair authority with training and simple, numeric criteria.

---

## 6) Measurement that ties the loop
> [!note] Why it matters
> Measurement enables early warning in **control**, quantifies needs and capability in **planning**, and prioritizes and diagnoses in **improvement**.

Know these terms quickly:
- **Unit of measure** (e.g., seconds, ppm).  
- **Sensor** or method.  
- **Opportunity/occurrence** basis for defect rates.

---

## 7) Costs of Quality and QA vs QC

> [!example] Cost of Quality — Revision
>
> Cost of Poor Quality (COPQ) introduced in [[Lecture 10#💰 4. Cost of Poor Quality (COPQ)]]
> QA vs QC distinction covered in [[Chapter 6#3 Relation to Quality Assurance]]
>
> **Prevention** and **Appraisal** happen before shipment. **Internal** and **External Failure** happen when things go wrong, before vs after the customer.
>
> - **QA** designs and standardizes the system to **prevent** defects.
> - **QC** runs feedback during operations to **detect and correct** deviations.

---

## 8) Exam triggers and quick checks

> [!bug] EXAM CRITICAL — Integration Topics
> Speaker 2: "Combination between theory and then applying that"
> Final tutorial theme: "Develop a quality management implementation plan"

> [!check] Likely asked
> - Map a scenario to **DMADV vs DMAIC** and justify.
> - Explain **self-control** and why it cuts inspection cost.
> - Choose **control subjects** that align with customer CTQs and defend measures and standards.

> [!question] 60-second drills
> - How do you ensure process capability matches CTQs at design time?  
> - What makes a standard “legitimate, measurable, attainable, equitable”?  
> - Give one action rule you would predefine for a key metric.

---

## 9) Minimal memory, maximum understanding
> [!tip] Commit to memory
> - Names of the loops: **Juran**, **DMADV**, **QC 6-step**.  
> - One clean example for each.  
> Everything else is logic you can reconstruct from the mental model.

