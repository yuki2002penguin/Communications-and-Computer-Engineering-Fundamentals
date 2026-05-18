# Lecture Notes: Algorithms & Computational Complexity

**Course:** ICT.A435 Communications and Computer Engineering - Fundamentals  
**Institution:** Institute of Science Tokyo  
**Lecturer:** Atsushi Takahashi  
**Topic:** Foundations of Algorithm Analysis, Asymptotics, and the P vs. NP Framework  

---

## 1. Introduction: The Core of Algorithm Design
When designing embedded systems, VLSIs, or computer architectures, software design primarily splits into **Algorithms** and **Real-Time Operating Systems (RTOS)**. 

Before writing any line of code, the absolute **first step** of algorithm design is to answer one fundamental question:
> **"Is the problem easy or difficult to solve?"**

To answer this, we must quantify the efficiency of our methods using mathematical frameworks rather than just benchmarking them empirically on a local machine.

---

## 2. Measuring Algorithm Efficiency & Visualization

### Why Benchmarking Small Inputs Fails
If we evaluate three hypothetical algorithms ($\alpha, \beta, \gamma$) with small input sizes ($n$), an algorithm like $\gamma$ might appear to be the fastest because its constant overhead is small. However, as $n \to \infty$:
* High-order polynomial or exponential algorithms slow down drastically.
* Low-order algorithms (e.g., linear, logarithmic) eventually outperform them completely.

### The Power of Log-Log Graphs
To analyze asymptotic behavior, computer scientists plot the relation between **Execution Time $T(n)$** and **Input Size $n$** on a **Log-Log scale**.
* As $n \to \infty$, polynomial time algorithms straighten out into **straight lines**.
* The **slope** of the resulting line represents the order/degree of the polynomial.

### Polynomial vs. Exponential Time
* **Polynomial Time ($O(n^k)$):** Growth is reasonable. It represents problems that are **efficiently computable** and practical for real-world execution.
* **Exponential Time ($O(k^n)$):** Growth is explosive. A minor increase in input size $n$ can cause execution times to scale so rapidly that computing the answer would take **longer than the age of the universe ($\approx 13.8$ billion years)**.

---

## 3. Mathematical Language of Efficiency: Asymptotics

To rigorously classify how fast functions grow without relying on coordinate graphs, we use **Asymptotics**.

### Core Asymptotic Definitions


| Notation | Intuitive Meaning | Analogous Relation | Strict Mathematical Limit Definition |
| :--- | :--- | :--- | :--- |
| **$f(n) = O(g(n))$** | Asymptotically no more than... (Upper bound) | $a \le b$ | $\lim_{n \to \infty} \frac{f(n)}{g(n)} < \infty$ |
| **$f(n) = \Omega(g(n))$** | Asymptotically no less than... (Lower bound) | $a \ge b$ | $\lim_{n \to \infty} \frac{f(n)}{g(n)} \ge c > 0$ |
| **$f(n) = \Theta(g(n))$** | Asymptotically equal to... (Tight bound) | $a = b$ | $f(n) = O(g(n))$ **and** $f(n) = \Omega(g(n))$ |
| **$f(n) = o(g(n))$** | Asymptotically less than... (Strict upper) | $a < b$ | $\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0$ |
| **$f(n) = \omega(g(n))$** | Asymptotically more than... (Strict lower) | $a > b$ | $\lim_{n \to \infty} \frac{f(n)}{g(n)} = \infty$ |

### Standard Order of Growth
$$O(1) \subset O(\log n) \subset O(n) \subset O(n \log n) \subset O(n^k) \subset O(k^n)$$

### Important Theorems Covered in Class
1. **Polynomials:** If $a_0 > 0$, then $a_0n^k + a_1n^{k-1} + \dots + a_k = \Theta(n^k)$.
2. **Factorial Logarithm:** $\log_2 n! = \Theta(n \log_2 n)$.
   * *Proof Sketch for Upper Bound:* $n! = n \times (n-1) \times \dots \times 1 \le n^n \implies \log_2 n! \le n \log_2 n \implies O(n \log_2 n)$.
   * *Proof Sketch for Lower Bound:* $n! \ge (\frac{n}{2})^{\frac{n}{2}} \implies \log_2 n! \ge \frac{n}{2} \log_2 \frac{n}{2} = \frac{1}{2}n\log_2 n - \frac{n}{2} \implies \Omega(n \log_2 n)$.

---

