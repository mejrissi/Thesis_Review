# Verification packet: Paper 4, Proposition R5 (`\StmtPropVerificationMargin`)

Source: `papers/paper4/research/statements.tex` at `33801b4`, copied verbatim; the short reference macros (`\RefFour...`) are expanded to their text. All mathematics is LaTeX. The Paper 1 and Paper 2 items are copied verbatim from `papers/paper1/research/statements.tex` and `papers/paper2/research/statements.tex` at the same commit, with their short reference macros (`\RefDef...`, `\RefAssm...`) expanded; "this paper" in a Paper 1 item means Paper 1. Paper 4's statements file has no `\Stmt...Uses` macros: the definitions and assumptions below are those the statement names or whose symbols it uses.

## Statement

`\StmtPropVerificationMargin` (Paper 4):

```latex
\textbf{Proposition R5 (Verification margin).} Assume (G-A1) and (G-A6), with \(s_v, t_v \in [0,1]\). Let \(\pi = \pi^{\mathrm{ver}}_{\bar x}\) with thresholds \(q_1 \le q_2\) (Paper~2's, or any others), \(\alpha = \alpha_\pi\) and \(m_F\) the fault verification mass (Definition~G6). For every \(\varepsilon \in [0,1]\) and every \(x_K\) with \(\mathrm{TV}(P^W_{x_K}, P^W_{x_F}) \le \varepsilon\) (in particular every \(x_K \in \mathcal{E}_W(\varepsilon)\)), with \(\Delta = x_K - x_F\):
(a) \((s_v + t_v - 1)\,m_F - \varepsilon \;\le\; \beta_\pi(x_K) - \alpha \;\le\; (s_v + t_v - 1)\,m_F + \varepsilon\);
(b) \(1 - \alpha - (s_v + t_v - 1)\,m_F + \varepsilon \ge 0\) and \(U_A(\pi, x_K) \le h(\Delta)^+\,\big(1 - \alpha - (s_v + t_v - 1)\,m_F + \varepsilon\big)\), where \(h^+ = \max\{h, 0\}\); in particular, if \(h(\Delta) \ge 0\), \(U_A(\pi, x_K) \le h(\Delta)\big(1 - \alpha - (s_v + t_v - 1)\,m_F + \varepsilon\big)\).
Under (G-A5) (\(s_v + t_v > 1\)), the margin \((s_v + t_v - 1)\,m_F\) is positive iff \(m_F > 0\); if the verification region is empty (\(q_1 = q_2\)), \(m_F = 0\) and (a) reduces to Proposition~R1(b).
```

## Definitions

`\StmtDefGame` (Paper 4):

```latex
\textbf{Definition G1 (Players, timing, game form).} There are two players, the \emph{operator} (leader) and the \emph{attacker} (follower), and a move of nature. (1) The operator commits to a rule \(\pi\) from a class \(\Pi\) (Definition~G5) and to an observation window \(W\). (2) The attacker observes \(\pi\) and \(W\) and chooses an injection vector \(x_K\) from its admissible set (Definition~G3). (3) Nature draws the cause \(M = K\) with probability \(p \in (0,1)\) and \(M = F\) otherwise; under \(F\) the fault instance \(x_F\) is fixed ((G-A4)), under \(K\) the injection is \(x_K\). (4) The operator observes \(Y_W\) (and, under a rule with verification, the verification outcome \(Z\)) and applies \(\pi\). The attacker's choice is a pure strategy; the operator's rule may be randomized (values in \([0,1]\)). The operator does not revise \(\pi\) after observing \(Y_W\) beyond what \(\pi\) itself prescribes (commitment).
```

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

`\StmtDefRules` (Paper 4):

