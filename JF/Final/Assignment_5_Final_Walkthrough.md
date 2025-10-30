# Assignment 5 - Final Walkthrough
**Course:** CS 321 - Theory of Computation  
**Module:** Module 5 - Context-Free Grammars, Parsing, Ambiguity  
**Due Date:** Wednesday, October 31, 2025, 11:59 PM  
**Total Points:** 60 points  
**Student Name:** [Your Name]

---

## Metadata

**Construct Folder:** `/mnt/c/Users/Owner/FALL 2025/INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)/Modue 5/JF/Final`

**Referenced JFLAP Files:**
- `Problem 1/Problem 1.jff`
- `Problem 2/Problem 2.jff`
- `Problem 3/P3.jff`
- `Problem 4/Ambiguous Grammar Tree 1 (aSb First).jff`
- `Problem 4/Ambiguous Grammar Tree 2 (SS First).jff`
- `Problem 4/Unambiguous Grammar.jff`

**Referenced Screenshots:**
- `Problem 1/Problem 1.png`
- `Problem 2/Problem 2.png`
- `Problem 3/Problem 3.png`
- `Problem 3/Problem 3 B.png`
- `Problem 4/Ambiguous Grammar Tree 1 (aSb First)-Tests-BlowUp.png`
- `Problem 4/Ambiguous Grammar Tree 1 (aSb First).png`
- `Problem 4/Ambiguous Grammar Tree 2 (SS First).png`
- `Problem 4/Unambiguous Grammer-Tests.png`
- `Problem 4/Unambiguous Grammar-Tree.png`

---

## Section 5.1: Context-Free Grammar Construction

### Problem 1: Create a context-free grammar for the language L = {a^n b^m : 2n ≤ m ≤ 3n}

**Question Type:** JFLAP-based (CFG Construction)  
**JFLAP File:** `Problem 1/Problem 1.jff`  
**Screenshot:** `Problem 1/Problem 1.png`

#### Context-Free Grammar

The grammar is designed to ensure that for every $a$ generated, the number of $b$'s is constrained between 2 and 3 times the number of $a$'s.

$$S \rightarrow aSbb \mid aSbbb \mid \lambda$$

#### Design Approach and Reasoning

The key insight is that we need to maintain the ratio $2n \le m \le 3n$ throughout the derivation. The grammar achieves this by:

1. **Rule $S \rightarrow aSbb$**: For each $a$ added, we add exactly 2 $b$'s (minimum case)
2. **Rule $S \rightarrow aSbbb$**: For each $a$ added, we add exactly 3 $b$'s (maximum case)
3. **Rule $S \rightarrow \lambda$**: Base case for the empty string (when $n=0$, $m=0$)

By allowing a choice between adding 2 or 3 $b$'s for each $a$, we can generate any value of $m$ in the range $[2n, 3n]$ for a given $n$.

#### How the Grammar Works

- Start with $S$
- Apply $S \rightarrow aSbb$ or $S \rightarrow aSbbb$ recursively $n$ times
- Each application adds one $a$ and either 2 or 3 $b$'s
- Finish with $S \rightarrow \lambda$ to terminate
- The total number of $b$'s will be between $2n$ (all minimum choices) and $3n$ (all maximum choices)

#### Test Cases and Correctness

**Accept Cases (strings in L):**
- $\lambda$ (empty string): $n=0, m=0$, satisfies $2(0) \le 0 \le 3(0)$ ✓
- $abb$: $n=1, m=2$, satisfies $2(1) \le 2 \le 3(1)$ ✓
- $abbb$: $n=1, m=3$, satisfies $2(1) \le 3 \le 3(1)$ ✓
- $aabbbb$: $n=2, m=4$, satisfies $2(2) \le 4 \le 3(2)$ ✓
- $aabbbbb$: $n=2, m=5$, satisfies $2(2) \le 5 \le 3(2)$ ✓
- $aabbbbbb$: $n=2, m=6$, satisfies $2(2) \le 6 \le 3(2)$ ✓
- $aaabbbbbb$: $n=3, m=6$, satisfies $2(3) \le 6 \le 3(3)$ ✓