### ⚠️ Critical Class Case Study: Primality Testing (`PRIMES`)
Consider a naive exhaustive search algorithm to determine if an integer $n$ is a prime number (looping $i$ from $2$ to $\sqrt{n}$ to check for divisibility).
* **The Misconception:** The loop runs $\sqrt{n}$ times, so the time complexity is $O(\sqrt{n})$. This looks like polynomial time, right?
* **The Reality:** Time complexity must be calculated relative to the **input size (number of bits)**. An integer $n$ is stored in binary representation with a length of $s \approx \log_2 n$ bits.
* **The Math:** Since $s = \log_2 n$, we know $n \approx 2^s$. Substituting this into the runtime gives:
  $$O(\sqrt{n}) = O(\sqrt{2^s}) = O(2^{s/2})$$
* **Conclusion:** Because the time complexity scales as an **exponential function** of the input size $s$, this naive algorithm is actually **Exponential Time**!
* *Professor's Note:* It wasn't until 2004 that Agrawal, Kayal, and Saxena proved that `PRIMES` is actually in **P** (meaning a true deterministic polynomial-time algorithm exists).

---

## 4. The Complexity Landscape: P vs. NP Framework

To classify theoretical problem difficulty, we analyze **Decision Problems** (problems whose answers are strictly a `YES` or `NO`).



### 1. Defining P and NP
* **P (Deterministic Polynomial Time):** The set of decision problems that can be **solved** by a deterministic algorithm in polynomial time. (i.e., *Easy to solve*).
* **NP (Nondeterministic Polynomial Time):** The set of decision problems that can be **verified** by a deterministic algorithm in polynomial time, given an "evidence/certificate". (i.e., *Easy to check*).
  * *Nondeterministic Mechanism:* Step 1 guesses a potential solution (evidence) out of exponential candidates. Step 2 deterministically checks it in polynomial time. If the evidence is valid, it outputs `YES`.
* **The Great Conjecture:** It is obvious that $P \subseteq NP$. The unresolved question in computer science is whether $P \neq NP$ (meaning some problems can be easily checked but are fundamentally impossible to solve quickly).

### 2. Polynomial-Time Reduction ($\propto$)
Reduction defines the relative difficulty between two separate problems:
$$\Pi_1 \propto \Pi_2$$
* **Definition:** An instance of problem $\Pi_1$ can be transformed into an instance of problem $\Pi_2$ in polynomial time while keeping the `YES`/`NO` answer identical.
* **Implication:** $\Pi_2$ is **at least as difficult as** $\Pi_1$ ($\Pi_2$ is not easier than $\Pi_1$). If a polynomial-time algorithm is discovered for $\Pi_2$, then $\Pi_1$ can automatically be solved in polynomial time as well.

### 3. NP-Complete (NP-C) and NP-Hard
* **NP-Complete (NP-C):** The hardest problems inside the NP class. A problem $\Pi_0$ is NP-complete if:
  1. $\Pi_0 \in NP$
  2. $\forall \Pi \in NP, \Pi \propto \Pi_0$ (All problems in NP reduce to it).
  * *Examples:* `SAT`, `3-SAT`, `3-COLORING`, `(n²-1)-PUZZLE`, Hamiltonian Graph (`HG`).
* **NP-Hard:** Problems that are **at least as hard as** the hardest problems in NP, but do not have to be in the NP class themselves.
  * *Optimization Problems* (e.g., finding the *shortest* path, minimizing costs) cannot be classified as NP-complete because they aren't simple `YES/NO` decision problems. However, if their decision variants are NP-complete, the optimization problem is defined as **NP-hard**.

---

## 5. Summary: Engineering Roadmap for Algorithm Design

When entering the workforce or starting a system design project, follow this structured blueprint to tackle computational problems efficiently:

### Step 1: Check Problem Tractability
Assess whether your problem is computationally easy or difficult, assuming $P \neq NP$.

### Step 2: Branch Based on Complexity
1. **If the problem is Easy (in Class P):**
   * Strive for the exact mathematical solution.
   * Focus engineering efforts on reducing time/space complexity (e.g., optimizing code structure, hardware synthesis, or compiler tweaks).
2. **If the problem is Difficult (NP-Complete / NP-Hard):**
   * Accept that finding a perfectly fast and exact solution is practically impossible.
   * Immediately pivot your strategy. Do not waste development time on exact calculations. Instead, design:
     * **Approximation Algorithms:** To find a provably good solution close to the optimum.
     * **Heuristic Algorithms:** To find a "good enough" solution quickly under realistic operational boundaries.
