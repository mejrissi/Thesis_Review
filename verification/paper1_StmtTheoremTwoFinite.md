# Verification packet: Paper 1, Theorem 2 (finite-horizon version) (`\StmtTheoremTwoFinite`)

Source: `papers/paper1/research/statements.tex` at `919c38d`, copied verbatim; the short reference macros (`\RefDef...`, `\RefAssm...`) are expanded to their text. All mathematics is LaTeX.

## Statement

`\StmtTheoremTwoFinite` (Paper 1):

```latex
\textbf{Theorem~2 (finite-horizon version).} Under the state-level injection model, let \(\Delta_0 = \theta_K b_K - \theta_F b_F\), let \(H \ge 1\) be the number of post-onset observations, and define
\[G_H = \begin{bmatrix} C \\ C(I+A) \\ \vdots \\ C\sum_{j=0}^{H-1}A^j \end{bmatrix}.\]
Mechanism instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) induce the same law of the observations over the window of \(H\) post-onset observations if and only if \(G_H\Delta_0 = 0\), which holds if and only if \(CA^j\Delta_0 = 0\) for \(j = 0, \dots, H-1\). If \(H \ge n\), this is equivalent to the all-time condition of Theorem~2, \(\Delta_0 \in \bigcap_{k=0}^{n-1}\ker(CA^k)\).
```

## Definitions

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
\textbf{Definition D4 (Observation window; observational indistinguishability).} An observation window is a set \(W \subseteq \{0, 1, 2, \dots\}\) of time indices, finite or not; the observation trajectory on \(W\) is \(Y_W = (y_t)_{t \in W}\). Write \(P_M^W\) for the law of \(Y_W\) under instance \((M,\theta_M,b_M)\) (for infinite \(W\), the law on the product \(\sigma\)-algebra, determined by its finite-dimensional marginals). Instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) are observationally indistinguishable on \(W\) if \(P_K^W = P_F^W\). Theorem~1 uses \(W = \{t : t \ge 0\}\); ``indistinguishable at every \(t \ge \tau\)'' (Theorem~2) means \(P_K^W = P_F^W\) for \(W = \{t : t \ge \tau\}\); the finite-horizon version of Theorem~2 uses \(W = \{\tau, \dots, \tau+H-1\}\).
```

`\StmtDefObservability` (Paper 1):

```latex
\textbf{Definition D6 (Unobservable subspace; observability).} The (Kalman) unobservable subspace of \((A,C)\) is \(\mathcal{N}(A,C) = \bigcap_{k=0}^{n-1} \ker(CA^k)\). The pair \((A,C)\) is observable if \(\mathcal{N}(A,C) = \{0\}\), equivalently if the stacked matrix
\[\begin{bmatrix} C \\ CA \\ \vdots \\ CA^{n-1} \end{bmatrix}\]
has rank \(n\).
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
\textbf{(A5) Window reaches the onset.} The observation window \(W\) contains at least one \(t \ge \tau\). Theorem~2 uses the stronger forms \(W \supseteq \{t : t \ge \tau\}\) (all-time version) or \(W \supseteq \{\tau, \dots, \tau+H-1\}\) (finite-horizon version).
```

## Notation

```latex
- \(\mathbb{1}[\cdot]\) is the indicator; \(\ker\) is the kernel (null space) of a matrix; \(\mathrm{span}\) is the linear span; \(\Phi\) is the standard normal distribution function; \(\mathcal{N}(\mu, V)\) is the Gaussian law with mean \(\mu\) and covariance \(V\).
- In Paper 1, "the model of Section 3" is Definition D1 (output-level injection model) and "the state-level injection model" is Definition D2.
- \(n\) is the state dimension. "The window of \(H\) post-onset observations" is \(W = \{\tau, \dots, \tau+H-1\}\) (Definition D4), with (A5) in its finite-horizon form.
- "The all-time condition of Theorem 2" is the displayed condition of Paper 1's Theorem 2, reproduced below.
```

### Statements referred to

The statement refers to the statements below. They are reproduced verbatim so that every reference resolves; they are not the statement under verification.

`\StmtTheoremTwo` (Paper 1):

```latex
\textbf{Theorem 2 (State-feedback confounding requires unobservability).} Under the state-level injection model, let \(\Delta_0 = \theta_K b_K - \theta_F b_F\). Mechanism instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) are observationally indistinguishable at every \(t \ge \tau\) if and only if \(\Delta_0\) lies in the unobservable subspace of the pair \((A,C)\), i.e.

\[\Delta_0 \in \bigcap_{k=0}^{n-1} \ker(CA^k),\]

the classical (Kalman) unobservable subspace of \((A,C)\), where \(n\) is the state dimension.
```
