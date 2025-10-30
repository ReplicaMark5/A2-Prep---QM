
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
> 