# Verification packet: Paper 4, Lemma L1 (`\StmtLemmaBlindValue`)

Source: `papers/paper4/research/statements.tex` at `33801b4`, copied verbatim; the short reference macros (`\RefFour...`) are expanded to their text. All mathematics is LaTeX. The Paper 1 and Paper 2 items are copied verbatim from `papers/paper1/research/statements.tex` and `papers/paper2/research/statements.tex` at the same commit, with their short reference macros (`\RefDef...`, `\RefAssm...`) expanded; "this paper" in a Paper 1 item means Paper 1. Paper 4's statements file has no `\Stmt...Uses` macros: the definitions and assumptions below are those the statement names or whose symbols it uses.

## Statement

`\StmtLemmaBlindValue` (Paper 4):

```latex
\textbf{Lemma L1 (Excess harm on the blind subspace).} Assume (G-A1) and (G-A3), and write \(\Pi_{\mathcal{B}_W}\) for the orthogonal projection onto the blind subspace \(\mathcal{B}_W = \ker G_W\). Then \(\{\Delta \in \mathbb{R}^n : \lVert \Delta\rVert_2 \le r,\ \Delta^\top M_W \Delta = 0\} = \{\Delta \in \mathcal{B}_W : \lVert\Delta\rVert_2 \le r\}\), and
\[
\begin{aligned}
\mathcal{F}_W(0) &= \max\{\, g^\top \Delta : \lVert \Delta \rVert_2 \le r,\ \Delta^\top M_W \Delta = 0 \,\} \\
&= r\,\lVert \Pi_{\mathcal{B}_W} g \rVert_2 ,
\end{aligned}
\]
attained at \(\Delta = r\,\Pi_{\mathcal{B}_W} g/\lVert \Pi_{\mathcal{B}_W} g\rVert_2\) when \(\Pi_{\mathcal{B}_W} g \ne 0\) and at \(\Delta = 0\) otherwise.
```

## Definitions

`\StmtDefObservation` (Paper 4):

```latex
\textbf{Definition G2 (Observation model and stealth geometry).} The system follows Paper~1's output-level model (Paper~1, Definition~D1) or its state-level model (Paper~1, Definition~D2), with a finite window \(W \supseteq \{\tau, \dots, \tau + H - 1\}\), \(H \ge 1\). For an injection vector \(x \in \mathbb{R}^n\), write \(P^W_x\) for the law of \(Y_W\) when the injection from the onset on is \(x\). Under (G-A1) every \(P^W_x\) is Gaussian with a covariance \(V_W \succ 0\) that does not depend on \(x\), and mean \(\mu_W + G_W x\), where \(G_W\) stacks, for \(t \in W\), the zero block if \(t < \tau\), and for \(t = \tau + j\), \(j \ge 0\),
\[
C \ \ \text{(output-level)}, \qquad C \textstyle\sum_{i=0}^{j} A^i \ \ \text{(state-level)}.
\]
The \emph{stealth matrix} is \(M_W = G_W^\top V_W^{-1} G_W \succeq 0\), and the \emph{blind subspace} is \(\mathcal{B}_W = \ker G_W = \ker M_W\).
```

`\StmtDefAttacker` (Paper 4):

```latex
\textbf{Definition G3 (Attacker strategy, payload, budget).} The attacker chooses a severity \(\theta_K \in \mathbb{R}\) and a direction \(b_K \in \mathbb{R}^n\); only the injection vector \(x_K = \theta_K b_K\) enters the observation law (Definition~G2), so a strategy is identified with \(x_K\). The \emph{payload} is \(\Delta = x_K - x_F\), the part of the injection that differs from the fault's (Paper~1's \(\Delta_0\)). The admissible set is the payload budget
\[
\mathcal{X}_r = \{\, x_K \in \mathbb{R}^n : \lVert x_K - x_F \rVert_2 \le r \,\}, \qquad r > 0 .
\]
```

`\StmtDefStealth` (Paper 4):