```latex
\textbf{Definition G5 (Operator rules).} Write the operator's loss table as \(L(\text{contain}, K) = C_K\), \(L(\text{contain}, F) = C_F\), \(L(\text{leave}, K) = H_K\), \(L(\text{leave}, F) = H_F\) (Paper~1, Definition~D8), and put \(a = H_K - C_K\) and \(b = C_F - H_F\) (both positive under (G-A5)). A rule with verification uses a check on a separate channel ((G-A6)) with outcome \(Z \in \{+,-\}\), \emph{sensitivity} \(s_v = P(Z = + \mid K)\), \emph{specificity} \(t_v = P(Z = - \mid F)\), cost \(c_v\), delay \(\tau_v\), and harm rate \(r_K\) of a true compromise during the delay (Paper~2, Definition~2). A \emph{rule} on \(W\) is a measurable map \(\pi\) from observations to the probability of containing (Paper~1, Definition~D9), possibly after a verification step. The classes used are:
(i) \emph{Committed threshold rule} \(\pi^{\mathrm{thr}}_{\bar x}\). The operator fixes a \emph{nominal compromise model} \(\bar x \ne x_F\) (the compromise instance it plans against) and contains iff the nominal posterior
\(\bar q(Y_W) = p\,f^W_{\bar x}(Y_W) / \big(p\,f^W_{\bar x}(Y_W) + (1-p)\,f^W_{x_F}(Y_W)\big)\)
satisfies \(\bar q(Y_W) \ge q^\ast = b/(a+b)\) (Paper~2, Lemma~1).
(ii) \emph{Committed two-threshold rule with verification} \(\pi^{\mathrm{ver}}_{\bar x}\). With the same \(\bar q\) and thresholds \(q_1 \le q_2\): leave if \(\bar q \le q_1\); if \(q_1 < \bar q < q_2\), verify, then contain on \(Z = +\) and leave on \(Z = -\); contain if \(\bar q \ge q_2\). Paper~2's thresholds (Paper~2, Theorem~1) are, when its verification region is non-empty,
\[
q_1 = \frac{c_v + (1-t_v)\,b}{s_v\,a + (1-t_v)\,b - r_K\tau_v},
\]
\[
q_2 = \frac{t_v\,b - c_v}{t_v\,b + (1-s_v)\,a + r_K\tau_v},
\]
and \(q_1 = q_2 = q^\ast\) otherwise; the results below use only \(q_1 \le q_2\).
(iii) \emph{General rule}: any \(\pi\) (for the operator's optimal commitment); rules with verification are written as the quadruple \((\delta, \pi_0, \pi_+, \pi_-)\) of the verify probability \(\delta\), the containment probability \(\pi_0\) without verification and the containment probabilities \(\pi_\pm\) after \(Z = \pm\), each a measurable map from observations to \([0,1]\), as in Paper~2, Definition~4.
```

`\StmtDefDetection` (Paper 4):

