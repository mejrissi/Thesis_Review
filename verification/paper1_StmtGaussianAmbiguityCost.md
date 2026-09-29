# Verification packet: Paper 1, Proposition (Gaussian unequal-prior ambiguity cost) (`\StmtGaussianAmbiguityCost`)

Source: `papers/paper1/research/statements.tex` at `919c38d`, copied verbatim; the short reference macros (`\RefDef...`, `\RefAssm...`) are expanded to their text. All mathematics is LaTeX.

## Statement

`\StmtGaussianAmbiguityCost` (Paper 1):

```latex
\textbf{Proposition (Gaussian unequal-prior ambiguity cost).} Let \(Y \mid M \sim \mathcal{N}(\mu_M, V)\), \(M \in \{K,F\}\), with common covariance \(V \succ 0\) and discriminability \(d > 0\) (Definition~D11), prior \(p = P(K)\), and the general loss table with \(a = p(H_K-C_K)\), \(b=(1-p)(C_F-H_F)\), \(a, b > 0\). Then the population-optimal ambiguity cost is
\[\mathrm{CoA}_Y^\star(d) = a\,\Phi\!\left(\frac{\log(b/a)}{d} - \frac{d}{2}\right) + b\,\Phi\!\left(\frac{\log(a/b)}{d} - \frac{d}{2}\right),\]
which tends to \(\min(a,b)\) as \(d \to 0^+\) (the value at \(d=0\), exact confounding, recovering Proposition~1, is obtained as this limit) and decreases toward \(0\) as \(d\to\infty\).
```

## Definitions

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

`\StmtDefTotalVariation` (Paper 1):

```latex
\textbf{Definition D10 (Observation densities; total variation).} Let \(\mu\) be a measure dominating \(P_K\) and \(P_F\) (e.g.\ \(P_K + P_F\)), and \(f_K, f_F\) their densities with respect to \(\mu\); \(\int \cdot\, dy\) denotes integration against \(\mu\). The total variation distance is
\[\mathrm{TV}(P,P') = \sup_{B} |P(B) - P'(B)| = \tfrac{1}{2}\int |f - f'|\, dy,\]
so that \(1 - \mathrm{TV}(P_K, P_F) = \int \min\{f_K, f_F\}\, dy\).
```

`\StmtDefDiscriminability` (Paper 1):

```latex
\textbf{Definition D11 (Gaussian discriminability).} If \(Y \mid M \sim \mathcal{N}(\mu_M, V)\), \(M \in \{K,F\}\), with a common covariance \(V \succ 0\), let \(\delta = \mu_K - \mu_F\) and \(d = \sqrt{\delta^\top V^{-1} \delta} \ge 0\) (the whitened mean separation).
```

## Assumptions

None beyond the hypotheses written in the statement and the definitions above.

## Notation

```latex
- \(\mathbb{1}[\cdot]\) is the indicator; \(\ker\) is the kernel (null space) of a matrix; \(\mathrm{span}\) is the linear span; \(\Phi\) is the standard normal distribution function; \(\mathcal{N}(\mu, V)\) is the Gaussian law with mean \(\mu\) and covariance \(V\).
- "The general loss table" is Definition D8 in its general symbols \(C_K, C_F, H_K, H_F\). \(\mathrm{CoA}_Y^\star\) is \(\mathrm{CoA}^\star\) of Definition D9 with the observation \(Y\).
- The observation \(Y\) is given directly by its conditional Gaussian laws; the statement uses none of the model assumptions (A1)--(A6) of Paper 1.
- "Recovering Proposition 1" refers to Paper 1's Proposition 1, reproduced below with the Theorem 1 it relies on.
- \((\ast)\) (Paper 1) denotes the condition \(\theta_K\, C b_K = \theta_F\, C b_F\), numbered \((\ast)\) in Paper 1's Theorem 1 (reproduced below).
- In Paper 1, "the model of Section 3" is Definition D1 (output-level injection model) and "the state-level injection model" is Definition D2.
```

### Statements referred to

The statement refers to the statements below. They are reproduced verbatim so that every reference resolves; they are not the statement under verification.

`\StmtPropositionOneTitle` (Paper 1):

```latex
\textbf{Proposition 1 (Cost of ambiguity is bounded below under confounding --- corrected).}
```

`\StmtPropositionOne` (Paper 1):

```latex
Suppose (\(\ast\)) holds (the confounded case), \(0 < p < 1\), \(\mathrm{DISRUPT} > 0\), and \(\mathrm{HARM} > C_{OP} \ge 0\) (harm strictly worse than routine containment --- the assumption the earlier version omitted). Then the best achievable expected cost among policies mapping \(\{y_t\}\) to \(\{\text{contain}, \text{leave alone}\}\) is

\[R^\star = \min\{\,p\,C_{OP} + (1-p)\,\mathrm{DISRUPT},\ \ p\,\mathrm{HARM}\,\},\]

the oracle's expected cost is \(R_{\text{oracle}} = p\,C_{OP}\), and

\[\boxed{\mathrm{CoA}^\star \;=\; R^\star - R_{\text{oracle}} \;=\; \min\{\,(1-p)\,\mathrm{DISRUPT},\ \ p\,(\mathrm{HARM} - C_{OP})\,\} \;>\; 0.}\]
```

`\StmtTheoremOne` (Paper 1):

```latex
\textbf{Theorem 1 (Indistinguishability criterion).} Under the model of Section 3, with common onset time \(\tau\), mechanism instances \((K, \theta_K, b_K)\) and \((F, \theta_F, b_F)\) induce identical distributions over the observation trajectory \(\{y_t\}_{t\ge 0}\) if and only if

\[\theta_K\, C b_K = \theta_F\, C b_F. \tag{$\ast$}\]
```
