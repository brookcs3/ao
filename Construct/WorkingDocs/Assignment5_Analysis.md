# Assignment 5 Analysis - Context-Free Grammars

## Problem 1: CFG for L = {a^n b^m : 2n ≤ m ≤ 3n}

### Analysis:
- For each 'a' we generate, we need between 2 and 3 'b's
- The minimum is 2 b's per a, the maximum is 3 b's per a
- Strategy: Generate a's and ensure each a produces at least 2 b's, with optional third b

### Grammar Design:
We can think of this as generating n a's and then generating b's in the range [2n, 3n].
One approach:
- First generate n a's
- For each a, mandatorily generate 2 b's
- Optionally generate up to n additional b's (to reach 3n total)

### CFG Productions:
```
S → aSBB | ε
B → b
S → aSBBB | aSBB | ε
```

Better approach - generate a's with corresponding b's:
```
S → aSBB | aS BBB | ε
B → b
```

Most elegant approach:
```
S → aSbb | aSbbb | ε
```

This generates one 'a' at a time, and for each 'a', it generates either 2 or 3 'b's.

## Problem 2: CFG for L = {w ∈ {a,b}* : n_a(w) = 2n_b(w)}

### Analysis:
- The number of a's must be exactly twice the number of b's
- For every b, we need exactly 2 a's
- Order doesn't matter - a's and b's can be interspersed

### Grammar Design:
Strategy: For every b we generate, we must generate exactly 2 a's, but they can appear in any order.

### CFG Productions:
```
S → SS | aSa | aS | Sa | bSaa | abSa | aaSb | baS | abS | Sba | ε
```

Better approach - think of it as generating units where each unit has 2 a's and 1 b:
```
S → SaaSb | SaSab | SaSba | SbSaa | SabSa | SbaSa |
    aSaSb | aSbSa | bSaSa | aaSb | aSab | aSba |
    baSa | abSa | baS | ε
```

Most elegant:
```
S → SS | aSaSb | aSbSa | bSaSa | ε
```

This allows generating the symbols in any order while maintaining the 2:1 ratio.

## Problem 3: Derivation Tree for (a+b)*c+d

### Grammar from Example 5.12:
```
E → T | E + T
T → F | T * F
F → I | (E)
I → a | b | c | d
```

### Parsing (a+b)*c+d:
The expression should be parsed as ((a+b)*c)+d based on precedence rules.

Leftmost derivation:
1. E
2. E + T  (using E → E + T)
3. T + T  (using E → T)
4. T * F + T  (using T → T * F)
5. F * F + T  (using T → F)
6. (E) * F + T  (using F → (E))
7. (E + T) * F + T  (using E → E + T)
8. (T + T) * F + T  (using E → T)
9. (F + T) * F + T  (using T → F)
10. (I + T) * F + T  (using F → I)
11. (a + T) * F + T  (using I → a)
12. (a + F) * F + T  (using T → F)
13. (a + I) * F + T  (using F → I)
14. (a + b) * F + T  (using I → b)
15. (a + b) * I + T  (using F → I)
16. (a + b) * c + T  (using I → c)
17. (a + b) * c + F  (using T → F)
18. (a + b) * c + I  (using F → I)
19. (a + b) * c + d  (using I → d)

## Problem 4: Ambiguity Proof for S → aSb | SS | λ

### Part A: Show the grammar is ambiguous
Need to find a string with two different derivation trees.

Example string: aabb

First derivation:
S ⇒ aSb ⇒ aaSbb ⇒ aabb

Second derivation:
S ⇒ SS ⇒ aSbS ⇒ aaSbbS ⇒ aabbS ⇒ aabb

These give different parse trees, proving ambiguity.

### Part B: Show the language is not inherently ambiguous
The language generated is L = {w ∈ {a,b}* : n_a(w) = n_b(w) and for any prefix v of w, n_a(v) ≥ n_b(v)}

An unambiguous grammar for the same language:
```
S → aSbS | ε
```

This generates the same language but is unambiguous because at each step we can only apply one production based on whether we want to continue generating (aSbS) or stop (ε).

## Problem 5: Proof that unique-production grammars are unambiguous

### Theorem Statement:
If G is a context-free grammar in which no variable occurs on the left side of more than one production, then G is unambiguous.

### Proof:
By contradiction. Assume G has the property that each variable appears on the left side of at most one production, but G is ambiguous.

If G is ambiguous, then there exists some string w ∈ L(G) with two distinct leftmost derivations (and hence two distinct parse trees).

Let the two leftmost derivations be:
- D1: S ⇒ α₁ ⇒ α₂ ⇒ ... ⇒ w
- D2: S ⇒ β₁ ⇒ β₂ ⇒ ... ⇒ w

Since both derivations start from S and S appears on the left of exactly one production (by hypothesis), the first step must be the same in both derivations. That is, α₁ = β₁.

Now consider the leftmost variable in α₁ = β₁. Since this variable appears on the left of exactly one production, the next step in both derivations must also be the same. Therefore α₂ = β₂.

By induction, we can show that αᵢ = βᵢ for all i, which means the two derivations are identical. This contradicts our assumption that they are distinct.

Therefore, G must be unambiguous. QED.