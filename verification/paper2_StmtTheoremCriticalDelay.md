# Verification packet: Paper 2, Theorem 2 (`\StmtTheoremCriticalDelay`)

Source: `papers/paper2/research/statements.tex` at `317caec`, copied verbatim. All mathematics is LaTeX.

## Statement

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

## Assumptions

`\StmtAssumptionCosts` (Paper 2):

```latex
\textbf{Assumption 1 (Cost orderings).} \(H_K > C_K\) and \(C_F > H_F\); that is, \(a > 0\) and \(b > 0\): leaving a compromise is strictly worse than containing it, and containing a fault is strictly worse than leaving it.
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
- \(q_1, q_2\) (and \(q_1(\tau), q_2(\tau)\)) are the endpoints defined in Paper 2's Theorem 1, and "the convention \(q_1 = q_2 = q^\ast\) of Theorem~1" is the one stated there; Theorem 1 is reproduced below with the Lemma 1 it refers to.
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

`\StmtLemmaPassiveThreshold` (Paper 2):

```latex
\textbf{Lemma 1 (Passive threshold).} Under Assumption 1, let \(q^\ast = b/(a+b) \in (0,1)\). Leaving is strictly optimal for \(q < q^\ast\), containing is strictly optimal for \(q > q^\ast\), and
\[
R(q) \;=\; q\,H_K + (1-q)\,H_F \;-\; (a+b)\,(q - q^\ast)^+ ,
\]
so \(R\) is continuous, concave and piecewise linear on \([0,1]\) with a single kink at \(q^\ast\).
```
