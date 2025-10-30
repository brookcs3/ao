Assignment 5 Master Walkthrough and Guide

I. Assignment and Submission Metadata

Assignment Title: Assignment 5 - Context-Free Grammars, Parsing, and Ambiguity

Total Points: 60 points

Submission Format: Two Parts (PDF for explanations/screenshots, ZIP for JFLAP files)

Goal: Create a comprehensive guide for all five problems, ensuring all required JFLAP files and proofs are documented.

II. Problem 1: CFG for L = {a^n b^m : 2n ≤ m ≤ 3n}

A. Core Requirements

Language ($L$): $L = \{a^n b^m \mid 2n \le m \le 3n, n \ge 0\}$

Grammar Type: Context-Free Grammar (CFG)

JFLAP File: Problem1_CFG.jff

B. Context-Free Grammar

The grammar must control the ratio of $b$'s to $a$'s within the specified range while maintaining the $a^* b^*$ order.

$$S \rightarrow aSbb \mid aSbbb \mid \lambda
$$### C. Analysis and Formal Justification

The grammar is proven correct by tracking the contribution of $b$'s per $a$.

1.  **Variable Dependency:** The structure $a S \dots$ enforces the prefix $a^n$ followed by $b^m$ (i.e., $a^* b^*$ order).
2.  **Ratio Control:** Let $n$ be the total number of $a$'s. Let $x$ be the number of times $S \rightarrow aSbbb$ is chosen. The remaining $(n-x)$ times, $S \rightarrow aSbb$ is chosen. The total number of $b$'s, $m$, is:$$

m = 3x + 2(n - x) = 3x + 2n - 2x = 2n + x

$$3. **Range Validation:** Since the count of $x$ (the $3b$ rule) is bounded by $0 \le x \le n$:

   * Minimum $m$ occurs when $x=0$: $m = 2n$

   * Maximum $m$ occurs when $x=n$: $m = 3n$

   * This confirms the grammar correctly generates strings where $2n \le m \le 3n$.

### D. JFLAP Testing Matrix

The JFLAP screenshot must confirm both acceptance of valid strings and rejection of strings outside the bounds or order.

| Input String | $n$ | $m$ | $2n \le m \le 3n$? | Expected | 
 | ----- | ----- | ----- | ----- | ----- | 
