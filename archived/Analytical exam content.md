
> [!danger] **EXAM FOCUS — RELIABILITY ENGINEERING (A2)**
>
> 🎯 **Everything you must know analytically and conceptually**
>
> **1. Reliability Calculations**
> - Compute system reliability for **series**, **parallel (active & standby)**, and **k-out-of-w** configurations.  
> - Apply **Poisson models** for active standby systems.  
> - Understand **component importance** using $I_i = \frac{\partial R_S}{\partial R_i}$.
>
> **2. Laplace Trend Test**
> - Interpret $U$:  
>   - $U < -2$: improving → NHPP $(\beta < 1)$  
>   - $-2 < U < 2$: no trend → HPP (Exponential)  
>   - $U > 2$: degrading → NHPP $(\beta > 1)$  
> - Decide model type (**HPP/NHPP**) based on trend.  
> - Be able to compute $U$ and classify correctly.
>
> **3. Non-Repairable Systems (Weibull / Exponential)**
> - Know **PDF**, **CDF**, **Reliability**, and **Hazard** functions.  
> - Calculate **expected lifetime** analytically: $E[X]=\eta\Gamma\!\left(1+\frac{1}{\beta}\right)$.  
> - Compute **residual life** symbolically via integration; no closed form for $\beta \neq 1$.  
> - Understand that $\beta = 1$ ⇒ Exponential (constant hazard).  
> - Recognise when **numerical lookup** (integration tables in Excel) is required.
>
> **4. Repairable Systems (NHPP / HPP)**
> - **HPP**: constant failure rate ($\alpha_1 = 0$ or $\delta = 1$).  
> - **NHPP (Log-linear):**  
>   - $E[T_{r+1}\mid T_r]=\frac{\ln[(r+1)\alpha_1 + e^{\alpha_0}] - \alpha_0}{\alpha_1}$  
>   - $R(t_1\rightarrow t_2)=\exp\!\left[-\frac{e^{\alpha_0+\alpha_1t_2}-e^{\alpha_0+\alpha_1t_1}}{\alpha_1}\right]$  
> - **NHPP (Power-law):**  
>   - $E[T_{r+1}\mid T_r]=\left(\frac{1+\lambda T_r^{\delta}}{\lambda}\right)^{1/\delta}$  
>   - $R(t_1\rightarrow t_2)=e^{-\lambda(t_2^{\delta}-t_1^{\delta})}$  
> - Understand **MTBF** and how it differs from residual life.  
> - Analytic calculation applies only to **next event times**, not residual life.
>
> **5. Availability**
> - Derive and calculate:  
>   - $A=\frac{\text{MTBF}}{\text{MTBF}+\text{MTTR}}=\frac{\mu}{\lambda+\mu}$  
>   - Time-dependent availability: $A(t)=\frac{\mu}{\lambda+\mu}+\frac{\lambda}{\lambda+\mu}e^{-(\lambda+\mu)t}$.  
> - Apply to **series**, **parallel**, and **standby** systems.
>
> **6. Exam Guidelines**
> - Everything analytical can be computed with the provided formulas.  
> - **Not examinable:**  
>   - Confidence intervals / uncertainty bounds  
>   - Long-term cost optimization  
> - Expect:  
>   - $\approx$40 marks Reliability Engineering (A2)  
>   - 10 marks theory, 30 marks calculation  
>   - Mix of reliability, availability, importance, and trend test questions.  
> - Possible **Reliability Block Diagram** question (like Quiz 3 F1 car).  
> - A3 exam uses same scope and formulas (different data).
>
> ✅ **Study Strategy:**  
> Revise all worked examples, lecture notes, tutorials, and the three quizzes.  
> If you can perform each analytic calculation manually from your formula sheet, you are fully prepared.