```latex
\textbf{Definition G4 (\(\varepsilon\)-stealth).} For \(\varepsilon \in [0,1]\), an attacker strategy \(x_K\) is \emph{\(\varepsilon\)-stealthy on \(W\)} if \(\mathrm{TV}(P^W_{x_K}, P^W_{x_F}) \le \varepsilon\) (total variation as in Paper~1, Definition~D10). The \(\varepsilon\)-stealthy set is \(\mathcal{E}_W(\varepsilon) = \{ x_K \in \mathcal{X}_r : \mathrm{TV}(P^W_{x_K}, P^W_{x_F}) \le \varepsilon \}\). Under (G-A1), with \(d_W(\Delta) = \sqrt{\Delta^\top M_W \Delta}\),
\[
\mathrm{TV}(P^W_{x_K}, P^W_{x_F}) = 2\,\Phi\!\big(d_W(\Delta)/2\big) - 1,
\]
\[
\mathcal{E}_W(\varepsilon) = \{ x_K \in \mathcal{X}_r : d_W(x_K - x_F) \le \rho_\varepsilon \},
\]
where
\[
\rho_\varepsilon = 2\,\Phi^{-1}\!\big(\tfrac{1+\varepsilon}{2}\big), \qquad \rho_1 = +\infty .
\] \(\varepsilon = 0\) is exact confounding on \(W\) (Paper~1, Definition~D4).
```

`\StmtDefPayoffs` (Paper 4):

```latex
\textbf{Definition G7 (Harm and payoffs).} Fix a \emph{harm vector} \(g \in \mathbb{R}^n\). The attacker's \emph{excess harm} is the linear functional \(h(\Delta) = g^\top \Delta\) of its payload: the harm it extracts beyond what the fault it imitates would cause. The attacker's payoff against rule \(\pi\) is the expected excess harm extracted before containment, net of a capture loss \(c_A \ge 0\):
\[
U_A(\pi, x_K) = h(x_K - x_F)\,\big(1 - \beta_\pi(x_K)\big) - c_A\,\beta_\pi(x_K).
\]
The operator's expected cost is Paper~1's loss table (Definition~D8, general symbols) with the leave-a-compromise entry raised by the extracted harm, \(H_K + h(\Delta)\):
\[
J(\pi, x_K) = p\,\Big(\beta_\pi(x_K)\,C_K + \big(1-\beta_\pi(x_K)\big)\big(H_K + h(\Delta)\big)\Big) + (1-p)\,\big(\alpha_\pi\,C_F + (1-\alpha_\pi)\,H_F\big) + \mathrm{Ver}_\pi(x_K),
\]
where \(\mathrm{Ver}_\pi\) is the expected verification cost \(c_v + \mathbb{1}[M = K]\,r_K \tau_v\) incurred on the event that \(\pi\) verifies (Paper~2, Definition~4), and zero for a rule without verification. The game is not zero-sum (\(U_A \ne -J\) in general).
```

`\StmtDefFrontier` (Paper 4):

```latex
\textbf{Definition G9 (Stealth--harm frontier, detection--harm frontier, harm ceiling).} The \emph{stealth--harm frontier} on \(W\) is
\[
\mathcal{F}_W(\varepsilon) = \sup\{\, h(x - x_F) : x \in \mathcal{E}_W(\varepsilon) \,\}, \qquad \varepsilon \in [0,1],
\]
which does not depend on the operator's rule. The \emph{detection--harm frontier against a rule \(\pi\)} is
\(\Psi_\pi(\beta) = \sup\{\, h(x - x_F) : x \in \mathcal{X}_r,\ \beta_\pi(x) \le \beta \,\}\), \(\beta \in [0,1]\).
The \emph{harm ceiling} is \(\bar{\mathcal{F}}_W = \lim_{\varepsilon \downarrow 0} \mathcal{F}_W(\varepsilon)\) (the limit exists since \(\mathcal{F}_W\) is nondecreasing).
```

`\StmtDefOutputModel` (Paper 1):

```latex
\textbf{Definition D1 (Output-level injection model).} Fix \(n, m\), a matrix \(A \in \mathbb{R}^{n\times n}\), an observation matrix \(C \in \mathbb{R}^{m\times n}\), covariance matrices \(Q \in \mathbb{R}^{n\times n}\) and \(\Sigma \in \mathbb{R}^{m\times m}\), and an onset time \(\tau\). Under a mechanism instance \((M, \theta_M, b_M)\) (Definition~D3), the latent state, the perturbed state and the observation evolve for \(t \ge 0\) as
\[\begin{gathered} x_{t+1} = A x_t + w_t, \qquad \tilde x_t = x_t + \mathbb{1}[t \ge \tau]\,\theta_M\, b_M, \\ y_t = C \tilde x_t + \varepsilon_t, \end{gathered}\]
with \(w_t \sim \mathcal{N}(0,Q)\) and \(\varepsilon_t \sim \mathcal{N}(0,\Sigma)\). The injection enters the observation only; the state recursion does not see it. (Section~3 additionally takes \(m < n\); no statement below uses that restriction.)
```