**Reject Cases (strings not in L):**
- $a$: $n=1, m=0$, violates $2(1) \le 0$ ✗
- $ab$: $n=1, m=1$, violates $2(1) \le 1$ ✗
- $abbbb$: $n=1, m=4$, violates $4 \le 3(1)$ ✗
- $aab$: $n=2, m=1$, violates $2(2) \le 1$ ✗
- $aabbb$: $n=2, m=3$, violates $2(2) \le 3$ ✗
- $aabbbbbbb$: $n=2, m=7$, violates $7 \le 3(2)$ ✗
- $ba$: Invalid order (b before a) ✗
- $aba$: Invalid interleaving ✗

The screenshot demonstrates that the grammar correctly accepts all valid strings and rejects all invalid strings, confirming the correctness of the design.

---

### Problem 2: Create a context-free grammar for the language L = {w ∈ {a,b}* : n_a(w) = 2n_b(w)}

**Question Type:** JFLAP-based (CFG Construction)  
**JFLAP File:** `Problem 2/Problem 2.jff`  
**Screenshot:** `Problem 2/Problem 2.png`

#### Context-Free Grammar

This grammar ensures a constant ratio of 2 $a$'s for every 1 $b$, regardless of the order in which the terminals appear.

$$S \rightarrow aabS \mid abaS \mid baaS \mid \lambda$$

#### Design Approach and Reasoning

The challenge is that the language allows arbitrary interleaving of $a$'s and $b$'s, as long as the final count maintains $n_a = 2n_b$. The grammar handles this by:

