# Assignment 5 - Context-Free Grammars Analysis

## Assignment Metadata
- **Assignment Title:** Assignment 5 - Context-Free Grammars, Parsing, and Ambiguity
- **Due Date:** Wednesday by 11:59pm
- **Total Points:** 60 (12 points per problem)
- **Module Directory:** C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5
- **Construct Folder:** C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct
- **WorkingDocs Folder:** C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\WorkingDocs

## Submission Requirements
- **Part 1:** Single PDF file with all written explanations, CFG productions, derivation trees, and proofs
- **Part 2:** ZIP file with JFLAP files (NOT NEEDED - this assignment has no automata questions)

## Context Review

### Key Concepts from Section 5.1
1. **Context-Free Grammar (CFG):** G = (V, T, S, P) where productions are A → x, A ∈ V, x ∈ (V ∪ T)*
2. **Derivation Trees:** Show structure of derivation independent of order
3. **Leftmost/Rightmost Derivations:** Specific orders for applying productions

### Key Concepts from Section 5.2
1. **Parsing:** Finding sequence of productions to derive a string
2. **Ambiguity:** Grammar is ambiguous if some string has multiple distinct derivation trees
3. **Inherently Ambiguous Language:** Language for which every grammar is ambiguous
4. **s-grammar:** Productions of form A → ax where (A,a) occurs at most once

### Relevant Examples from Textbook
- **Example 5.3:** L = {a^n b^m : n ≠ m} - shows how to handle inequality constraints
- **Example 5.4:** L = {w : n_a(w) = n_b(w), prefix condition} - balanced parentheses grammar
- **Example 5.10:** Shows ambiguity with multiple derivation trees for "aabb"
- **Example 5.12:** Unambiguous arithmetic expression grammar with precedence
- **Exercise 9(d) Section 5.1:** L = {a^n b^m : 2n ≤ m ≤ 3n} - DIRECTLY RELEVANT to Problem 1
- **Exercise 9(g) Section 5.1:** L = {w : n_a(w) = 2n_b(w) + 1} - Similar to Problem 2

## Problem Analysis

### Problem 1: CFG for L = {a^n b^m : 2n ≤ m ≤ 3n}
**Type:** CFG Construction
**Challenge:** Handle double inequality constraint on a's and b's

**Approach:**
- Constraint: 2n ≤ m ≤ 3n means for every 'a', need between 2 and 3 'b's
- Break into cases: generate minimum (2b per a), then add extra b's (up to 1 more per a)
- Strategy: Generate a's and 2b's together (balanced), then add extra b's

**Solution Strategy:**
- First generate pairs: each 'a' with exactly 2 'b's → ensures 2n ≤ m
- Then allow adding up to n more 'b's → ensures m ≤ 3n
- Need two parts: S₁ generates a^n b^(2n), then add up to n more b's

### Problem 2: CFG for L = {w ∈ {a,b}* : n_a(w) = 2n_b(w)}
**Type:** CFG Construction
**Challenge:** For every 'b', need exactly 2 'a's (order doesn't matter)

**Approach:**
- Ratio constraint: 2 a's for every 1 b
- Can interleave in any order: "aab", "aba", "baa" all valid
- Similar to Example 5.4 but with 2:1 ratio instead of 1:1

**Solution Strategy:**
- Option 1: Generate combinations that maintain 2:1 ratio
- Option 2: Use recursive structure - place 'b' and 2 'a's anywhere, recursively
- Think: S → aaS b | aS a b | S aa b | ... (all orderings of "aa" and "b" with recursive S)

### Problem 3: Derivation Tree for (a + b) * c + d
**Type:** Derivation Tree Construction
**Grammar:** Example 5.12 with I → a|b|c|d

**Given Grammar Productions:**
- E → T | E + T
- T → F | T * F
- F → I | (E)
- I → a | b | c | d

**String to derive:** (a + b) * c + d

**Analysis:**
- Parse according to precedence: * before +
- Parentheses force grouping
- Structure: ((a + b) * c) + d
- Root E, splits into E + T where E derives (a+b)*c and T derives d

### Problem 4: Ambiguity Proof
**Type:** Two-part proof
**Grammar:** S → aSb | SS | λ

**Part A - Prove Grammar is Ambiguous:**
- Find a string with two distinct derivation trees
- Example from textbook: "aabb" has two trees (Figure 5.4)
- Tree 1: S ⇒ SS ⇒ aSb S ⇒ aaSbb S ⇒ aabb λ ⇒ aabb
- Tree 2: S ⇒ aSb ⇒ aSSb ⇒ aaSbb ⇒ aabb

**Part B - Prove Language is NOT Inherently Ambiguous:**
- Must find equivalent unambiguous grammar
- Language: {w : n_a(w) = n_b(w), prefix condition satisfied}
- Unambiguous version: eliminate SS production, force specific structure

### Problem 5: Theoretical Proof
**Type:** Formal proof
**Statement:** If G is a CFG where no variable occurs on left side of more than one production, then G is unambiguous

**Proof Strategy:**
- Proof by contradiction or direct proof
- Key insight: Each variable has unique production rule
- At any derivation step, only ONE choice for replacing each variable
- Therefore, only ONE possible derivation tree exists
- Referenced in textbook Section 5.2, Exercise 24

## Notation Standards
- Productions: A → x (use → symbol)
- Lambda (empty string): λ
- Alternative operator: |
- Variables: Capital letters (S, A, B, etc.)
- Terminals: Lowercase letters (a, b, c, etc.)

## Next Steps
1. Solve Problem 1 - CFG construction
2. Solve Problem 2 - CFG construction
3. Solve Problem 3 - Draw derivation tree (generate LaTeX code)
4. Solve Problem 4 - Ambiguity proof (two parts)
5. Solve Problem 5 - Theoretical proof
6. Create comprehensive walkthrough for PDF compiler agent