```latex
\textbf{Definition G6 (Detection, false alarm, verification mass).} For a rule \(\pi\) let \(\phi_\pi^M(y) \in [0,1]\) be the probability of containing given \(Y_W = y\) and cause \(M\) (for a rule without verification \(\phi^K_\pi = \phi^F_\pi = \pi\); for \(\pi^{\mathrm{ver}}_{\bar x}\), \(\phi^K = \mathbb{1}[\bar q \ge q_2] + s_v\,\mathbb{1}[q_1 < \bar q < q_2]\) and \(\phi^F = \mathbb{1}[\bar q \ge q_2] + (1-t_v)\,\mathbb{1}[q_1 < \bar q < q_2]\)). The \emph{detection probability} of strategy \(x_K\) is \(\beta_\pi(x_K) = \mathbb{E}_{x_K}[\phi^K_\pi(Y_W)]\), the \emph{false-alarm probability} is \(\alpha_\pi = \mathbb{E}_{x_F}[\phi^F_\pi(Y_W)]\), and for a rule with verification the \emph{fault verification mass} is \(m_F = P_{x_F}(q_1 < \bar q(Y_W) < q_2)\) (Paper~2's verification mass, Definition~5, evaluated on the fault law).
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

`\StmtDefLossTable` (Paper 1):

```latex
\textbf{Definition D8 (Loss table).} The general two-action, two-cause loss table \(L(a, M)\), \(a \in \{\text{contain}, \text{leave alone}\}\), \(M \in \{K,F\}\), is
\[\begin{gathered} L(\text{contain}, K) = C_K, \qquad L(\text{contain}, F) = C_F, \\ L(\text{leave alone}, K) = H_K, \qquad L(\text{leave alone}, F) = H_F, \end{gathered}\]
with \(C_K, C_F, H_K, H_F \in \mathbb{R}\). This paper's table (Section~3) is the special case
\[C_{OP} = C_K, \qquad \mathrm{DISRUPT} = C_F, \qquad \mathrm{HARM} = H_K, \qquad H_F = 0.\]
Propositions~1 and~2 are stated in this paper's symbols \(C_{OP}, \mathrm{DISRUPT}, \mathrm{HARM}\).
```

`\StmtDefDecisionProblem` (Paper 1):

```latex
\textbf{Definition D9 (Prior, policies, Bayes risk, oracle risk, cost of ambiguity).} The cause is drawn as \(M = K\) with prior probability \(p = P(K)\) and \(M = F\) with probability \(1-p\); given \(M\), the observation trajectory \(Y_W\) has law \(P_M^W\). A policy is a measurable map \(\pi\) from observation trajectories on \(W\) to \([0,1]\), read as the probability of the action \emph{contain} (randomized policies allowed; a deterministic policy takes values in \(\{0,1\}\)). Its expected cost is
\[\begin{aligned} R(\pi) = {}& p\,\mathbb{E}_K\big[\pi(Y_W)\,C_K + (1-\pi(Y_W))\,H_K\big] \\ &+ (1-p)\,\mathbb{E}_F\big[\pi(Y_W)\,C_F + (1-\pi(Y_W))\,H_F\big]. \end{aligned}\]
The best achievable expected cost is \(R^\star = \inf_\pi R(\pi)\); the oracle, which observes \(M\), has expected cost \(R_{\text{oracle}} = p \min\{C_K, H_K\} + (1-p)\min\{C_F, H_F\}\); the cost of ambiguity is \(\mathrm{CoA}^\star = R^\star - R_{\text{oracle}}\). Where the observation is the raw trajectory \(Y\) the subscript \(Y\) is written (\(R_Y^\star\), \(\mathrm{CoA}_Y^\star\)).
```

`\StmtDefPassiveRisk` (Paper 2):

```latex
\textbf{Definition 1 (Loss table, passive risk).} There are two causes, compromise \(K\) (the orders are submitted through a valid credential or session by someone the holder of that credential or session did not authorize: a stolen credential, a hijacked session) and fault \(F\) (the orders are the holder's own, distorted by a benign malfunction), and two terminal actions, \emph{contain} and \emph{leave}. Containing costs \(C_K\) under \(K\) and \(C_F\) under \(F\); leaving costs \(H_K\) under \(K\) and \(H_F\) under \(F\). For a belief \(q = P(K) \in [0,1]\) the \emph{passive risk} is
\[
R(q) \;=\; \min\{\, q\,C_K + (1-q)\,C_F,\;\; q\,H_K + (1-q)\,H_F \,\}.
\]
Write \(a = H_K - C_K\) and \(b = C_F - H_F\).
```

`\StmtDefVerification` (Paper 2):

```latex
\textbf{Definition 2 (Verification action).} Verification returns an outcome \(Z \in \{+,-\}\) with sensitivity \(s = P(Z = + \mid K)\) and specificity \(t = P(Z = - \mid F)\). It costs \(c_v\) and takes a delay \(\tau\); during the delay a true compromise causes harm at rate \(r_K\). From belief \(q\),
\[
P(+) = q s + (1-q)(1-t), \qquad P(-) = q(1-s) + (1-q)t,
\]
\[
q^+ = \frac{q s}{P(+)}, \qquad q^- = \frac{q(1-s)}{P(-)}
\]
(a posterior whose outcome has probability zero is never used; see Definition 3).
```

`\StmtDefVerifyFirst` (Paper 2):

```latex
\textbf{Definition 3 (Verify-first risk, value of information, verification region).} The \emph{verify-first risk} is
\[
R_v(q) \;=\; c_v + q\,r_K\,\tau + P(+)\,R(q^+) + P(-)\,R(q^-),
\]
where \(P(z)\,R(q^z)\) is read as \(\min\{\, P(z,K)\,C_K + P(z,F)\,C_F,\; P(z,K)\,H_K + P(z,F)\,H_F \,\}\) with \(P(z,K)=P(z\mid K)\,q\) and \(P(z,F)=P(z\mid F)\,(1-q)\) (equal to the product when \(P(z)>0\), and zero when \(P(z)=0\)). The \emph{value of information} is \(V(q) = R(q) - [P(+)R(q^+) + P(-)R(q^-)]\), the \emph{verification cost} is \(\chi(q) = c_v + q\,r_K\,\tau\), and the \emph{verification region} is
\[
S \;=\; \{\, q \in [0,1] : R_v(q) < R(q) \,\} \;=\; \{\, q \in [0,1] : V(q) > \chi(q) \,\}.
\]
Ties are resolved in favour of the passive action: the operator verifies only when verifying is strictly cheaper.
```

`\StmtDefVerifyFirstPolicy` (Paper 2):

```latex
\textbf{Definition 4 (Decision problem with verification; verify-first cost of ambiguity).} The cause \(M\) is \(K\) with prior probability \(p = P(K) \in (0,1)\) and \(F\) otherwise. Given \(M\), the order-flow observation \(Y\) has law \(P^Y_M\), and the verification outcome \(Z\) has the law of Definition~2, jointly as in Assumption~2. Write \(L(\text{contain},K) = C_K\), \(L(\text{contain},F) = C_F\), \(L(\text{leave},K) = H_K\), \(L(\text{leave},F) = H_F\) (Definition~1). A \emph{verify-first policy} is a quadruple of measurable maps \(\delta, \pi_0, \pi_+, \pi_-\) from observations \(y\) to \([0,1]\): with probability \(\delta(y)\) the operator verifies and then contains with probability \(\pi_Z(y)\); otherwise it contains with probability \(\pi_0(y)\). Its expected cost is
\[
\begin{aligned}
J(\delta,\pi) = \mathbb{E}\Big[ &(1-\delta(Y))\big(\pi_0(Y)\,L(\text{contain},M) \\
&\qquad + (1-\pi_0(Y))\,L(\text{leave},M)\big) \\
&+ \delta(Y)\big(c_v + \mathbb{1}[M=K]\,r_K\tau + \pi_Z(Y)\,L(\text{contain},M) \\
&\qquad + (1-\pi_Z(Y))\,L(\text{leave},M)\big)\Big] .
\end{aligned}
\]
A \emph{passive policy} is a verify-first policy with \(\delta \equiv 0\). Let \(R^\star_Y\) and \(R^\star_{Y,v}\) be the infima of \(J\) over passive and over verify-first policies, \(R_{\text{oracle}} = p\min\{C_K,H_K\} + (1-p)\min\{C_F,H_F\}\) the expected cost of an operator who observes \(M\), and
\[
\mathrm{CoA}^\star = R^\star_Y - R_{\text{oracle}}, \qquad \mathrm{CoA}^\star_v = R^\star_{Y,v} - R_{\text{oracle}}
\]
the passive and the verify-first cost of ambiguity.
```

`\StmtDefCellQuantities` (Paper 2):

```latex
\textbf{Definition 5 (Verification mass, saving and recovered share of a cell).} An \emph{order-flow model} \(c\) is a pair of order-flow laws \(P^c_K, P^c_F\) on a measurable space, with densities \(f^c_K, f^c_F\) with respect to a \(\sigma\)-finite measure \(\nu\) dominating both (e.g.\ \(\nu = P^c_K + P^c_F\)). A \emph{cell} \((c, p)\) is an order-flow model \(c\) together with a prior \(p \in (0,1)\); in Paper~1's grid, \(c\) is a market design in one regime and \(p\) is a prior of the grid. In the setting of Definition~4 with \(P^Y_K = P^c_K\), \(P^Y_F = P^c_F\) and prior \(p \in (0,1)\), write \(P_p = p\,P^c_K + (1-p)\,P^c_F\) for the law of \(Y\) and
\[
q_p(y) \;=\; \frac{p\,f^c_K(y)}{p\,f^c_K(y) + (1-p)\,f^c_F(y)}
\]
for the passive posterior (defined where the denominator is positive, a set of full \(P_p\)-measure). The \emph{verification mass}, the \emph{saving} and the \emph{recovered share} of the cell \((c, p)\) are
\[
m_c(p) = P_p\bigl(q_p(Y) \in S\bigr), \qquad
D_c(p) = \mathbb{E}_p\bigl[(V - \chi)^+\bigl(q_p(Y)\bigr)\bigr],
\]
\[
\rho_c(p) = \frac{D_c(p)}{\mathrm{CoA}^\star_c(p)} ,
\]
with \(S\), \(V\), \(\chi\) as in Definition~3 and \(\mathrm{CoA}^\star_c(p)\) the passive cost of ambiguity of Definition~4 for this cell; \(\rho_c(p)\) is defined when \(\mathrm{CoA}^\star_c(p) > 0\). Where \(f^c_K, f^c_F > 0\), \(\operatorname{logit} q_p(y) = \operatorname{logit} p + \Lambda_c(y)\) with \(\Lambda_c = \log(f^c_K / f^c_F)\).
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

`\StmtAssmChannel` (Paper 4):

```latex
\textbf{(G-A6) Verification is not manipulable by order flow.} Paper~2's separate-channel assumption (Assumption~2) holds for every attacker strategy: verification reads authorization, not order flow, through a channel the party submitting the orders does not control; given the cause, \(Z\) is independent of \(Y_W\), \(P(Z, Y_W \mid M) = P(Z \mid M)\,P(Y_W \mid M)\) for \(M \in \{K, F\}\); and \((s_v, t_v)\) depend neither on \(Y_W\) nor on \(x_K\). (An attacker who also attacks the authorization channel, for instance with stolen credentials, violates this assumption; that case is out of scope.)
```

`\StmtAssmCosts` (Paper 4):

```latex
\textbf{(G-A5) Costs and verification.} (1) \emph{Cost orderings} (Paper~2, Assumption~1): \(a = H_K - C_K > 0\) and \(b = C_F - H_F > 0\): leaving a compromise is strictly worse than containing it, and containing a fault is strictly worse than leaving it. For rules with verification, in addition:
(2) \emph{Informative one-shot verification} (Paper~2, Assumption~3): \(s_v, t_v \in [0,1]\) with \(s_v + t_v > 1\); \(c_v \ge 0\), \(\tau_v \ge 0\), \(r_K \ge 0\); verification is available once, and after its outcome the operator takes a terminal action (contain or leave).
(3) \emph{Delay accounting} (Paper~2, Assumption~4): the harm \(r_K\tau_v\) accrued by a true compromise during the verification delay is additional to the terminal cost, whichever terminal action is taken; the terminal costs and \((s_v, t_v)\) do not depend on \(\tau_v\); a fault accrues no additional cost during the delay; and no further order-flow evidence is used between the start of verification and the terminal action.
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
- Paper 4 writes Paper 2's sensitivity \(s\), specificity \(t\) and delay \(\tau\) as \(s_v\), \(t_v\), \(\tau_v\) (in Paper 4, \(t\) is a time index and \(\tau\) the onset). \(a = H_K - C_K\), \(b = C_F - H_F\) (Definition G5); \(r_K\) is the harm rate of a true compromise during the verification delay (Paper 2, Definition 2); \(H_K, H_F\) are the costs of leaving.
- \(p \in (0,1)\) is the prior probability of compromise (Definition G1). \(q^\ast = b/(a+b)\).
- In Paper 2's items, \(q_L = \frac{(1-t)\,b}{s\,a + (1-t)\,b}\) and \(q_U = \frac{t\,b}{t\,b + (1-s)\,a}\) (Paper 2's Lemma 3); \(R\), \(V\), \(\chi\), \(S\) are those of Paper 2's Definitions 1 and 3; \(\mathrm{CoA}^\star\) is that of Paper 2's Definition 4. "Paper~1's grid" in Paper 2's Definition 5 is an example and plays no role here.
- Paper 2's Assumptions 1--4, its Lemma 1 and its Theorem 1 are reproduced under "Statements referred to" because Definition G5 names them; they are not hypotheses of the statement.
- \(h^+ = \max\{h, 0\}\).
- (G-A5) is a hypothesis only of the last sentence ("Under (G-A5) ..."); (G-A3) is not a hypothesis of this statement.
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

`\StmtAssumptionCosts` (Paper 2):

```latex
\textbf{Assumption 1 (Cost orderings).} \(H_K > C_K\) and \(C_F > H_F\); that is, \(a > 0\) and \(b > 0\): leaving a compromise is strictly worse than containing it, and containing a fault is strictly worse than leaving it.
```

`\StmtAssumptionSeparateChannel` (Paper 2):

```latex
\textbf{Assumption 2 (Separate channel).} Verification reads authorization, not order flow: it asks whether the holder of the credential or session authorized the orders, through a channel the person submitting them does not control (for example an out-of-band confirmation with the account holder, or a step-up authentication with a factor bound to the holder). A check of whether the credential or session is valid is not such a check, since a stolen credential or a hijacked session is valid under \(K\). Its outcome \(Z\) is conditionally independent of the order-flow observation \(Y\) given the cause: \(P(Z, Y \mid c) = P(Z \mid c)\,P(Y \mid c)\) for \(c \in \{K, F\}\), and \((s,t)\) do not depend on \(Y\).
```

`\StmtAssumptionVerification` (Paper 2):

```latex
\textbf{Assumption 3 (Informative one-shot verification).} \(s, t \in [0,1]\) with \(s + t > 1\); \(c_v \ge 0\), \(\tau \ge 0\), \(r_K \ge 0\). Verification is available once; after its outcome the operator takes a terminal action (contain or leave) and cannot verify again.
```

`\StmtAssumptionDelay` (Paper 2):

```latex
\textbf{Assumption 4 (Delay accounting).} The harm \(r_K\tau\) accrued by a true compromise during the verification delay is \emph{additional} to the terminal cost (\(C_K\) or \(H_K\)) incurred afterwards, whichever terminal action is taken; the terminal costs \(C_K, C_F, H_K, H_F\) and the verification characteristics \(s, t\) do not depend on \(\tau\); a fault accrues no additional cost during the delay (its damage rate is \(r_F = 0\)); and no further order-flow evidence is used between the start of verification and the terminal action.
```

`\StmtLemmaPassiveThreshold` (Paper 2):

```latex
\textbf{Lemma 1 (Passive threshold).} Under Assumption 1, let \(q^\ast = b/(a+b) \in (0,1)\). Leaving is strictly optimal for \(q < q^\ast\), containing is strictly optimal for \(q > q^\ast\), and
\[
R(q) \;=\; q\,H_K + (1-q)\,H_F \;-\; (a+b)\,(q - q^\ast)^+ ,
\]
so \(R\) is continuous, concave and piecewise linear on \([0,1]\) with a single kink at \(q^\ast\).
```

`\StmtTheoremTwoThreshold` (Paper 2):

```latex
\textbf{Theorem 1 (Two-threshold leave / verify / contain rule).} Under Assumptions 1, 3 and 4, the verification region \(S\) is an open interval (possibly empty). It is non-empty if and only if
\[
V(q^\ast) \;>\; c_v + q^\ast r_K \tau ,
\]
and then \(S = (q_1, q_2)\) with \(q_L \le q_1 < q^\ast < q_2 \le q_U\), where
\[
q_1 = \frac{c_v + (1-t)\,b}{s\,a + (1-t)\,b - r_K\tau}, \qquad
q_2 = \frac{t\,b - c_v}{t\,b + (1-s)\,a + r_K\tau}
\]
(both denominators are positive when \(S \neq \emptyset\)). The optimal one-shot policy is: \emph{leave} if \(q \le q_1\), \emph{verify} if \(q_1 < q < q_2\) and then contain on \(Z = +\) and leave on \(Z = -\), \emph{contain} if \(q \ge q_2\) (with \(q_1 = q_2 = q^\ast\) and the passive rule of Lemma 1 when \(S = \emptyset\)). When \(c_v = 0\) and \(\tau r_K = 0\), \(S = (q_L, q_U)\).
```

`\StmtPropTVCap` (Paper 4):

```latex
\textbf{Proposition R1 (Total-variation detection cap).} Assume (G-A1). Let \(\varepsilon \in [0,1]\) and let \(x_K \in \mathbb{R}^n\) satisfy \(\mathrm{TV}(P^W_{x_K}, P^W_{x_F}) \le \varepsilon\) (in particular, any \(x_K \in \mathcal{E}_W(\varepsilon)\)).
(a) For every measurable \(\phi\) from observations on \(W\) to \([0,1]\), \(\big|\mathbb{E}_{x_K}[\phi(Y_W)] - \mathbb{E}_{x_F}[\phi(Y_W)]\big| \le \varepsilon\).
(b) For every rule \(\pi\) without verification, \(\alpha_\pi - \varepsilon \le \beta_\pi(x_K) \le \alpha_\pi + \varepsilon\).
(c) Assume in addition (G-A6). For every rule with verification, written as in Definition~G5(iii) as \((\delta, \pi_0, \pi_+, \pi_-)\), let \(\phi^K = (1-\delta)\pi_0 + \delta\,(s_v \pi_+ + (1-s_v)\pi_-)\) and \(\phi^F = (1-\delta)\pi_0 + \delta\,((1-t_v)\pi_+ + t_v \pi_-)\) (for \(\pi^{\mathrm{ver}}_{\bar x}\) these are the maps of Definition~G6). Then \(\beta_\pi(x_K) = \mathbb{E}_{x_K}[\phi^K(Y_W)]\), \(\alpha_\pi = \mathbb{E}_{x_F}[\phi^F(Y_W)]\), and
\(\mathbb{E}_{x_F}[\phi^K(Y_W)] - \varepsilon \le \beta_\pi(x_K) \le \mathbb{E}_{x_F}[\phi^K(Y_W)] + \varepsilon\).
(d) (Tightness.) For every \(x \in \mathbb{R}^n\), \(\sup_\pi \big(\beta_\pi(x) - \alpha_\pi\big) = \mathrm{TV}(P^W_x, P^W_{x_F})\), the supremum over rules without verification, attained by the rule that contains iff \(f^W_x(Y_W) > f^W_{x_F}(Y_W)\).
```
