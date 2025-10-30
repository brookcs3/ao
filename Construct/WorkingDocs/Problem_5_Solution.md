# Problem 5 Solution: Unambiguous Single-Production Grammars

## Problem Statement
Prove that if G is a context-free grammar in which no variable occurs on the left side of more than one production, then G is unambiguous.

## Formal Statement

**Theorem:** Let G = (V, T, S, P) be a context-free grammar such that for every variable A ∈ V, there is at most one production with A on the left-hand side. Then G is unambiguous.

## Proof

### Strategy
We will prove this by contradiction. We assume that G is ambiguous and derive a contradiction.

Alternatively, we can prove it directly by showing that every string has a unique derivation tree.

I'll use the **direct proof** approach.

### Direct Proof

**Claim:** Every string w ∈ L(G) has exactly one derivation tree.

**Proof by strong induction** on the structure of derivation trees:

#### Base Case
Consider the smallest possible derivation tree (height 1):
- The tree has root S and leaves that are all terminals
- This corresponds to a single production S → w where w ∈ T*
- Since S has at most one production, this derivation tree is unique ✓

#### Inductive Hypothesis
Assume that for all partial derivation trees with root A and yield v, where the height is at most h, the partial derivation tree is uniquely determined.

#### Inductive Step
Consider a derivation tree with root S and yield w, where the tree has height h + 1.

**Case Analysis:**
- The root is S
- There is at most one production with S on the left side
- Let's say this production is S → α₁α₂...αₙ where each αᵢ ∈ V ∪ T

Since this is the only production for S, the derivation must start with:
```
S ⇒ α₁α₂...αₙ
```

Now, we must derive w from α₁α₂...αₙ.

The string w can be written as w = w₁w₂...wₙ where:
- If αᵢ ∈ T, then wᵢ = αᵢ (exactly the terminal)
- If αᵢ ∈ V, then wᵢ is derived from αᵢ

For each αᵢ ∈ V:
- There is at most one production with αᵢ on the left side
- By the inductive hypothesis, the partial derivation tree with root αᵢ and yield wᵢ is unique

Since:
1. The first production S → α₁α₂...αₙ is uniquely determined (at most one production for S)
2. Each subsequent partial derivation tree is uniquely determined by the inductive hypothesis

The entire derivation tree is **uniquely determined**.

By induction, every string in L(G) has exactly one derivation tree.

Therefore, G is unambiguous. ∎

## Alternative Proof (by Contradiction)

**Assume:** G is ambiguous.

**Then:** There exists some string w ∈ L(G) with two distinct derivation trees T₁ and T₂.

**Analysis:**
- Both T₁ and T₂ have root S
- Since there is at most one production with S on the left side, the first step in both derivation trees must be the same
- Let S → α₁α₂...αₙ be this unique production

Now consider the children of S in both trees:
- Both trees have the same children α₁, α₂, ..., αₙ in the same order
- The yield of the tree can be partitioned as w = w₁w₂...wₙ

Since T₁ ≠ T₂ (they are distinct trees), there must be some position i where the subtree rooted at αᵢ differs between T₁ and T₂.

Let T₁ⁱ and T₂ⁱ be these differing subtrees:
- Both have root αᵢ
- Both have the same yield wᵢ
- But T₁ⁱ ≠ T₂ⁱ (they are structurally different)

This means αᵢ has two different derivation trees for the same string wᵢ.

For this to happen, the first step in these two derivations must differ, which means αᵢ must have two different productions:
- αᵢ → β₁β₂...βₖ (used in T₁ⁱ)
- αᵢ → γ₁γ₂...γₘ (used in T₂ⁱ)

where β₁β₂...βₖ ≠ γ₁γ₂...γₘ.

But this contradicts our assumption that each variable has at most one production!

Therefore, our assumption that G is ambiguous must be false.

Hence, G is unambiguous. ∎

## Formal Write-up for Assignment

**Theorem:** Let G = (V, T, S, P) be a context-free grammar such that each variable A ∈ V appears on the left-hand side of at most one production in P. Then G is unambiguous.

**Proof:**

We prove this by showing that every string w ∈ L(G) has a unique derivation tree.

Let w be an arbitrary string in L(G). We proceed by strong induction on the number of derivation steps required to generate w.

**Base case (n = 1):**
If w is derived in one step, then S → w is a production in P. Since S has at most one production, this derivation is unique.

**Inductive step:**
Assume that for all strings derivable in k or fewer steps (k ≥ 1), the derivation tree is unique.

Consider a string w derived in k + 1 steps. The derivation starts with some production S → α where α = α₁α₂...αₘ and each αᵢ ∈ V ∪ T.

Since S has at most one production, this first step is uniquely determined.

The string w can be partitioned as w = w₁w₂...wₘ where:
- If αᵢ ∈ T, then wᵢ = αᵢ
- If αᵢ ∈ V, then wᵢ is derived from αᵢ in fewer than k + 1 steps

For each αᵢ ∈ V, by the inductive hypothesis, the derivation tree for wᵢ from αᵢ is unique.

Since:
1. The first step is unique (S has at most one production)
2. Each subtree is unique (by inductive hypothesis)

The entire derivation tree for w is unique.

By the principle of mathematical induction, every string in L(G) has a unique derivation tree.

Therefore, G is unambiguous. ∎

## Connection to Textbook

This problem is directly stated as Exercise 24 in Section 5.2 of the textbook:

"Prove the following result. Let G = (V, T, S, P) be a context-free grammar in which every A ∈ V occurs on the left side of at most one production. Then G is unambiguous."

The proof technique used here (induction on derivation tree structure) is a standard approach in formal language theory and follows the patterns established in the textbook's treatment of derivation trees (Theorem 5.1 and related results).

## Key Insight

The fundamental insight is that ambiguity arises from having **choices** during derivation. If each variable has only one production, then at every step of the derivation, there is only one possible production to apply. This eliminates all choices, making the derivation tree unique.

This is a sufficient condition for unambiguity, but **not a necessary condition**. There are many unambiguous grammars where variables have multiple productions (e.g., Example 5.12 in the textbook).
