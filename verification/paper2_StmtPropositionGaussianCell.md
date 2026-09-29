# Verification packet: Paper 2, Proposition 1 (`\StmtPropositionGaussianCell`)

Source: `papers/paper2/research/statements.tex` at `317caec`, copied verbatim. All mathematics is LaTeX.

## Statement

`\StmtPropositionGaussianCell` (Paper 2):

```latex
\textbf{Proposition 1 (Closed forms for a Gaussian order-flow model).} Under Assumptions 1--4, let the order-flow model \(c\) of Definition~5 be Gaussian: \(Y \mid M \sim \mathcal{N}(\mu_M, \Sigma_Y)\), \(M \in \{K, F\}\), with common covariance \(\Sigma_Y \succ 0\) and whitened separation \(d = \sqrt{(\mu_K - \mu_F)^\top \Sigma_Y^{-1} (\mu_K - \mu_F)} > 0\). Suppose \(S = (q_1, q_2) \neq \emptyset\). Write \(\ell = \operatorname{logit} p\), \(\ell_1 = \operatorname{logit} q_1\), \(\ell^\ast = \operatorname{logit} q^\ast = \log(b/a)\), \(\ell_2 = \operatorname{logit} q_2\) (with \(\operatorname{logit} 0 = -\infty\), \(\operatorname{logit} 1 = +\infty\), \(\Phi(\pm\infty) = 1, 0\) accordingly), and for \(-\infty \le u < v \le +\infty\)
\[
\begin{aligned}
\Pi_K(u, v) &= \Phi\!\Big(\frac{v - \ell}{d} - \frac{d}{2}\Big) - \Phi\!\Big(\frac{u - \ell}{d} - \frac{d}{2}\Big), \\
\Pi_F(u, v) &= \Phi\!\Big(\frac{v - \ell}{d} + \frac{d}{2}\Big) - \Phi\!\Big(\frac{u - \ell}{d} + \frac{d}{2}\Big).
\end{aligned}
\]
Then
\[
m_c(p) = p\,\Pi_K(\ell_1, \ell_2) + (1-p)\,\Pi_F(\ell_1, \ell_2),
\]
\[
\begin{aligned}
D_c(p) = {} & p\,(\alpha_1 - \beta_1)\,\Pi_K(\ell_1, \ell^\ast) - (1-p)\,\beta_1\,\Pi_F(\ell_1, \ell^\ast) \\
& + p\,(\beta_2 - \alpha_2)\,\Pi_K(\ell^\ast, \ell_2) + (1-p)\,\beta_2\,\Pi_F(\ell^\ast, \ell_2),
\end{aligned}
\]
with \(\alpha_1 = s\,a + (1-t)\,b - r_K\tau\), \(\beta_1 = c_v + (1-t)\,b\), \(\alpha_2 = t\,b + (1-s)\,a + r_K\tau\), \(\beta_2 = t\,b - c_v\) (so that \(q_1 = \beta_1/\alpha_1\) and \(q_2 = \beta_2/\alpha_2\), Theorem~1). As \(d \to 0\), \(m_c(p) \to \mathbb{1}[p \in S]\) for \(p \notin \{q_1, q_2\}\) and \(D_c(p) \to (V - \kappa)^+(p)\) for every \(p\), the confounded values of Corollary~1.
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

`\StmtDefCellQuantities` (Paper 2):

```latex
\textbf{Definition 5 (Verification mass, saving and recovered share of a cell).} An \emph{order-flow model} \(c\) is a pair of order-flow laws \(P^c_K, P^c_F\) on a measurable space, with densities \(f^c_K, f^c_F\) with respect to a \(\sigma\)-finite measure \(\nu\) dominating both (e.g.\ \(\nu = P^c_K + P^c_F\)). A \emph{cell} \((c, p)\) is an order-flow model \(c\) together with a prior \(p \in (0,1)\); in Paper~1's grid, \(c\) is a market design in one regime and \(p\) is a prior of the grid. In the setting of Definition~4 with \(P^Y_K = P^c_K\), \(P^Y_F = P^c_F\) and prior \(p \in (0,1)\), write \(P_p = p\,P^c_K + (1-p)\,P^c_F\) for the law of \(Y\) and
\[
q_p(y) \;=\; \frac{p\,f^c_K(y)}{p\,f^c_K(y) + (1-p)\,f^c_F(y)}
\]
for the passive posterior (defined where the denominator is positive, a set of full \(P_p\)-measure). The \emph{verification mass}, the \emph{saving} and the \emph{recovered share} of the cell \((c, p)\) are
\[
m_c(p) = P_p\bigl(q_p(Y) \in S\bigr), \qquad
D_c(p) = \mathbb{E}_p\bigl[(V - \kappa)^+\bigl(q_p(Y)\bigr)\bigr],
\]
\[
\rho_c(p) = \frac{D_c(p)}{\mathrm{CoA}^\star_c(p)} ,
\]
with \(S\), \(V\), \(\kappa\) as in Definition~3 and \(\mathrm{CoA}^\star_c(p)\) the passive cost of ambiguity of Definition~4 for this cell; \(\rho_c(p)\) is defined when \(\mathrm{CoA}^\star_c(p) > 0\). Where \(f^c_K, f^c_F > 0\), \(\operatorname{logit} q_p(y) = \operatorname{logit} p + \Lambda_c(y)\) with \(\Lambda_c = \log(f^c_K / f^c_F)\).
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
- \(q_1, q_2\) and \(S\) are those of Paper 2's Theorem 1; "the confounded values of Corollary 1" refers to Paper 2's Corollary 1. Both are reproduced below, with Paper 2's Lemma 1 and Theorem 2, which they refer to.
- \((V - \kappa)^+(p)\) means \(\max\{V(p) - \kappa(p), 0\}\), with \(V, \kappa\) of Definition 3.
```

### Statements referred to

The statement refers to the statements below. They are reproduced verbatim so that every reference resolves; they are not the statement under verification.

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

`\StmtLemmaPassiveThreshold` (Paper 2):

```latex
\textbf{Lemma 1 (Passive threshold).} Under Assumption 1, let \(q^\ast = b/(a+b) \in (0,1)\). Leaving is strictly optimal for \(q < q^\ast\), containing is strictly optimal for \(q > q^\ast\), and
\[
R(q) \;=\; q\,H_K + (1-q)\,H_F \;-\; (a+b)\,(q - q^\ast)^+ ,
\]
so \(R\) is continuous, concave and piecewise linear on \([0,1]\) with a single kink at \(q^\ast\).
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
