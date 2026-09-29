# Verification packet: Paper 2, Corollary 2 (`\StmtCorollaryUniformCeiling`)

Source: `papers/paper2/research/statements.tex` at `317caec`, copied verbatim. All mathematics is LaTeX. The Paper 1 statements under "Statements referred to" are copied verbatim from `papers/paper1/research/statements.tex` at `317caec`, with its short reference macros (`\RefDef...`, `\RefAssm...`) expanded to their text; "this paper" in a Paper 1 statement means Paper 1.

## Statement

`\StmtCorollaryUniformCeiling` (Paper 2):

```latex
\textbf{Corollary 2 (Uniform ceiling: the confounded case is the worst case).} Under Assumptions 1--4, in the setting of Definition~4, let \(E(p)\) be as in Corollary~1. For every pair of order-flow laws \(P^Y_K, P^Y_F\) and every \(p \in (0,1)\):
(i) the \emph{verify-everything} policy (\(\delta \equiv 1\), \(\pi_+ \equiv 1\), \(\pi_- \equiv 0\)) has expected cost \(R_{\text{oracle}} + E(p)\), whatever the order-flow laws;
(ii) \(\mathrm{CoA}^\star \le \min\{\, p\,a,\; (1-p)\,b \,\}\) and
\[
\mathrm{CoA}^\star_v \;\le\; \min\{\, \mathrm{CoA}^\star,\; E(p) \,\} \;\le\; \min\{\, p\,a,\; (1-p)\,b,\; E(p) \,\};
\]
(iii) every inequality in (ii) is an equality in the confounded case \(P^Y_K = P^Y_F\) (Corollary~1), so that, over all pairs of order-flow laws, the largest passive cost of ambiguity is \(\min\{p\,a, (1-p)\,b\}\) and the largest verify-first cost of ambiguity is \(\min\{p\,a, (1-p)\,b, E(p)\}\), both attained in the confounded case;
(iv) the largest verify-first cost of ambiguity is strictly below the largest passive one if and only if \(p \in S\), and the gap is \((V(p) - \kappa(p))^+\).
Under the correspondence of Paper~1, Definition~D8 (\(H_F = 0\)), and the hypotheses of Paper~1, Proposition~1, \(\min\{p\,a, (1-p)\,b\}\) is the cost of ambiguity of Paper~1, Proposition~1, and the passive bound in (ii) is the upper bound of Paper~1's total-variation extension of that proposition: the value of Paper~1's Proposition~1 is the worst case of the passive cost of ambiguity over all order-flow models, and verification caps the cost of ambiguity at \(E(p)\) for every order-flow model.
```

