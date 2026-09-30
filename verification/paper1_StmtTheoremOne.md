# Verification packet: Paper 1, Theorem 1 (`\StmtTheoremOne`)

Source: `papers/paper1/research/statements.tex` at `cb08121`, copied verbatim; the short reference macros (`\RefDef...`, `\RefAssm...`) are expanded to their text. "This paper" in a quoted statement means Paper 1. All mathematics is LaTeX.

## Statement

`\StmtTheoremOne` (Paper 1):

```latex
\textbf{Theorem 1 (Indistinguishability criterion).} Under the model of Section 3, with common onset time \(\tau\), mechanism instances \((K, \theta_K, b_K)\) and \((F, \theta_F, b_F)\) induce identical distributions over the observation trajectory \(\{y_t\}_{t\ge 0}\) if and only if

\[\theta_K\, C b_K = \theta_F\, C b_F. \tag{$\ast$}\]
```

## Definitions

`\StmtDefOutputModel` (Paper 1):

```latex
\textbf{Definition D1 (Output-level injection model).} Fix \(n, m\), a matrix \(A \in \mathbb{R}^{n\times n}\), an observation matrix \(C \in \mathbb{R}^{m\times n}\), covariance matrices \(Q \in \mathbb{R}^{n\times n}\) and \(\Sigma \in \mathbb{R}^{m\times m}\), and an onset time \(\tau\). Under a mechanism instance \((M, \theta_M, b_M)\) (Definition~D3), the latent state, the perturbed state and the observation evolve for \(t \ge 0\) as
\[\begin{gathered} x_{t+1} = A x_t + w_t, \qquad \tilde x_t = x_t + \mathbb{1}[t \ge \tau]\,\theta_M\, b_M, \\ y_t = C \tilde x_t + \varepsilon_t, \end{gathered}\]
with \(w_t \sim \mathcal{N}(0,Q)\) and \(\varepsilon_t \sim \mathcal{N}(0,\Sigma)\). The injection enters the observation only; the state recursion does not see it. (Section~3 additionally takes \(m < n\); no statement below uses that restriction.)
```

`\StmtDefMechanismInstance` (Paper 1):

```latex
\textbf{Definition D3 (Mechanism instance).} A mechanism instance is a triple \((M, \theta_M, b_M)\) with cause \(M \in \{K, F\}\) (\(K\): compromise, \(F\): fault), a deterministic severity \(\theta_M \in \mathbb{R}\) and a deterministic injection direction \(b_M \in \mathbb{R}^n\). Statements compare one fixed instance of \(K\) with one fixed instance of \(F\) (pairwise-instance reading); no distribution over severities, directions or onsets within a cause is modelled.
```

`\StmtDefIndistinguishability` (Paper 1):

```latex
\textbf{Definition D4 (Observation window; observational indistinguishability).} An observation window is a set \(W \subseteq \{0, 1, 2, \dots\}\) of time indices, finite or not; the observation trajectory on \(W\) is \(Y_W = (y_t)_{t \in W}\). Write \(P_M^W\) for the law of \(Y_W\) under instance \((M,\theta_M,b_M)\) (for infinite \(W\), the law on the product \(\sigma\)-algebra, determined by its finite-dimensional marginals). Instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) are observationally indistinguishable on \(W\) if \(P_K^W = P_F^W\). Theorem~1 uses \(W = \{t : t \ge 0\}\); ``indistinguishable at every \(t \ge \tau\)'' (Theorem~2) means \(P_K^W = P_F^W\) for \(W = \{t : t \ge \tau\}\); Theorem~3 (the finite-horizon version of Theorem~2) uses \(W = \{\tau, \dots, \tau+H-1\}\).
```

## Assumptions

`\StmtAssmNoise` (Paper 1):

```latex
\textbf{(A1) Gaussian, independent noise.} \(w_t \sim \mathcal{N}(0,Q)\) and \(\varepsilon_t \sim \mathcal{N}(0,\Sigma)\), with \(Q\) and \(\Sigma\) symmetric positive semidefinite; the family \(\{w_t\}_{t \ge 0} \cup \{\varepsilon_t\}_{t \ge 0}\) is mutually independent (across time and across the two sequences), and its law does not depend on the instance.
```

`\StmtAssmInit` (Paper 1):

```latex
\textbf{(A2) Deterministic initial state.} \(x_0 = 0\). (The proofs use only that \(x_0\) is Gaussian, possibly degenerate, independent of the noise, with a law that does not depend on the instance; \(x_0 = 0\) is the implemented special case.)
```

`\StmtAssmCommon` (Paper 1):

```latex
\textbf{(A3) Known, common model.} \(A\), \(Q\), \(C\), \(\Sigma\) are known and identical under both causes; only the injection term \(\theta_M b_M\) depends on the instance.
```

`\StmtAssmOnset` (Paper 1):

```latex
\textbf{(A4) Common onset.} The onset \(\tau\) is deterministic, common to both causes, not necessarily known to the operator. (The proofs use only that \(\tau\) is deterministic and common; no statement requires a policy to know \(\tau\).)
```

`\StmtAssmWindow` (Paper 1):

```latex
\textbf{(A5) Window reaches the onset.} The observation window \(W\) contains at least one \(t \ge \tau\). Theorem~2 uses the stronger form \(W \supseteq \{t : t \ge \tau\}\) and Theorem~3 the stronger form \(W \supseteq \{\tau, \dots, \tau+H-1\}\).
```

## Notation

```latex
- \(\mathbb{1}[\cdot]\) is the indicator; \(\mathcal{N}(\mu, V)\) is the Gaussian law with mean \(\mu\) and covariance \(V\).
- In Paper 1, "the model of Section 3" is Definition D1 (output-level injection model).
- "Identical distributions over the observation trajectory \(\{y_t\}_{t\ge 0}\)" means observational indistinguishability on the window \(W = \{t : t \ge 0\}\) (Definition D4), i.e. \(P_K^W = P_F^W\), with (A5) for this window.
```