`\StmtDefStateModel` (Paper 1):

```latex
\textbf{Definition D2 (State-level injection model).} As Definition~D1, except that the perturbed state drives the recursion from the onset on:
\[\begin{gathered} x_{t+1} = A x_t + w_t \ (t < \tau), \qquad x_{t+1} = A \tilde x_t + w_t \ (t \ge \tau), \\ \tilde x_t = x_t + \mathbb{1}[t \ge \tau]\,\theta_M\, b_M, \qquad y_t = C \tilde x_t + \varepsilon_t. \end{gathered}\]
The injection is persistent (added at every \(t \ge \tau\)) and propagates through \(A\).
```

`\StmtDefMechanismInstance` (Paper 1):

```latex
\textbf{Definition D3 (Mechanism instance).} A mechanism instance is a triple \((M, \theta_M, b_M)\) with cause \(M \in \{K, F\}\) (\(K\): compromise, \(F\): fault), a deterministic severity \(\theta_M \in \mathbb{R}\) and a deterministic injection direction \(b_M \in \mathbb{R}^n\). Statements compare one fixed instance of \(K\) with one fixed instance of \(F\) (pairwise-instance reading); no distribution over severities, directions or onsets within a cause is modelled.
```

`\StmtDefIndistinguishability` (Paper 1):

```latex
\textbf{Definition D4 (Observation window; observational indistinguishability).} An observation window is a set \(W \subseteq \{0, 1, 2, \dots\}\) of time indices, finite or not; the observation trajectory on \(W\) is \(Y_W = (y_t)_{t \in W}\). Write \(P_M^W\) for the law of \(Y_W\) under instance \((M,\theta_M,b_M)\) (for infinite \(W\), the law on the product \(\sigma\)-algebra, determined by its finite-dimensional marginals). Instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) are observationally indistinguishable on \(W\) if \(P_K^W = P_F^W\). Theorem~1 uses \(W = \{t : t \ge 0\}\); ``indistinguishable at every \(t \ge \tau\)'' (Theorem~2) means \(P_K^W = P_F^W\) for \(W = \{t : t \ge \tau\}\); Theorem~3 (the finite-horizon version of Theorem~2) uses \(W = \{\tau, \dots, \tau+H-1\}\).
```

`\StmtDefTotalVariation` (Paper 1):

```latex
\textbf{Definition D10 (Observation densities; total variation).} Let \(\mu\) be a \(\sigma\)-finite measure dominating \(P_K\) and \(P_F\) (e.g.\ the finite measure \(P_K + P_F\)), and \(f_K, f_F\) their densities with respect to \(\mu\); \(\int \cdot\, dy\) denotes integration against \(\mu\). The total variation distance is
\[\mathrm{TV}(P,P') = \sup_{B} |P(B) - P'(B)| = \tfrac{1}{2}\int |f - f'|\, dy,\]
so that \(1 - \mathrm{TV}(P_K, P_F) = \int \min\{f_K, f_F\}\, dy\).
```

## Assumptions

`\StmtAssmModel` (Paper 4):

```latex
\textbf{(G-A1) Paper~1's linear-Gaussian model.} Paper~1's standing assumptions (A1)--(A6) hold; written out:
(A1) the process noise \(w_t \sim \mathcal{N}(0,Q)\) and the observation noise \(\varepsilon_t \sim \mathcal{N}(0,\Sigma)\), \(Q, \Sigma\) symmetric positive semidefinite, are mutually independent across time and across the two sequences, with a law that does not depend on the cause or the injection;
(A2) the initial state is \(x_0 = 0\) (any Gaussian \(x_0\) independent of the noise, with a law that does not depend on the cause or the injection, would do);
(A3) \(A\), \(Q\), \(C\), \(\Sigma\) are identical under both causes; only the injection vector depends on the cause;
(A4) the onset \(\tau\) is deterministic and common to both causes;
(A5) the window reaches the onset, here in the stronger form used by Paper~1's Theorem~3: \(W\) is finite and contains \(\{\tau, \dots, \tau+H-1\}\), \(H \ge 1\) (Definition~G2);
(A6) \(\Sigma \succ 0\), hence \(V_W \succ 0\).
The quantities \((A, C, Q, \Sigma)\), \(\tau\) and \(W\) are known to both players ((G-A2)).
```

