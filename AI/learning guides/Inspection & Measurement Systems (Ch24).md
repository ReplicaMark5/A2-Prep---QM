
**Chapter 24** – Inspection, Test & Measurement
_Source: Lecture 17 (Quality Management 444 – Prof Imke de Kock)_

---

## 1 | Purpose and Role

> [!example] Quality Control Context — Builds on Chapter 6
>
> Inspection and testing are **Quality Control tools**, introduced in [[Quality Control & Feedback Loops (Ch6)]]
> Also relates to measurement concepts from [[Quality Management Integration (L15)#6) Measurement that ties the loop]]
>
> Inspection and testing sit inside **Quality Control**, not planning or improvement.
> Their job is to **compare what was made** to **what was specified** — confirming if an output conforms to requirements.
>
> **Key idea:**
> Inspection + Testing = Operational verification of quality.
> They ensure a product, part, or service is _adequate for its intended use._

---

## 2 | Inspection vs Testing

**Inspection** looks at the **state or appearance** of a product.

- Can be **visual**, **destructive**, or involve **precise measurement**.
    
- Happens under **static** conditions.
    
- Checks conformance to a **design standard** (within UCL/LCL limits).
    

**Testing** evaluates **functionality during operation.**

- Run on complex assemblies or systems.
    
- Seeks to confirm **functional performance** over a reasonable period.
    

> [!question] Why the difference matters  
> Inspection asks, “Does it _look and measure_ right?”  
> Testing asks, “Does it _work_ right?”

In modern systems, this line blurs—both serve the same aim: **prove reliability before use.**

---

## 3 | Why We Inspect or Test

The overarching reason: **Product Acceptance.**

Acceptance decisions rest on three judgments:

1. **Conformance:** Does it meet specification?
    
2. **Fitness for use:** Can it still function if slightly off-spec?
    
3. **Communication:** Who must know about the outcome?
    

> [!learn] Fit-for-use ≠ Perfect conformance  
> A product may deviate slightly yet still satisfy the customer’s purpose safely and economically.

---

## 4 | Decisions After Inspection

### A. Fitness-for-Use

Think like the end-user:  
Who will use it? Under what risk, urgency, and cost conditions?  
If a defect has no impact on function or safety, it may still be accepted.

### B. Communication

Two directions:

- **Outsiders** (customers): must know when quality varies.
    
- **Insiders** (operators, inspectors): often unaware of such waivers — this gap can weaken learning loops.
    

> [!danger] LEARN THIS  
> Hidden acceptance decisions reduce system feedback → recurring defects.

### C. Disposition of Non-Conforming Product

|Action|Examples|
|:--|:--|
|**Do not ship**|Rework, scrap, return to supplier|
|**Ship with waiver**|Approved by designer, customer, or MRB|
|**Corrective action**|Distinguish between sporadic fix vs chronic root-cause issue|

> [!tip] Always trace _why_ a waiver was given — it signals tolerance levels and risk appetite.

---

## 5 | Inspection Planning

Choosing **where and when** to inspect determines efficiency.  
Typical checkpoints:

- At **receiving**, **setup approval**, or **critical operations**
    
- **Between departments**
    
- **Before shipping** or any **irreversible step**
    
- At **natural windows** (logical process pauses)
    

> [!question] Think about flow  
> Each inspection point acts as a feedback gate to stop defects early and cheaply.

---

## 6 | Selecting Quality Characteristics

Inspectors verify the **vital few** characteristics tied directly to **fitness for use**, not every measurable detail.  
Designers know the reasoning behind specs, but inspectors often don’t — a key communication gap.

Bridging that gap means:

- Simulating real-use conditions during tests.
    
- Providing contextual info (“why this spec matters”).
    
- Training inspectors and supervisors.
    
- Using **seriousness classification** to prioritize checks.
    

> [!learn] Seriousness Classification  
> Not all defects are equal — classify them by their effect on safety, function, and customer perception (usually 3–4 levels).

---

## 7 | Accuracy and Measurement Error

Every measurement system contributes its own variation.  
To interpret data correctly, we must separate **process variation** from **measurement variation**:

$$
\sigma^2_{total} = \sigma^2_{process} + \sigma^2_{measurement}
$$

> [!question] What defines “good measurement”?
> 
> - **Bias (Accuracy):** how close the average reading is to the true value.
>     
> - **Precision:** how repeatable readings are.
>     

If measurement error is large or unknown, improvement decisions lose validity.

> [!danger] LEARN THIS  
> You cannot control what you cannot measure reliably.

---

## 8 | Putting It Together

Inspection and testing exist to:

- Provide **evidence** of quality.
    
- Support **acceptance decisions** based on risk, cost, and use.
    
- Feed data back into **process control and improvement** loops.
    

> [!summary] Core Takeaways
> 
> - Understand **why** inspection occurs, not just **how**.
>     
> - Link every measurement to its decision purpose.
>     
> - Prioritize characteristics that affect customer safety and satisfaction.
>     
> - Never separate measurement quality from process quality.
>     

---

**End of Chapter 24 Study Note**  
_(Built for conceptual mastery; revisit callouts marked “LEARN THIS” for high-probability exam content.)_

---

https://chatgpt.com/share/690388f7-10ac-8013-8d53-7992401029e6