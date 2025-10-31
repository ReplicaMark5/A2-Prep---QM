
Explain to me how the optimisation part works. Let's say we take an paper airplane and use three different cardboard papers weighted and then use a paperclip and add it to the airplane on some and then also add in another factor of maybe using different lengths. And the for all the experiment combinations we measure the distance the plain flys. Explain to me the sequence of steps in this process

---
# GEMINI

> That's a fantastic real-world example! Using the paper airplane experiment helps explain the sequence perfectly. The "optimisation part" is the final phase, which you reach after you've identified the key factors.
Here is the sequence of steps, using your paper airplane example:
> 1. 🔍 Screening Phase: Find the Key Factors
> (Design: Fractional Factorial)
> Goal: Quickly test all three of your initial factors (Paper Weight, Paperclip Placement, Plane Length) to see which ones actually influence the distance the plane flies.
>  * Setup: You'd run a Fractional Factorial design, using only a subset of all possible combinations. This is efficient for checking many factors.
>    * Factors/Levels:
>      * A: Paper Weight: (Light vs. Heavy)
>      * B: Paperclip: (No Clip vs. Clip on Nose)
>      * C: Length: (Short vs. Long)
>    * Run Example: Instead of running all 8 combinations (a full factorial), you might run only 4 combinations (e.g., Light/No Clip/Short, Heavy/Clip/Short, Light/Clip/Long, Heavy/No Clip/Long).
>  * Outcome: You analyse the data and find that Paper Weight (A) and Paperclip (B) are highly influential, but Length (C) has a negligible effect. You now discard Length (C) for the next phase.
> 1. 🤝 Characterisation Phase: Understand Effects & Interactions
> (Design: Full Factorial / Centre Points)
> Goal: Thoroughly understand how your vital few factors (Paper Weight and Paperclip) work together, and check if the relationship is linear.
>  * Setup: You switch to a Full Factorial design on the remaining vital factors (A and B). Since there are now only two, you test all 2^2=4 combinations.
>    * Run Example: (1) Light/No Clip, (2) Heavy/No Clip, (3) Light/Clip, (4) Heavy/Clip. You replicate these runs to reduce noise.
>    * Crucial Step: You check for an Interaction. An interaction means the effect of the Paperclip depends on the Paper Weight (e.g., the clip helps the Light paper a lot, but hurts the Heavy paper).
>    * You also add centre points (e.g., a "Medium" weight paper with a "Mid-Nose" clip placement) to check if the relationship is curved (nonlinear).
>  * Outcome: You confirm that both factors are significant, and you observe a clear interaction—the best distance occurs with Heavy paper AND a Clip on the Nose. The centre points suggest there might be a better setting between Heavy and Light.
> 1. 📈 Optimisation Phase: Find the Exact Best Setting
> (Design: Response Surface Methods - RSM)
> Goal: Since you found a significant interaction and curvature, you now escalate to RSM to map the response and locate the exact optimum distance.
>  * Setup: You use a specialized design (like a Central Composite Design) that adds more levels and points around the promising region found in Step 2.
>    * Variables: You treat Paper Weight and Clip Position as continuous variables (e.g., Weight in grams, Clip position in millimeters from the nose).
>    * Data Collection: You run tests at several new, intermediate settings (e.g., Slightly Heavy paper, Clip 5\text{mm} back).
>  * Analysis (How the Optimisation Works):
>    * Fit a Surface: You use regression analysis to fit a mathematical surface to all your distance data. This surface is usually a quadratic (curved) equation:
>      
>    * Locate the Peak: You then use calculus (or specialized software) to find the absolute peak of this fitted surface.
>  * Final Result: The analysis tells you the optimal combination is, for example, "Paper Weight of 75 grams and a Clip Position of 3\text{mm} from the nose," which maximizes the distance the paper airplane flies.

---

# GROK EXAMPLE 


Applying Design of Experiments (DoE): A Step-by-Step Guide with a Real-World Example

What is DoE?  
DoE is a structured, scientific method to run controlled experiments that reveal which inputs (factors) most affect your output (response variable), how those inputs interact with each other, and the best settings to achieve your goal—all with the fewest experiments possible.

