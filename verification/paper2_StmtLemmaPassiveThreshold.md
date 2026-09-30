# Verification packet: Paper 2, Lemma 1 (`\StmtLemmaPassiveThreshold`)

Source: `papers/paper2/research/statements.tex` at `d823a85`, copied verbatim. All mathematics is LaTeX.

## Statement

`\StmtLemmaPassiveThreshold` (Paper 2):

```latex
\textbf{Lemma 1 (Passive threshold).} Under Assumption 1, let \(q^\ast = b/(a+b) \in (0,1)\). Leaving is strictly optimal for \(q < q^\ast\), containing is strictly optimal for \(q > q^\ast\), and
\[
R(q) \;=\; q\,H_K + (1-q)\,H_F \;-\; (a+b)\,(q - q^\ast)^+ ,
\]
so \(R\) is continuous, concave and piecewise linear on \([0,1]\) with a single kink at \(q^\ast\).
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

## Assumptions

`\StmtAssumptionCosts` (Paper 2):

```latex
\textbf{Assumption 1 (Cost orderings).} \(H_K > C_K\) and \(C_F > H_F\); that is, \(a > 0\) and \(b > 0\): leaving a compromise is strictly worse than containing it, and containing a fault is strictly worse than leaving it.
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
```