## Definitions

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
where \(P(z)\,R(q^z)\) is read as \(\min\{\, P(z,K)\,C_K + P(z,F)\,C_F,\; P(z,K)\,H_K + P(z,F)\,H_F \,\}\) with \(P(z,K)=P(z\mid K)\,q\) and \(P(z,F)=P(z\mid F)\,(1-q)\) (equal to the product when \(P(z)>0\), and zero when \(P(z)=0\)). The \emph{value of information} is \(V(q) = R(q) - [P(+)R(q^+) + P(-)R(q^-)]\), the \emph{verification cost} is \(\kappa(q) = c_v + q\,r_K\,\tau\), and the \emph{verification region} is
\[
S \;=\; \{\, q \in [0,1] : R_v(q) < R(q) \,\} \;=\; \{\, q \in [0,1] : V(q) > \kappa(q) \,\}.
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

## Assumptions

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

## Notation

Shared notation, verbatim from the header of Paper 2's statements file:

```latex
% Notation shared by all statements:
%   q in [0,1]   belief that the cause is compromise K (the alternative is fault F);
%   a := H_K - C_K  (net benefit of containing a compromise),
%   b := C_F - H_F  (net cost of containing a fault).
%   r_K >= 0     damage rate: harm per unit time caused by a true compromise during the verification delay
%                (renamed from h_K, decision 0026, issue #134; r_F is the rate of a fault, zero under Assumption 4 and >= 0 in Corollary 4).
%                H_K, H_F stay the costs of leaving.
```

```latex
- \(x^+ = \max\{x, 0\}\); \(\mathbb{1}[\cdot]\) is the indicator; \(\Phi\) is the standard normal distribution function; \(\operatorname{logit} q = \log(q/(1-q))\).
- \(q^\ast = b/(a+b)\) (Paper 2): defined in Paper 2's Lemma 1 ("let \(q^\ast = b/(a+b)\)").
- \(q_L\), \(q_U\) (Paper 2): defined in Paper 2's Lemma 3 as \(q_L = \frac{(1-t)\,b}{s\,a + (1-t)\,b}\), \(q_U = \frac{t\,b}{t\,b + (1-s)\,a}\).
- \(E(p)\) is that of Paper 2's Corollary 1, reproduced below with the Theorems 1 and 2 and the Lemma 1 it refers to; \(S\), \(V\), \(\kappa\) are those of Definition 3, and \((V(p) - \kappa(p))^+ = \max\{V(p) - \kappa(p), 0\}\).
- The last sentence refers to Paper 1 of the same thesis. Paper 1's Definition D8 (with its Definitions D4 and D9), its Proposition 1, its Proposition 2, the total-variation extension of Proposition 1 (with its Definition D10), and the Theorem 1, Definition D1 and Definition D3 that Proposition 1 relies on are reproduced below. In Paper 1, \((\ast)\) denotes \(\theta_K\, C b_K = \theta_F\, C b_F\) and "the model of Section 3" is Paper 1's Definition D1. In Paper 1's Proposition 2 (the total-variation extension), \(a\) and \(b\) denote \(p(\mathrm{HARM}-C_{OP})\) and \((1-p)\,\mathrm{DISRUPT}\), not Paper 2's \(a\) and \(b\), and \(P_K, P_F\) are Paper 1's observation laws.
```

### Statements referred to

The statement refers to the statements below. They are reproduced verbatim so that every reference resolves; they are not the statement under verification.

`\StmtCorollaryConfoundedCoA` (Paper 2):

```latex
\textbf{Corollary 1 (Verification lowers the confounded cost of ambiguity).} Under Assumptions 1--4, in the setting of Definition~4, suppose the order-flow laws coincide, \(P^Y_K = P^Y_F\) (the confounded case). Then:
(i) \(\mathrm{CoA}^\star = \min\{\, p\,a,\; (1-p)\,b \,\} > 0\);
(ii) the verify-first cost of ambiguity is
\[
\mathrm{CoA}^\star_v \;=\; \min\{\, \mathrm{CoA}^\star,\; E(p) \,\},
\]
\[
E(p) \;=\; c_v + p\,r_K\tau + p\,(1-s)\,a + (1-p)\,(1-t)\,b ,
\]
equivalently \(\mathrm{CoA}^\star_v = \mathrm{CoA}^\star - (V(p) - \kappa(p))^+\), and it is attained by the policy of Theorem~1 applied at the belief \(q = p\), whatever \(Y\);
(iii) \(\mathrm{CoA}^\star_v < \mathrm{CoA}^\star\) if and only if \(p \in S\), that is, if and only if \(V(q^\ast) > c_v + q^\ast r_K\tau\) and \(q_1 < p < q_2\) (Theorem~1); if \(r_K > 0\) and \(V(q^\ast) > c_v\), this holds if and only if \(\tau < \tau^\ast\) and \(q_1(\tau) < p < q_2(\tau)\) (Theorem~2), and if \(V(q^\ast) \le c_v\) it holds for no \(p\) and no \(\tau\);
(iv) over \(p \in (0,1)\), the reduction \(\mathrm{CoA}^\star - \mathrm{CoA}^\star_v\) is largest at \(p = q^\ast\), where it equals \((V(q^\ast) - c_v - q^\ast r_K\tau)^+\);
(v) \(\mathrm{CoA}^\star_v = 0\) if and only if \(s = t = 1\), \(c_v = 0\) and \(r_K\tau = 0\).
Under the correspondence of Paper~1, Definition~D8 (\(H_F = 0\)), \(\mathrm{CoA}^\star\) in (i) is the cost of ambiguity of Paper~1, Proposition~1, so (iii) states when verification brings the cost of ambiguity strictly below that value.
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

`\StmtTheoremCriticalDelay` (Paper 2):

```latex
\textbf{Theorem 2 (Critical delay).} Under Assumptions 1, 3 and 4, write \(S(\tau)\) for the verification region at delay \(\tau\), all other parameters fixed.
(i) \emph{Nesting.} \(\tau < \tau'\) implies \(S(\tau') \subseteq S(\tau)\). If \(r_K > 0\) and \(V(q^\ast) > c_v\), then \(S(\tau) \neq \emptyset\) exactly for \(\tau \in [0, \tau^\ast)\) (part (ii)), and on \([0, \tau^\ast)\) the end point \(q_2(\tau)\) of Theorem~1 is strictly decreasing in \(\tau\), and \(q_1(\tau)\) is strictly increasing in \(\tau\) unless \(c_v = 0\) and \(t = 1\), in which case \(q_1(\tau) = 0\) on \([0, \tau^\ast)\). For \(\tau \ge \tau^\ast\), \(S(\tau) = \emptyset\) and the convention \(q_1 = q_2 = q^\ast\) of Theorem~1 applies.
(ii) \emph{Critical delay.} If \(r_K > 0\) and \(V(q^\ast) > c_v\), let
\[
\tau^\ast \;=\; \frac{V(q^\ast) - c_v}{q^\ast\, r_K} \;=\; \frac{(s+t-1)\,a - c_v/q^\ast}{r_K} \;>\; 0 .
\]
Then \(S(\tau) \neq \emptyset\) if and only if \(\tau < \tau^\ast\).
(iii) \emph{Degenerate cases.} If \(V(q^\ast) \le c_v\), then \(S(\tau) = \emptyset\) for every \(\tau \ge 0\). If \(r_K = 0\), \(S(\tau)\) does not depend on \(\tau\).
(iv) \emph{How the interval vanishes.} Suppose \(r_K > 0\) and \(V(q^\ast) > c_v\) (the hypotheses of (ii)). If \(c_v > 0\) or \(t < 1\), then \(q_1 \to q^\ast\) and \(q_2 \to q^\ast\) as \(\tau \uparrow \tau^\ast\): the interval shrinks continuously to the point \(q^\ast\). If \(c_v = 0\) and \(t = 1\), then \(S(\tau) = (0, q_2(\tau))\) for \(\tau < \tau^\ast\) with \(q_2(\tau) \downarrow q^\ast\), and \(S(\tau^\ast) = \emptyset\): the interval vanishes discontinuously.
```

`\StmtLemmaPassiveThreshold` (Paper 2):

```latex
\textbf{Lemma 1 (Passive threshold).} Under Assumption 1, let \(q^\ast = b/(a+b) \in (0,1)\). Leaving is strictly optimal for \(q < q^\ast\), containing is strictly optimal for \(q > q^\ast\), and
\[
R(q) \;=\; q\,H_K + (1-q)\,H_F \;-\; (a+b)\,(q - q^\ast)^+ ,
\]
so \(R\) is continuous, concave and piecewise linear on \([0,1]\) with a single kink at \(q^\ast\).
```

`\StmtDefLossTable` (Paper 1):

```latex
\textbf{Definition D8 (Loss table).} The general two-action, two-cause loss table \(L(a, M)\), \(a \in \{\text{contain}, \text{leave alone}\}\), \(M \in \{K,F\}\), is
\[\begin{gathered} L(\text{contain}, K) = C_K, \qquad L(\text{contain}, F) = C_F, \\ L(\text{leave alone}, K) = H_K, \qquad L(\text{leave alone}, F) = H_F, \end{gathered}\]
with \(C_K, C_F, H_K, H_F \in \mathbb{R}\). This paper's table (Section~3) is the special case
\[C_{OP} = C_K, \qquad \mathrm{DISRUPT} = C_F, \qquad \mathrm{HARM} = H_K, \qquad H_F = 0.\]
Propositions~1 and~2 are stated in this paper's symbols \(C_{OP}, \mathrm{DISRUPT}, \mathrm{HARM}\).
```

`\StmtDefIndistinguishability` (Paper 1):

```latex
\textbf{Definition D4 (Observation window; observational indistinguishability).} An observation window is a set \(W \subseteq \{0, 1, 2, \dots\}\) of time indices, finite or not; the observation trajectory on \(W\) is \(Y_W = (y_t)_{t \in W}\). Write \(P_M^W\) for the law of \(Y_W\) under instance \((M,\theta_M,b_M)\) (for infinite \(W\), the law on the product \(\sigma\)-algebra, determined by its finite-dimensional marginals). Instances \((K,\theta_K,b_K)\) and \((F,\theta_F,b_F)\) are observationally indistinguishable on \(W\) if \(P_K^W = P_F^W\). Theorem~1 uses \(W = \{t : t \ge 0\}\); ``indistinguishable at every \(t \ge \tau\)'' (Theorem~2) means \(P_K^W = P_F^W\) for \(W = \{t : t \ge \tau\}\); Theorem~3 (the finite-horizon version of Theorem~2) uses \(W = \{\tau, \dots, \tau+H-1\}\).
```

`\StmtDefDecisionProblem` (Paper 1):

```latex
\textbf{Definition D9 (Prior, policies, Bayes risk, oracle risk, cost of ambiguity).} The cause is drawn as \(M = K\) with prior probability \(p = P(K)\) and \(M = F\) with probability \(1-p\); given \(M\), the observation trajectory \(Y_W\) has law \(P_M^W\). A policy is a measurable map \(\pi\) from observation trajectories on \(W\) to \([0,1]\), read as the probability of the action \emph{contain} (randomized policies allowed; a deterministic policy takes values in \(\{0,1\}\)). Its expected cost is
\[\begin{aligned} R(\pi) = {}& p\,\mathbb{E}_K\big[\pi(Y_W)\,C_K + (1-\pi(Y_W))\,H_K\big] \\ &+ (1-p)\,\mathbb{E}_F\big[\pi(Y_W)\,C_F + (1-\pi(Y_W))\,H_F\big]. \end{aligned}\]
The best achievable expected cost is \(R^\star = \inf_\pi R(\pi)\); the oracle, which observes \(M\), has expected cost \(R_{\text{oracle}} = p \min\{C_K, H_K\} + (1-p)\min\{C_F, H_F\}\); the cost of ambiguity is \(\mathrm{CoA}^\star = R^\star - R_{\text{oracle}}\). Where the observation is the raw trajectory \(Y\) the subscript \(Y\) is written (\(R_Y^\star\), \(\mathrm{CoA}_Y^\star\)).
```

`\StmtPropositionOneTitle` (Paper 1):

```latex
\textbf{Proposition 1 (Cost of ambiguity is bounded below under confounding --- corrected).}
```

`\StmtPropositionOne` (Paper 1):

```latex
Suppose (\(\ast\)) holds (the confounded case), \(0 < p < 1\), \(\mathrm{DISRUPT} > 0\), and \(\mathrm{HARM} > C_{OP}\) (harm strictly worse than routine containment --- the assumption the earlier version omitted). Then the best achievable expected cost among policies mapping \(\{y_t\}\) to \(\{\text{contain}, \text{leave alone}\}\) is