Unlike OFAT (One Factor At a Time)—where you change only one thing while “holding others constant” (which wastes time, misses interactions, and gives narrow results)—DoE tests smart combinations efficiently, giving reliable, causal insights (true cause-and-effect, not just correlations).

Our Example: Optimizing Laundry Detergent Performance

Goal: Maximize whiteness score (response variable: a 0-100 measurement of how white clothes get after washing; higher = better).  
Problem: Three detergents (A, B, C) perform inconsistently across machines and temperatures. We suspect interactions (e.g., Detergent A shines at high temp but flops at low).  
Why DoE? OFAT might test detergents one-by-one on one machine/temp, missing how temp boosts B but hurts C.

We’ll go through 7 practical phases you can copy-paste into any project. Each phase builds on the last, escalating from simple screening to optimization.

  

Phase 1: Define the Objective and Response Variable

What to do: Clearly state your goal (e.g., “maximize” or “minimize”) and pick a repeatable, measurable output (response). Define the effect size worth detecting (e.g., “5-point whiteness improvement”).  
Why? Keeps you focused; avoids vague “improve everything.”

Example:

- Objective: Maximize whiteness score by ≥10 points.
- Response: Whiteness (measured by a colorimeter device post-wash).
- Success metric: Proven settings for 95+ whiteness across machines.  
    Checklist: Is it quantifiable? Yes → Proceed.

  

Phase 2: Brainstorm and Select Factors + Levels

What to do: List controllable inputs (factors) that might matter. Pick 2 levels per factor (low/high) for screening—safe, realistic ranges. Start with 5-7 factors max (too many = too many runs).

Key terms:

- Factor: Anything you can control (e.g., temperature).
- Level: Specific setting (e.g., low=40°C, high=60°C).

Example:

|   |   |   |   |
|---|---|---|---|
|Factor|Low Level|High Level|Why?|
|Detergent Type|A|C|B as center later|
|Temperature|40°C|60°C|Common washer range|
|Wash Cycle|Short|Long|Time saver?|
|Machine|Machine 1|Machine 2|Nuisance (block it!)|

Pro tip: Use Ishikawa (fishbone) diagram if stuck—categorize factors (machine, method, material).

  

Phase 3: Choose the Right Design

What to do: Pick a design matrix (table of runs) based on factors/time:

- Screening (many factors, few runs): Fractional factorial (tests subset of combos; assumes rare higher interactions).
- Full understanding: Full factorial (all combos; e.g., 3 factors = 8 runs).
- Curvature? Add center points (mid-levels).
- Nuisances? Block (group runs with fixed nuisance).

Key designs (from simple to advanced):

|   |   |   |   |
|---|---|---|---|
|Scenario|Design|Runs (3 factors)|Learns…|
|Screen fast|Fractional|4-8|Vital few factors|
|Full effects|Full Factorial|8|Main effects + interactions|
|2 nuisances|Latin Square|9|But assumes NO interactions—risky!|
|Optimize curve|RSM (Response Surface)|15+|Best settings|

Example: Start with 2² Full Factorial (Detergent A/C, Temp low/high = 4 runs). Block by Machine (run all on Machine 1, then all on Machine 2). Replicate 2x (total 16 runs—cheap!).

Generated Design Matrix (random order later):

|   |   |   |   |   |
|---|---|---|---|---|
|Run|Detergent|Temp|Machine (Block)|Expected Whiteness|
|1|A (low)|Low|1|?|
|2|A|High|1|?|
|…|…|…|…|…|

Tools: Free software like Minitab/JMP or Excel add-ins generate this.

  

Phase 4: Plan Execution (The “Bulletproof” Setup)

What to do:

- Randomize run order (shuffle to kill time/bias).
- Replicate (repeat treatments; cuts noise—random variation).
- Block (fix nuisances within groups).
- Balance/Orthogonal (equal high/low; effects don’t “leak”).

Key terms:

- Replication: Same combo 2-3x (e.g., Run 1 twice).
- Blocking: Run blocks where nuisance is constant (e.g., all Machine 1 together).
- Randomisation: Excel RAND() → sort.
- Orthogonality: Effects estimated cleanly (math magic—design ensures it).

Example Plan:

- 16 runs total: 2 blocks (machines) × 2 replicates × 4 combos.
- Random order per block: E.g., Block 1: Run 3,1,4,2.
- Prep: Calibrate machines, train operators.

  

Phase 5: Run the Experiments

What to do: Execute exactly as planned. Record response + any covariates (observed extras, e.g., water hardness).

Example Results (hypothetical—your real data here):

|     |                   |      |         |           |
| --- | ----------------- | ---- | ------- | --------- |
| Run | Detergent         | Temp | Machine | Whiteness |
| 1   | A                 | Low  | 1       | 75        |
| 2   | A                 | High | 1       | 92        |
| 3   | C                 | Low  | 1       | 80        |
| 4   | C                 | High | 1       | 88        |
| …   | (Repeats/Block 2) | …    | …       | Avg 85    |

Tip: Log everything—photos, notes.

  

Phase 6: Analyze the Data

What to do:

1. Plots first (visual!):

- Main effects plot: Avg response at low vs high per factor (steep line = big effect).
- Interaction plot: Lines for factor pairs (parallel = no interaction; crossing/sloping = interaction).

3. Stats: ANOVA (tests if effects > noise; p<0.05 = significant). Software does it.

Example Insights:

- Main effects: Temp huge (+15 points high). Detergent minor.

Main Effects Plot:

Temp: Low=78 --- High=92 (steep!)

Detergent: A=82 -- C=85 (flat)

- Interaction plot:

Temp Low: A=75, C=80 (C better)

Temp High: A=92, C=88 (A better!) → **Interaction!** (lines cross)

- ANOVA: Temp p=0.001 (huge), Interaction p=0.03 (real).

Curvature? Add centers (mid-temp=50°C); if U-shaped, go RSM.

  

Phase 7: Interpret, Optimize, and Iterate

What to do:

- Key effects: “Temp high + Detergent A = winner.”
- Next: RSM for fine-tune (e.g., exact temp 55-65°C).
- Validate: Run optimal 3x in production.
- Report: Plots + recommendations.

Example Conclusion:

- Optimal: Detergent A + 58°C + Long cycle.
- Gain: Whiteness 95 (from 80 baseline).
- Savings: 16 runs vs OFAT’s 50+.
- If interactions missed? Escalate to full factorial.

  

Quick Wins for Any Project

- Time-crunched? Fractional screen → vital 2-3 factors → full.
- Traps: No randomize = bias. Few replicates = noise wins. Assume no interactions = wrong!
- Scale up: Screening (Phase 1-3) = 1 day; Full project = 1 week.

Bottom line: Follow these phases → causal proof + optimal settings with 80% fewer runs than guessing/OFAT. Try it on your next problem! Questions? Paste your factors—I’ll build your design.


# grok phases

Prompt:


> Core Purpose of DoE
> 
> 1.  Screen — Find the vital few factors from many suspects.
> 
> 2.  Characterize — Measure how much each factor matters and how they interact.
> 
> 3.  Optimize — Find the best settings for maximum/minimum response.
> 
> 
> Are these phases of doe or just the purpose on its own?
> 


They are the core purposes of DoE — not phases.

  

Clear Distinction (Exam-Ready)

|   |   |
|---|---|
|Core Purposes (What DoE is FOR)|Phases (How you APPLY DoE)|
|1. Screen – Identify the vital few factors|Phase: Screening experiment (e.g., fractional factorial)|
|2. Characterize – Quantify main effects + interactions|Phase: Follow-up full factorial or augmented design|
|3. Optimize – Find best settings|Phase: Response Surface Methodology (RSM)|

EXAM PHRASE:  
“The three purposes of DoE are screening, characterization, and optimization — achieved through sequential phases of experimental designs.”

  

Why the Difference Matters

- Purposes = Why you use DoE → strategic goals
- Phases = How you do it → tactical steps/designs

You can use one DoE for one purpose — or sequence them:

Screen (Purpose 1) → Characterize top factors (Purpose 2) → Optimize (Purpose 3)

  

Bottom Line (Memorize This)

“Screen, Characterize, Optimize” are the three core purposes of DoE — not phases.  
They guide which design you choose in which phase of your project.

You’re exam-safe. Say:  
“The purpose is to screen, characterize, and optimize — using appropriate designs in sequence.”