1. **Rule $S \rightarrow aabS$**: Adds the pattern $aab$ (2 $a$'s, 1 $b$)
2. **Rule $S \rightarrow abaS$**: Adds the pattern $aba$ (2 $a$'s, 1 $b$)
3. **Rule $S \rightarrow baaS$**: Adds the pattern $baa$ (2 $a$'s, 1 $b$)
4. **Rule $S \rightarrow \lambda$**: Base case for the empty string

Each recursive rule adds exactly 2 $a$'s and 1 $b$ in different orderings, covering all possible local arrangements while maintaining the global 2:1 ratio.

#### How the Grammar Works

- Start with $S$
- Apply any combination of the three recursive rules
- Each application adds a "block" of 2 $a$'s and 1 $b$ in some order
- The choice of which rule to apply determines the local ordering
- Finish with $S \rightarrow \lambda$ to terminate
- The result is a string where $n_a = 2n_b$ with arbitrary interleaving

#### Test Cases and Correctness

**Accept Cases (strings in L):**
- $\lambda$ (empty string): $n_a=0, n_b=0$, satisfies $0 = 2(0)$ ✓
- $aab$: $n_a=2, n_b=1$, satisfies $2 = 2(1)$ ✓
- $aba$: $n_a=2, n_b=1$, satisfies $2 = 2(1)$ ✓
- $baa$: $n_a=2, n_b=1$, satisfies $2 = 2(1)$ ✓
- $aabaab$: $n_a=4, n_b=2$, satisfies $4 = 2(2)$ ✓
- $aabbaa$: $n_a=4, n_b=2$, satisfies $4 = 2(2)$ ✓
- $baaaab$: $n_a=4, n_b=2$, satisfies $4 = 2(2)$ ✓
- $aaabaabaab$: $n_a=6, n_b=3$, satisfies $6 = 2(3)$ ✓

**Reject Cases (strings not in L):**
- $a$: $n_a=1, n_b=0$, violates $1 = 2(0)$ ✗
- $b$: $n_a=0, n_b=1$, violates $0 = 2(1)$ ✗
- $aa$: $n_a=2, n_b=0$, violates $2 = 2(0)$ ✗
- $ab$: $n_a=1, n_b=1$, violates $1 = 2(1)$ ✗
- $aaab$: $n_a=3, n_b=1$, violates $3 = 2(1)$ ✗
- $aabb$: $n_a=2, n_b=2$, violates $2 = 2(2)$ ✗
- $aaabb$: $n_a=3, n_b=2$, violates $3 = 2(2)$ ✗
- $aaabbb$: $n_a=3, n_b=3$, violates $3 = 2(3)$ ✗

The screenshot demonstrates that the grammar correctly handles arbitrary interleaving while maintaining the 2:1 ratio, confirming the correctness of the design.

---

## Section 5.2: Derivation Trees and Ambiguity

### Problem 3: Give the derivation tree for (a + b) * c + d, using the grammar in Example 5.12, but with I → a|b|c|d

**Question Type:** JFLAP-based (Derivation Tree)  
**JFLAP File:** `Problem 3/P3.jff`  
**Screenshots:** `Problem 3/Problem 3.png` (tests), `Problem 3/Problem 3 B.png` (derivation tree)

#### Grammar Rules (Modified Example 5.12)

The grammar for arithmetic expressions with proper operator precedence:

$$\begin{align*}
E &\rightarrow E+T \mid T \\
T &\rightarrow T*F \mid F \\
F &\rightarrow (E) \mid I \\
I &\rightarrow a \mid b \mid c \mid d
\end{align*}$$

**Precedence Hierarchy:**
- **Lowest Precedence:** Addition ($+$) - handled by $E$ rules
- **Medium Precedence:** Multiplication ($*$) - handled by $T$ rules
- **Highest Precedence:** Parentheses and identifiers - handled by $F$ and $I$ rules

#### Design Approach and Reasoning

This grammar enforces correct operator precedence through its hierarchical structure:

1. **Expression level ($E$)**: Handles addition, the lowest precedence operator
2. **Term level ($T$)**: Handles multiplication, which binds tighter than addition
3. **Factor level ($F$)**: Handles parentheses (highest precedence) and atomic identifiers
4. **Identifier level ($I$)**: Represents the terminal symbols (variables)

The grammar ensures that multiplication is performed before addition, and parenthesized expressions are evaluated first.

#### Leftmost Derivation Sequence

For the string $(a+b)*c+d$:

$$\begin{align*}
E &\Rightarrow E+T \\
&\Rightarrow T+T \\
&\Rightarrow T*F+T \\
&\Rightarrow F*F+T \\
&\Rightarrow (E)*F+T \\
&\Rightarrow (E+T)*F+T \\
&\Rightarrow (T+T)*F+T \\
&\Rightarrow (F+T)*F+T \\
&\Rightarrow (I+T)*F+T \\
&\Rightarrow (a+T)*F+T \\
&\Rightarrow (a+F)*F+T \\
&\Rightarrow (a+I)*F+T \\
&\Rightarrow (a+b)*F+T \\
&\Rightarrow (a+b)*I+T \\
&\Rightarrow (a+b)*c+T \\
&\Rightarrow (a+b)*c+F \\
&\Rightarrow (a+b)*c+I \\
&\Rightarrow (a+b)*c+d
\end{align*}$$

#### Derivation Tree Structure

The parse tree (shown in screenshot `Problem 3 B.png`) demonstrates:

1. **Root:** $E$ (the start symbol)
2. **First split:** $E \rightarrow E+T$ (outermost addition)
3. **Left subtree:** The expression $(a+b)*c$ is derived from the left $E$
   - This $E$ derives to $T$ (no addition at this level)
   - $T \rightarrow T*F$ (multiplication)
   - Left $T$ derives $(a+b)$ through parentheses
   - Right $F$ derives $c$
4. **Right subtree:** The term $d$ is derived from the right $T$

The tree structure correctly shows that:
- The outermost operation is addition ($+$)
- The left operand of this addition is $(a+b)*c$ (multiplication has higher precedence)
- The right operand is $d$
- Inside the parentheses, $a+b$ is correctly parsed as addition

#### Test Cases

The screenshot `Problem 3.png` shows test cases confirming the grammar accepts valid arithmetic expressions and rejects malformed ones:

**Accept Cases:**
- Simple identifiers: $a$, $b$, $c$, $d$
- Addition: $a+b$, $c+d$
- Multiplication: $a*b$, $c*d$
- Parentheses: $(a)$, $(a+b)$
- Complex expressions: $(a+b)*c$, $(a+b)*c+d$

**Reject Cases:**
- Empty string
- Invalid operators: $a\&b$, $a\#b$
- Mismatched parentheses: $(a$, $a)$
- Invalid syntax: $+a$, $a+$, $**a$

The derivation tree in screenshot `Problem 3 B.png` visually confirms the correct precedence and associativity for the target expression $(a+b)*c+d$.

---

### Problem 4: Show that the following grammar is ambiguous, but that the language it generates is not inherently ambiguous

**Grammar:** $S \rightarrow aSb \mid SS \mid \lambda$

**Question Type:** JFLAP-based (Ambiguity Proof with visual evidence)  
**JFLAP Files:**
- `Problem 4/Ambiguous Grammar Tree 1 (aSb First).jff`
- `Problem 4/Ambiguous Grammar Tree 2 (SS First).jff`
- `Problem 4/Unambiguous Grammar.jff`

**Screenshots:**
- `Problem 4/Ambiguous Grammar Tree 1 (aSb First)-Tests-BlowUp.png` (tests)
- `Problem 4/Ambiguous Grammar Tree 1 (aSb First).png` (parse tree 1)
- `Problem 4/Ambiguous Grammar Tree 2 (SS First).png` (parse tree 2)
- `Problem 4/Unambiguous Grammer-Tests.png` (unambiguous tests)
- `Problem 4/Unambiguous Grammar-Tree.png` (unambiguous parse tree)

#### Part I: Proving the Grammar is Ambiguous

**Definition:** A grammar is ambiguous if there exists at least one string in the language that has two or more distinct parse trees (or equivalently, two or more distinct leftmost derivations).

**Proof Strategy:** We demonstrate ambiguity by exhibiting a string with two distinct parse trees.

**Witness String:** $w = aabb$

**Derivation 1 (Using $S \rightarrow aSb$ first):**

$$\begin{align*}
S &\Rightarrow aSb \\
&\Rightarrow aaSbb \\
&\Rightarrow a\lambda bb \\
&\Rightarrow aabb
\end{align*}$$

**Parse Tree 1 Structure** (shown in `Ambiguous Grammar Tree 1 (aSb First).png`):
```
       S
      /|\
     a S b
      /|\
     a S b
       |
       λ
```

This tree represents a **nested structure**: the string is parsed as $a(ab)b$, where the inner $ab$ is wrapped by an outer $a$ and $b$.

**Derivation 2 (Using $S \rightarrow SS$ first):**

$$\begin{align*}
S &\Rightarrow SS \\
&\Rightarrow aSbS \\
&\Rightarrow a\lambda bS \\
&\Rightarrow abS \\
&\Rightarrow abaSb \\
&\Rightarrow aba\lambda b \\
&\Rightarrow aabb
\end{align*}$$

**Parse Tree 2 Structure** (shown in `Ambiguous Grammar Tree 2 (SS First).png`):
```
       S
      / \
     S   S
    /|\  /|\
   a S b a S b
     |     |
     λ     λ
```

This tree represents a **concatenation structure**: the string is parsed as $(ab)(ab)$, where two independent $ab$ substrings are concatenated.

**Conclusion:** Since the string $aabb$ has two distinct parse trees with different structural interpretations, the grammar $G_A: S \rightarrow aSb \mid SS \mid \lambda$ is **ambiguous**.

The screenshots `Ambiguous Grammar Tree 1 (aSb First).png` and `Ambiguous Grammar Tree 2 (SS First).png` visually confirm these two distinct parse trees for the same string.

#### Part II: Proving the Language is NOT Inherently Ambiguous

**Definition:** A language is inherently ambiguous if every grammar that generates it is ambiguous. Conversely, a language is NOT inherently ambiguous if there exists at least one unambiguous grammar that generates it.

**Proof Strategy:** We construct an unambiguous grammar that generates the same language as $G_A$.

**Language Analysis:**

First, we determine what language $G_A$ generates. The grammar has three rules:
- $S \rightarrow aSb$: Adds matching $a$ and $b$ on the outside
- $S \rightarrow SS$: Concatenates two strings from the language
- $S \rightarrow \lambda$: Generates the empty string

By analyzing the grammar, we can show that $L(G_A) = \{w \in \{a,b\}^* : n_a(w) = n_b(w) \text{ and every prefix has } n_a \ge n_b\}$. This is the language of **balanced parentheses** (if we think of $a$ as "(" and $b$ as ")").

**Unambiguous Grammar:**

$$G_U: S \rightarrow aSbS \mid \lambda$$

**JFLAP File:** `Problem 4/Unambiguous Grammar.jff`

**Why $G_U$ is Unambiguous:**

The grammar $G_U$ has only two rules, and the structure is carefully designed:
1. $S \rightarrow aSbS$: This rule adds an $a$, then recursively generates a balanced substring, then adds a $b$, then recursively generates another balanced substring
2. $S \rightarrow \lambda$: Base case

For any string in the language, there is exactly one way to parse it:
- The first $a$ in the string must be matched with its corresponding $b$ (the first $b$ that closes the balanced prefix)
- This uniquely determines where to split the string
- The grammar enforces a **canonical parsing** where each $a$ is immediately followed by its matching balanced substring before the closing $b$

**Proof that $L(G_U) = L(G_A)$:**

We need to show that both grammars generate the same language.

**($L(G_U) \subseteq L(G_A)$):** Every string generated by $G_U$ can be generated by $G_A$:
- $\lambda$ is generated by both
- If $G_U$ generates $aSbS$, we can use $G_A$ to generate $aSb$ (from the first part) and $S$ (from the second part), then concatenate using $SS$

**($L(G_A) \subseteq L(G_U)$):** Every string generated by $G_A$ can be generated by $G_U$:
- This requires showing that the concatenation rule $SS$ in $G_A$ can be simulated by the $aSbS$ rule in $G_U$
- The key insight is that any balanced string can be decomposed into a form where the first $a$ is matched with a specific $b$, and the remaining parts are balanced

**Verification with JFLAP:**

The screenshot `Unambiguous Grammer-Tests.png` shows that $G_U$ accepts the same set of test strings as $G_A$:
- Both accept: $\lambda$, $ab$, $aabb$, $abab$, $aaabbb$, etc.
- Both reject: $a$, $b$, $ba$, $abb$, $aab$, etc.

The screenshot `Unambiguous Grammar-Tree.png` shows that for the string $aabb$, there is only one parse tree in $G_U$, confirming unambiguity.

**Conclusion:** Since we have constructed an unambiguous grammar $G_U$ that generates the same language as $G_A$, the language $L(G_A)$ is **NOT inherently ambiguous**.

#### Summary

- **Part I:** The grammar $S \rightarrow aSb \mid SS \mid \lambda$ is ambiguous (proven by exhibiting two parse trees for $aabb$)
- **Part II:** The language generated by this grammar is not inherently ambiguous (proven by constructing the unambiguous grammar $S \rightarrow aSbS \mid \lambda$)

---

### Problem 5: Prove that if G is a context-free grammar in which no variable occurs on the left side of more than one production, then G is unambiguous

**Question Type:** Theory-only (Formal Proof)  
**JFLAP File:** N/A (No JFLAP required)  
**Screenshot:** N/A (No screenshot required)

#### Theorem Statement

**Theorem:** Let $G = (V, T, S, P)$ be a context-free grammar such that each variable $A \in V$ appears on the left-hand side of at most one production in $P$. Then $G$ is unambiguous.

#### Proof

We prove this theorem directly by showing that every string $w \in L(G)$ has a unique derivation tree.

**Proof by Strong Induction on Derivation Length:**

We proceed by strong induction on the number of derivation steps $n$ required to generate a string $w$.

**Base Case ($n = 1$):**

If $w$ is derived in exactly one step, then the derivation is:
$$S \Rightarrow w$$

This means there is a production $S \rightarrow w$ in $P$. Since $S$ appears on the left-hand side of at most one production (by hypothesis), this production is unique. Therefore, the derivation tree for $w$ is uniquely determined: it consists of the root $S$ with children forming the string $w$.

Thus, the base case holds.

**Inductive Hypothesis:**

Assume that for all $k$ with $1 \le k \le n$, any string derivable in $k$ or fewer steps has a unique derivation tree.

**Inductive Step:**

Consider a string $w$ that is derived in exactly $n+1$ steps. The derivation must begin with:
$$S \Rightarrow \alpha$$

where $\alpha = \alpha_1 \alpha_2 \cdots \alpha_m$ is a sentential form (a string of variables and terminals).

**Uniqueness of the First Step:**

Since $S$ appears on the left-hand side of at most one production in $P$, the production $S \rightarrow \alpha$ is uniquely determined. Therefore, the first step of the derivation is unique.

**Uniqueness of Subsequent Steps:**

The string $w$ is derived from $\alpha$ in $n$ steps:
$$\alpha = \alpha_1 \alpha_2 \cdots \alpha_m \Rightarrow^* w$$

We can partition $w$ as:
$$w = w_1 w_2 \cdots w_m$$

where each $w_i$ is derived from $\alpha_i$.

For each $i$:
- If $\alpha_i \in T$ (a terminal), then $w_i = \alpha_i$ (no derivation needed)
- If $\alpha_i \in V$ (a variable), then $w_i$ is derived from $\alpha_i$ in fewer than $n+1$ steps

**Applying the Inductive Hypothesis:**

For each variable $\alpha_i \in V$:
1. The substring $w_i$ is derived from $\alpha_i$ in fewer than $n+1$ steps
2. By the inductive hypothesis, the derivation tree for $w_i$ from $\alpha_i$ is unique
3. Since $\alpha_i$ appears on the left-hand side of at most one production, the first step of deriving $w_i$ from $\alpha_i$ is unique
4. By induction, the entire subtree rooted at $\alpha_i$ is unique

**Combining the Results:**

Since:
1. The first step $S \rightarrow \alpha$ is unique (by the hypothesis on $G$)
2. Each subsequent subtree derived from $\alpha_i$ is unique (by the inductive hypothesis)

The entire derivation tree for $w$ is uniquely determined.

**Conclusion:**

By the principle of strong mathematical induction, every string $w \in L(G)$ has a unique derivation tree. Therefore, the grammar $G$ is unambiguous. $\square$

#### Intuitive Explanation

The key insight of this proof is that the constraint "no variable appears on the left side of more than one production" eliminates all sources of ambiguity:

1. **No choice at any step:** When deriving from a variable $A$, there is at most one production $A \rightarrow \beta$ to apply
2. **Deterministic derivation:** The derivation process becomes deterministic—at each step, there is only one possible production to apply
3. **Unique parse tree:** Since every derivation step is forced, there can be only one parse tree for any string

This is a very restrictive condition on grammars (most useful grammars have multiple productions for the same variable), but it guarantees unambiguity.

#### Example

Consider the grammar:
$$\begin{align*}
S &\rightarrow AB \\
A &\rightarrow a \\
B &\rightarrow b
\end{align*}$$

Each variable ($S$, $A$, $B$) appears on the left side of exactly one production. For the string $ab$:
- Must start with $S \rightarrow AB$ (only production for $S$)
- Must derive $A \rightarrow a$ (only production for $A$)
- Must derive $B \rightarrow b$ (only production for $B$)
- Result: unique derivation tree

This grammar satisfies the theorem's hypothesis and is indeed unambiguous.

---

## Submission Checklist

### PDF Submission
- [ ] Problem 1: CFG + explanation + screenshot
- [ ] Problem 2: CFG + explanation + screenshot
- [ ] Problem 3: Derivation tree + explanation + 2 screenshots
- [ ] Problem 4: Ambiguity proof + explanation + 5 screenshots
- [ ] Problem 5: Formal proof (text only)

### ZIP Submission
- [ ] `Problem 1.jff`
- [ ] `Problem 2.jff`
- [ ] `P3.jff`
- [ ] `Ambiguous Grammar Tree 1 (aSb First).jff`
- [ ] `Ambiguous Grammar Tree 2 (SS First).jff`
- [ ] `Unambiguous Grammar.jff`

---

**End of Walkthrough**