\[R^\star = \min\{\,p\,C_{OP} + (1-p)\,\mathrm{DISRUPT},\ \ p\,\mathrm{HARM}\,\},\]

the oracle's expected cost is \(R_{\text{oracle}} = p\,C_{OP}\), and

\[\boxed{\mathrm{CoA}^\star \;=\; R^\star - R_{\text{oracle}} \;=\; \min\{\,(1-p)\,\mathrm{DISRUPT},\ \ p\,(\mathrm{HARM} - C_{OP})\,\} \;>\; 0.}\]
```

`\StmtPropositionOneTV` (Paper 1):

```latex
\textbf{Proposition~2 (Total-variation extension of Proposition~1).} Let the loss table and prior be as in Proposition~1, with \(0 < p < 1\), \(\mathrm{DISRUPT} > 0\) and \(\mathrm{HARM} > C_{OP}\), but do not assume (\(\ast\)). Let \(f_K, f_F\) be the observation densities (Definition~D10) and set \(a = p(\mathrm{HARM}-C_{OP})\), \(b = (1-p)\,\mathrm{DISRUPT}\). Then
\[\mathrm{CoA}^\star = \int \min\{a f_K(y),\, b f_F(y)\}\, dy = \frac{a+b-\int |af_K - bf_F|\,dy}{2},\]
\[\min(a,b)\,\big(1-\mathrm{TV}(P_K,P_F)\big) \;\le\; \mathrm{CoA}^\star \;\le\; \min(a,b),\]
and, if a common surrogate law \(\bar P\) satisfies \(\mathrm{TV}(P_K,\bar P) \le \epsilon_K\) and \(\mathrm{TV}(P_F,\bar P) \le \epsilon_F\), then
\[\mathrm{CoA}^\star \ge \min(a,b)\max\{0,\ 1-\epsilon_K-\epsilon_F\}.\]
```

`\StmtDefTotalVariation` (Paper 1):

```latex
\textbf{Definition D10 (Observation densities; total variation).} Let \(\mu\) be a measure dominating \(P_K\) and \(P_F\) (e.g.\ \(P_K + P_F\)), and \(f_K, f_F\) their densities with respect to \(\mu\); \(\int \cdot\, dy\) denotes integration against \(\mu\). The total variation distance is
\[\mathrm{TV}(P,P') = \sup_{B} |P(B) - P'(B)| = \tfrac{1}{2}\int |f - f'|\, dy,\]
so that \(1 - \mathrm{TV}(P_K, P_F) = \int \min\{f_K, f_F\}\, dy\).
```

`\StmtTheoremOne` (Paper 1):

```latex
\textbf{Theorem 1 (Indistinguishability criterion).} Under the model of Section 3, with common onset time \(\tau\), mechanism instances \((K, \theta_K, b_K)\) and \((F, \theta_F, b_F)\) induce identical distributions over the observation trajectory \(\{y_t\}_{t\ge 0}\) if and only if

\[\theta_K\, C b_K = \theta_F\, C b_F. \tag{$\ast$}\]
```

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
