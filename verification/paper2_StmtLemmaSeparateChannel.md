# Verification packet: Paper 2, Lemma 2 (`\StmtLemmaSeparateChannel`)

Source: `papers/paper2/research/statements.tex` at `d823a85`, copied verbatim. All mathematics is LaTeX.

## Statement

`\StmtLemmaSeparateChannel` (Paper 2):

```latex
\textbf{Lemma 2 (Verification composes with any passive posterior).} Under Assumption 2, let \(q(y) = P(K \mid Y = y)\) be the passive (order-flow) posterior. Then \(P(K \mid Y = y, Z = z)\) equals the verification update of Definition 2 applied to \(q = q(y)\): it is \(q(y)^+\) if \(z = +\) and \(q(y)^-\) if \(z = -\). In particular the characteristics \((s,t)\), and hence \(V\), \(S\) and all results below, are the same whatever the order-flow law, including when the order-flow laws under \(K\) and \(F\) coincide.
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
where \(P(z)\,R(q^z)\) is read as \(\min\{\, P(z,K)\,C_K + P(z,F)\,C_F,\; P(z,K)\,H_K + P(z,F)\,H_F \,\}\) with \(P(z,K)=P(z\mid K)\,q\) and \(P(z,F)=P(z\mid F)\,(1-q)\) (equal to the product when \(P(z)>0\), and zero when \(P(z)=0\)). The \emph{value of information} is \(V(q) = R(q) - [P(+)R(q^+) + P(-)R(q^-)]\), the \emph{verification cost} is \(\chi(q) = c_v + q\,r_K\,\tau\), and the \emph{verification region} is
\[
S \;=\; \{\, q \in [0,1] : R_v(q) < R(q) \,\} \;=\; \{\, q \in [0,1] : V(q) > \chi(q) \,\}.
\]
Ties are resolved in favour of the passive action: the operator verifies only when verifying is strictly cheaper.
```

## Assumptions

`\StmtAssumptionSeparateChannel` (Paper 2):

```latex
\textbf{Assumption 2 (Separate channel).} Verification reads authorization, not order flow: it asks whether the holder of the credential or session authorized the orders, through a channel the person submitting them does not control (for example an out-of-band confirmation with the account holder, or a step-up authentication with a factor bound to the holder). A check of whether the credential or session is valid is not such a check, since a stolen credential or a hijacked session is valid under \(K\). Its outcome \(Z\) is conditionally independent of the order-flow observation \(Y\) given the cause: \(P(Z, Y \mid c) = P(Z \mid c)\,P(Y \mid c)\) for \(c \in \{K, F\}\), and \((s,t)\) do not depend on \(Y\).
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
- \(x^+ = \max\{x, 0\}\); \(\mathbb{1}[\cdot]\) is the indicator.
- \(q^\ast = b/(a+b)\) (Paper 2): defined in Paper 2's Lemma 1 (``let \(q^\ast = b/(a+b)\)'').
- \(Y\) is the order-flow observation of Assumption 2; \(q(y)^\pm\) is \(q^\pm\) of Definition 2 evaluated at \(q = q(y)\).
- \(\chi(q) = c_v + q\,r_K\,\tau\) is the verification cost of Definition 3.
- ``All results below'' is not further specified in the source: in Paper 2's statements file, Lemma 2 is followed by Lemma 3, Theorems 1--2, Remark 1, Corollaries 1--4, Lemma 4 and Proposition 1. None of them is reproduced here.
```