| $\lambda$ | 0 | 0 | $0 \le 0 \le 0$ | Accept | 
| `abb` | 1 | 2 | $2 \le 2 \le 3$ | Accept | 
| `abbb` | 1 | 3 | $2 \le 3 \le 3$ | Accept | 
| `aabbbb` | 2 | 4 | $4 \le 4 \le 6$ | Accept | 
| `aabbbbb` | 2 | 5 | $4 \le 5 \le 6$ | Accept | 
| `aabbbbbb` | 2 | 6 | $4 \le 6 \le 6$ | Accept | 
| `ab` | 1 | 1 | $2 \le 1 \le 3$ | Reject (Too few $b$'s) | 
| `aaabbbbbbbb` | 3 | 9 | $6 \le 9 \le 9$ | Accept | 
| `aabbbbbbb` | 2 | 7 | $4 \le 7 \le 6$ | Reject (Too many $b$'s) | 

## III. Problem 2: CFG for L = {w ∈ {a,b}\* : n_a(w) = 2n_b(w)}

### A. Core Requirements

* **Language ($L$):** $L = \{w \in \{a, b\}^* \mid n_a(w) = 2n_b(w)\}$

* **Grammar Type:** Context-Free Grammar (CFG)

* **JFLAP File:** `Problem2_CFG.jff`

### B. Context-Free Grammar

The grammar must maintain the $2:1$ ratio of $a$'s to $b$'s while allowing arbitrary interleaving.

$$S \rightarrow aabS \mid abaS \mid baaS \mid \lambda$$
### C. Analysis and Formal Justification

1.  **Ratio Invariance:** Every recursive production ($aabS$, $abaS$, $baaS$) contributes exactly two $a$'s and one $b$. Therefore, the ratio $n_a : n_b$ is preserved at $2:1$ throughout the derivation, and the final string satisfies $n_a(w) = 2n_b(w)$.
2.  **Permutation Coverage:** Any minimal string satisfying the $2:1$ ratio has length 3 and is a permutation of $aab$. The three rules explicitly cover all possible cyclic permutations of the block. Since any string $w \in L$ is a concatenation of these blocks, the grammar is sufficiently powerful.

### D. JFLAP Testing Matrix

The JFLAP screenshot must test both simple blocks and complex concatenations.

| Input String | $n_a$ | $n_b$ | $n_a = 2n_b$? | Expected |
| :---: | :---: | :---: | :---: | :---: |
| `aba` | 2 | 1 | $2 = 2(1)$ | Accept |
| `baaS` | 2 | 1 | $2 = 2(1)$ | Accept |
| `aabaab` | 4 | 2 | $4 = 2(2)$ | Accept (Concatenation) |
| `aababa` | 4 | 2 | $4 = 2(2)$ | Accept |
| `aa` | 2 | 0 | $2 \ne 2(0)$ | Reject |
| `b` | 0 | 1 | $0 \ne 2(1)$ | Reject |
| `aabb` | 2 | 2 | $2 \ne 2(2)$ | Reject |

-----

## IV. Problem 3: Derivation Tree for (a + b) * c + d

### A. Core Requirements

  * **Task:** Give the derivation tree for $w = (a + b) * c + d$.
  * **Grammar:** Standard expression grammar (Modified Example 5.12)
  * **JFLAP File:** `Problem3_Expression_Grammar.jff`

### B. Grammar Rules and Precedence

The grammar rules establish the mathematical hierarchy:

$$\begin{array}{ll}
E \rightarrow T \mid E + T & \quad \text{(Addition: Lowest Precedence, Left-Associative)} \\
T \rightarrow F \mid T * F & \quad \text{(Multiplication: Medium Precedence, Left-Associative)} \\
F \rightarrow I \mid (E) & \quad \text{(Parentheses: Highest Precedence)} \\
I \rightarrow a \mid b \mid c \mid d & \quad \text{(Identifiers)}
\end{array}
$$### C. Detailed Leftmost Derivation and Structure

The parse must structure the expression as $((a+b) * c) + d$. The first operation applied (at the root) must be the last one executed (the lowest precedence operation, which is the final addition).

**Leftmost Derivation Sequence:**$$

\begin{align*}
E &\xrightarrow{E \rightarrow E+T} E + T \
&\xrightarrow{E \rightarrow T} T + T \
&\xrightarrow{T \rightarrow TF} T * F + T \
&\xrightarrow{T \rightarrow F} F * F + T \
&\xrightarrow{F \rightarrow (E)} (E) * F + T \quad \text{(Applies Parentheses)} \
&\xrightarrow{E \rightarrow E+T} (E + T) * F + T \quad \text{(Innermost Addition)} \
&\xrightarrow{E \rightarrow T} (T + T) * F + T \
&\xrightarrow{\dots} (a + b) * c + d
\end{align}
$$Derivation Tree (Graphical Representation):

The tree structure demonstrates strict adherence to precedence:

Root $E$ uses $E \rightarrow E+T$ (The last $+$).

Left $E$ resolves via $E \rightarrow T$ and then $T \rightarrow T*F$ (The $*$).

Left $T$ resolves via $T \rightarrow F$ and then $F \rightarrow (E)$ (The parentheses).

JFLAP Screenshot:

V. Problem 4: Ambiguity Proof

A. Core Requirements

Grammar ($G_A$): $S \rightarrow aSb \mid SS \mid \lambda$

Task: Show $G_A$ is Ambiguous, but $L(G_A)$ is Not Inherently Ambiguous.

JFLAP Files: Problem4_Ambiguous_Grammar.jff and Problem4_Unambiguous_Grammar.jff

B. Part A: Proof of Ambiguity

Proof Strategy: Show two distinct parse trees exist for the string $w = aabb$. Ambiguity in this grammar arises from the $S \rightarrow SS$ rule, which allows the string to be parsed either by nesting (via $aSb$) or concatenation (via $SS$).

Derivation 1 (Nested Grouping: $a(ab)b$)

Tree Structure: $S \rightarrow a S b$. The central $S$ recursively expands to $a b$.

JFLAP Tree:

Derivation 2 (Sequential Grouping: $(ab)(ab)$)

Tree Structure: $S \rightarrow S S$. The two child $S$'s each independently derive $a b$.

JFLAP Tree:

Since the string $aabb$ has two structurally different parse trees, the grammar $G_A$ is formally ambiguous.

JFLAP Screenshots Proving Ambiguity:

Tree 1:

Tree 2:

Test Cases:

C. Part B: Proof the Language is NOT Inherently Ambiguous

Language Identity: The language generated is $L(G_A) = \{a^n b^n \mid n \ge 0\}$, often referred to as the Dyck Language (if symbols are parentheses).

Definition: A language is not inherently ambiguous if there exists at least one unambiguous grammar that generates it.

Unambiguous Grammar ($G_U$):

$$G_U: S \rightarrow aSbS \mid \lambda$$

Proof of Unambiguity:
The grammar $G_U$ is unambiguous because the recursive rule $S \rightarrow aSbS$ forces a sequential, non-overlapping decomposition of the string. Any non-empty string $w \in L(G_U)$ must be uniquely factored into $w = a w_1 b w_2$, where $w_1$ and $w_2$ are derived from the two child $S$ non-terminals. This factorization is unique because the initial $a$ must match the first $b$ that closes a fully balanced prefix, eliminating the recursive choice that caused the ambiguity in $G_A$. Since $G_U$ is unambiguous and $L(G_U) = L(G_A)$, the language $L(G_A)$ is NOT inherently ambiguous.

JFLAP Screenshot (Unambiguous Grammar Test):

VI. Problem 5: Theoretical Proof

A. Core Requirements

Task: Prove that if $G$ is a context-free grammar in which no variable occurs on the left side of more than one production, then $G$ is unambiguous.

Type: Formal Proof

B. Formal Statement and Proof

Theorem: Let $G = (V, T, S, P)$ be a context-Free Grammar such that $\forall A \in V$, $A$ appears on the left side of at most one production in $P$. Then $G$ is unambiguous.

Proof:

We prove this by showing that every string $w \in L(G)$ has a unique derivation tree. We use the technique of strong induction on the number of derivation steps, $n$.

Base Case ($n = 1$):
If $w$ is derived in one step, the derivation is $S \rightarrow w$. Since the variable $S$ appears on the left side of at most one production, the rule $S \rightarrow w$ is the only possible first step. Thus, the derivation and its tree are uniquely determined.

Inductive Hypothesis:
Assume that for all strings derivable in $k$ or fewer steps ($k \ge 1$), the derivation tree is unique.

Inductive Step (Conclusion for $n = k+1$):
Consider a string $w$ derived in $k + 1$ steps.

Unique First Step: The derivation must begin with the first production $S \rightarrow \alpha$. Because $S$ appears on the left side of at most one production, this initial step is uniquely determined.

Unique Subtrees: The string $w$ is partitioned according to $\alpha = \alpha_1 \alpha_2 \dots \alpha_m$. Any non-terminal $\alpha_i \in V$ derives a substring $w_i$ in fewer than $k+1$ steps. Since $\alpha_i$ also appears on the left side of at most one production, and by the inductive hypothesis all shorter derivations are unique, the derivation tree for $w_i$ from $\alpha_i$ is uniquely determined.

Since the entire tree is constructed from a unique root expansion and unique subtrees, the final derivation tree for $w$ is uniquely determined.

By the principle of mathematical induction, the grammar $\mathbf{G}$ is unambiguous. $\mathbf{\square}$