`\StmtAssmBudget` (Paper 4):

```latex
\textbf{(G-A3) Payload budget.} The attacker's admissible set is \(\mathcal{X}_r\) (Definition~G3) for an \(r > 0\) known to both players ((G-A2)). (Compact and convex; any compact convex admissible set containing \(x_F\) could replace it at the cost of the closed forms.)
```

## Notation

```latex
- \(\mathbb{1}[\cdot]\) is the indicator; \(\mathcal{N}(\mu, V)\) is the Gaussian law with mean \(\mu\) and covariance \(V\); \(\Phi\) is the standard normal distribution function and \(\Phi^{-1}\) its inverse; \(\lVert\cdot\rVert_2\) is the Euclidean norm; \(V \succeq 0\) (\(V \succ 0\)) means positive semidefinite (definite); \(\ker\) is the kernel.
- \(\varepsilon \in [0,1]\) is the stealth level. Paper 1's observation noise \(\varepsilon_t\) always carries a time index.
- \(\tau\) is the onset (Paper 1's (A4)); \(t\) is a time index. \(n\) is the state dimension, \(H \ge 1\) the number of post-onset times in the window.
- \(x_M = \theta_M b_M\) is the injection vector of instance \(M\); only this product enters the observation laws. \(x_F\) is the fault's injection vector, fixed and known ((G-A4), reproduced below). \(\Delta = x_K - x_F\) is the payload.
- \(r > 0\) is the payload budget (Definition G3); \(g\) is the harm vector and \(h(\Delta) = g^\top \Delta\) the excess harm (Definition G7).
- \(b_K, b_F\) are Paper 1's injection directions (Definition D3).
- "Paper 1" and "Paper 2" are two earlier papers of the same thesis. A reference such as "Paper~1, Definition~D1" is to the Paper 1 item reproduced in this packet under the same number.
- Paper 1's Definition D10 is stated for two laws \(P_K, P_F\); it is used here for any two laws \(P, P'\) on the observations (in particular \(P^W_x, P^W_{x'}\)); \(f^W_x\) is the density of \(P^W_x\) with respect to a dominating measure as in Definition D10 (under (G-A1), \(V_W \succ 0\) by Definition G2, so Lebesgue measure on \(\mathbb{R}^{m|W|}\) serves).
- \(\Pi_S\) is the orthogonal projection onto a subspace \(S\).
- In Definition G7 this statement uses only the harm vector \(g\) and the excess harm \(h\); \(\beta_\pi\), \(\alpha_\pi\) (Definition G6), the verification cost \(\mathrm{Ver}_\pi\) and the loss-table entries (Definitions G5, Paper 1's D8, Paper 2's Definition 4) are not used and are not reproduced.
- (G-A2) (the game's information structure) is named in (G-A1) and (G-A3); it is not used by this statement and is not reproduced.
- Paper 1's Theorem 3 is named in (G-A1) only to identify the window form \(W \supseteq \{\tau, \dots, \tau+H-1\}\), which (G-A1) writes out; Paper 1's Theorems 1--3 named in Paper 1's Definition D4 are not reproduced. Paper 1's \(\Delta_0\) (Definition G3) is Paper 1's name for \(\Delta\).
- Paper 1's standing assumptions (A1)--(A6) are written out inside (G-A1); Paper 1's "Section 3" in its Definitions D1 and D8 is its output-level model, Definition D1.
```

### Statements referred to

The statement or the items above refer to the items below. They are reproduced verbatim so that every reference resolves; they are not the statement under verification, and an assumption listed here is a hypothesis of the statement only where the statement says so.

`\StmtAssmFault` (Paper 4):

```latex
\textbf{(G-A4) One fixed fault instance.} Under \(F\) the injection is a fixed, known \(x_F = \theta_F b_F\) (Paper~1's pairwise-instance reading, Definition~D3); no distribution over fault instances is modelled.
```
