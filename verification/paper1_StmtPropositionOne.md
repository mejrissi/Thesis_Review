# Verification packet: Paper 1, Proposition 1 (`\StmtPropositionOne`)

Source: `papers/paper1/research/statements.tex` at `919c38d`, copied verbatim; the short reference macros (`\RefDef...`, `\RefAssm...`) are expanded to their text. All mathematics is LaTeX.

## Statement

`\StmtPropositionOne` (Paper 1):

```latex
Suppose (\(\ast\)) holds (the confounded case), \(0 < p < 1\), \(\mathrm{DISRUPT} > 0\), and \(\mathrm{HARM} > C_{OP} \ge 0\) (harm strictly worse than routine containment --- the assumption the earlier version omitted). Then the best achievable expected cost among policies mapping \(\{y_t\}\) to \(\{\text{contain}, \text{leave alone}\}\) is

\[R^\star = \min\{\,p\,C_{OP} + (1-p)\,\mathrm{DISRUPT},\ \ p\,\mathrm{HARM}\,\},\]

the oracle's expected cost is \(R_{\text{oracle}} = p\,C_{OP}\), and

\[\boxed{\mathrm{CoA}^\star \;=\; R^\star - R_{\text{oracle}} \;=\; \min\{\,(1-p)\,\mathrm{DISRUPT},\ \ p\,(\mathrm{HARM} - C_{OP})\,\} \;>\; 0.}\]
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
\textbf{Definition D4 (Observation window; observational indistinguishability).} An observation window is a set \(W \subseteq \{0, 1, 2, \dots\}\) of time indices, finite or not; the observation trajectory on \(W\) is \(Y_W = (y_t)_{t \in W}\). Write \(P_M^W\) for the law of \(Y_W\) under instance \((M,\theta_M,b_M)\) (for infinite \(W\), the law on the product \(\sigma\)-algebra, determined by its finite-dimensional marginals). Instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) are observationally indistinguishable on \(W\) if \(P_K^W = P_F^W\). Theorem~1 uses \(W = \{t : t \ge 0\}\); ``indistinguishable at every \(t \ge \tau\)'' (Theorem~2) means \(P_K^W = P_F^W\) for \(W = \{t : t \ge \tau\}\); the finite-horizon version of Theorem~2 uses \(W = \{\tau, \dots, \tau+H-1\}\).
```

`\StmtDefLossTable` (Paper 1):

```latex
\textbf{Definition D8 (Loss table).} The general two-action, two-cause loss table \(L(a, M)\), \(a \in \{\text{contain}, \text{leave alone}\}\), \(M \in \{K,F\}\), is
\[\begin{gathered} L(\text{contain}, K) = C_K, \qquad L(\text{contain}, F) = C_F, \\ L(\text{leave alone}, K) = H_K, \qquad L(\text{leave alone}, F) = H_F, \end{gathered}\]
with \(C_K, C_F, H_K, H_F \in \mathbb{R}\). Paper~1's table (Section~3) is the special case
\[C_{OP} = C_K, \qquad \mathrm{DISRUPT} = C_F, \qquad \mathrm{HARM} = H_K, \qquad H_F = 0.\]
Proposition~1 is stated in Paper~1's symbols \(C_{OP}, \mathrm{DISRUPT}, \mathrm{HARM}\).
```

`\StmtDefDecisionProblem` (Paper 1):

```latex
\textbf{Definition D9 (Prior, policies, Bayes risk, oracle risk, cost of ambiguity).} The cause is drawn as \(M = K\) with prior probability \(p = P(K)\) and \(M = F\) with probability \(1-p\); given \(M\), the observation trajectory \(Y_W\) has law \(P_M^W\). A policy is a measurable map \(\pi\) from observation trajectories on \(W\) to \([0,1]\), read as the probability of the action \emph{contain} (randomized policies allowed; a deterministic policy takes values in \(\{0,1\}\)). Its expected cost is
\[\begin{aligned} R(\pi) = {}& p\,\mathbb{E}_K\big[\pi(Y_W)\,C_K + (1-\pi(Y_W))\,H_K\big] \\ &+ (1-p)\,\mathbb{E}_F\big[\pi(Y_W)\,C_F + (1-\pi(Y_W))\,H_F\big]. \end{aligned}\]
The best achievable expected cost is \(R^\star = \inf_\pi R(\pi)\); the oracle, which observes \(M\), has expected cost \(R_{\text{oracle}} = p \min\{C_K, H_K\} + (1-p)\min\{C_F, H_F\}\); the cost of ambiguity is \(\mathrm{CoA}^\star = R^\star - R_{\text{oracle}}\). Where the observation is the raw trajectory \(Y\) the subscript \(Y\) is written (\(R_Y^\star\), \(\mathrm{CoA}_Y^\star\)).
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
- \((\ast)\) (Paper 1) denotes the condition \(\theta_K\, C b_K = \theta_F\, C b_F\), numbered \((\ast)\) in Paper 1's Theorem 1 (reproduced below).
- The statement's title is the macro `\StmtPropositionOneTitle`, reproduced below.
- The statement is in Paper 1's loss-table symbols \(C_{OP}, \mathrm{DISRUPT}, \mathrm{HARM}\) (Definition D8). The policies "mapping \(\{y_t\}\) to \(\{\text{contain}, \text{leave alone}\}\)" are those of Definition D9 on the observation window of Theorem 1, \(W = \{t : t \ge 0\}\).
```

### Statements referred to

The statement refers to the statements below. They are reproduced verbatim so that every reference resolves; they are not the statement under verification.

`\StmtPropositionOneTitle` (Paper 1):

```latex
\textbf{Proposition 1 (Cost of ambiguity is bounded below under confounding --- corrected).}
```

`\StmtTheoremOne` (Paper 1):

```latex
\textbf{Theorem 1 (Indistinguishability criterion).} Under the model of Section 3, with common onset time \(\tau\), mechanism instances \((K, \theta_K, b_K)\) and \((F, \theta_F, b_F)\) induce identical distributions over the observation trajectory \(\{y_t\}_{t\ge 0}\) if and only if

\[\theta_K\, C b_K = \theta_F\, C b_F. \tag{$\ast$}\]
```
