# Verification packet: Paper 2, Lemma 3 (`\StmtLemmaValueTent`)

Source: `papers/paper2/research/statements.tex` at `317caec`, copied verbatim. All mathematics is LaTeX.

## Statement

`\StmtLemmaValueTent` (Paper 2):

```latex
\textbf{Lemma 3 (The value of information is a tent).} Under Assumptions 1 and 3,
\[
V(q) \;=\; \max\bigl\{\, 0,\; \min\{\, G^+(q),\; G^-(q) \,\} \bigr\},
\]
where
\[
G^+(q) = q\,s\,a - (1-q)(1-t)\,b, \qquad
G^-(q) = (1-q)\,t\,b - q\,(1-s)\,a .
\]
Consequently, with
\[
q_L = \frac{(1-t)\,b}{s\,a + (1-t)\,b}, \qquad q_U = \frac{t\,b}{t\,b + (1-s)\,a},
\]
(i) \(0 \le q_L < q^\ast < q_U \le 1\); (ii) \(V(q) > 0\) if and only if \(q \in (q_L, q_U)\), equivalently if and only if \(q^- < q^\ast < q^+\) (the two posteriors fall strictly on opposite sides of \(q^\ast\)); (iii) \(V\) is affine and strictly increasing on \([q_L, q^\ast]\), affine and strictly decreasing on \([q^\ast, q_U]\), and zero outside \((q_L, q_U)\); (iv) \(V\) attains its maximum uniquely at \(q^\ast\), with
\[
V(q^\ast) \;=\; (s + t - 1)\,\frac{a\,b}{a+b} \;=\; (s+t-1)\,a\,q^\ast \;>\; 0 .
\]
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
```
