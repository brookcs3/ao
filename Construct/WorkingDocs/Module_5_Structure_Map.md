# Module 5 - Structure Map

## Visual Directory Tree

```
Modue 5/
│
├── Module 5 - Overview.md ────────────┐ (Entry Point)
│                                      │
├── Module 5 - Exploration.md ────────┤ (Study Materials)
│                                      │
├── Assignment 5.md ──────────────────┘ (Assignment Instructions)
│
├── Section 5-1/ ─────────────────────┐ (Context-Free Grammars)
│   └── 5.1.txt                       │
│                                      │
├── Section 5-2/ ─────────────────────┤ (Parsing & Ambiguity)
│   ├── 5.2.txt                       │
│   ├── fig5.4.png                    │
│   ├── fig5.5.png                    │
│   └── fig5.6.png                    │
│                                      │
├── Construct/ ───────────────────────┤ (Deliverables Folder)
│   ├── WorkingDocs/ ─────────────────┤ (Analysis & Work)
│   │   ├── Module_5_Validation_Report.md
│   │   ├── Quick_Start_Guide.md
│   │   ├── Module_5_Structure_Map.md (THIS FILE)
│   │   └── [Agent outputs will go here]
│   │
│   └── [Final PDF will go here] ─────┘
│
├── Practice exercises.txt
├── Preactice Exercise answer.txt
└── [Other exploration files...]
```

---

## Navigation Flow

```
START HERE
    |
    v
Module 5 - Overview.md
    |
    +---> "What is this module about?"
    |     Answer: Context-Free Grammars, Parsing, Ambiguity
    |
    +---> "What will I learn?"
    |     Answer: Construct CFGs, analyze ambiguity
    |
    v
Module 5 - Exploration.md
    |
    +---> Section 5-1: Context-Free Grammars
    |     File: Section 5-1/5.1.txt
    |     Topics: CFG definitions, examples, language generation
    |
    +---> Section 5-2: Parsing and Ambiguity
    |     File: Section 5-2/5.2.txt
    |     Figures: fig5.4.png, fig5.5.png, fig5.6.png
    |     Topics: Parsing algorithms, ambiguous grammars, inherent ambiguity
    |
    v
Assignment 5.md
    |
    +---> Problem 1: CFG for {a^n b^m : 2n <= m <= 3n}
    +---> Problem 2: CFG for {w : n_a(w) = 2n_b(w)}
    +---> Problem 3: Derivation tree for (a+b)*c+d
    +---> Problem 4: Ambiguity proof (grammar vs. language)
    +---> Problem 5: Theoretical proof (single-production → unambiguous)
    |
    v
AGENT WORKFLOW
    |
    +---> jflap-automata-builder-midcourse
    |     Input: Assignment 5.md
    |     Output: WorkingDocs/[analysis files]
    |
    v
    +---> interactive-pdf-compiler-midcourse
    |     Input: WorkingDocs/[analysis files]
    |     Output: Construct/Assignment_5_Solution.pdf
    |
    v
SUBMIT PDF
```

---

## Assignment Problem Map

### Problem 1: CFG Construction
```
Language: L = {a^n b^m : 2n <= m <= 3n}
├── Constraint 1: m >= 2n (at least twice as many b's as a's)
├── Constraint 2: m <= 3n (at most three times as many b's as a's)
└── Solution approach: Construct CFG with productions that enforce both constraints

Agent: jflap-automata-builder-midcourse (CFG construction)
Output: Problem_1_CFG_Analysis.md
```

### Problem 2: CFG Construction
```
Language: L = {w in {a,b}* : n_a(w) = 2n_b(w)}
├── Constraint: Exactly twice as many a's as b's
├── Challenge: a's and b's can be interleaved arbitrarily
└── Solution approach: Construct CFG that maintains 2:1 ratio with flexible ordering

Agent: jflap-automata-builder-midcourse (CFG construction)
Output: Problem_2_CFG_Analysis.md
```

### Problem 3: Derivation Tree
```
Expression: (a + b) * c + d
├── Grammar: Example 5.12 with I -> a|b|c|d
├── Goal: Show parse tree demonstrating operator precedence
└── Solution approach: Build tree from root (start symbol) to leaves (terminals)

Agent: jflap-automata-builder-midcourse (Derivation tree generation)
Output: Problem_3_Derivation_Tree.md
```

### Problem 4: Ambiguity Proof
```
Grammar: S -> aSb | SS | ε
├── Part A: Prove grammar is ambiguous
│   └── Find string with multiple parse trees
├── Part B: Prove language is NOT inherently ambiguous
│   └── Construct unambiguous grammar generating same language
└── Solution approach: Find ambiguous string, then create alternative grammar

Agent: jflap-automata-builder-midcourse (Ambiguity analysis)
Output: Problem_4_Ambiguity_Proof.md
```

### Problem 5: Theoretical Proof
```
Statement: If no variable has multiple productions, then grammar is unambiguous
├── Proof type: Direct proof or proof by contradiction
├── Key insight: Single production per variable → unique derivation path
└── Solution approach: Formal mathematical proof with clear logic

Agent: jflap-automata-builder-midcourse (Theoretical proof)
Output: Problem_5_Theoretical_Proof.md
```

---

## File Path Quick Reference

### Entry Points
```
Overview:    C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Module 5 - Overview.md
Exploration: C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Module 5 - Exploration.md
Assignment:  C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Assignment 5.md
```

### Study Materials
```
Section 5.1: C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Section 5-1\5.1.txt
Section 5.2: C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Section 5-2\5.2.txt
```

### Work Areas
```
Working:     C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\WorkingDocs\
Final PDF:   C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\
```

---

## Validation Status

| Component | Status | Notes |
|-----------|--------|-------|
| Module folder | READY | Located at .../Modue 5/ |
| Overview MD | CREATED | Entry point with navigation |
| Exploration MD | CREATED | Links to all sections |
| Assignment MD | CREATED | 5 problems clearly defined |
| Section 5-1 | ORGANIZED | Contains 5.1.txt |
| Section 5-2 | ORGANIZED | Contains 5.2.txt + figures |
| Construct/ | CREATED | Ready for deliverables |
| WorkingDocs/ | CREATED | Ready for analysis |
| Navigation links | VERIFIED | All absolute paths functional |
| Agent readiness | CONFIRMED | Ready for midcourse agents |

---

## Agent Execution Plan

### Phase 1: Content Analysis and Solution
**Agent:** jflap-automata-builder-midcourse
**Input:** Assignment 5.md
**Actions:**
1. Analyze Problem 1 → Generate CFG → Save to WorkingDocs/
2. Analyze Problem 2 → Generate CFG → Save to WorkingDocs/
3. Analyze Problem 3 → Generate derivation tree → Save to WorkingDocs/
4. Analyze Problem 4 → Create ambiguity proof → Save to WorkingDocs/
5. Analyze Problem 5 → Write theoretical proof → Save to WorkingDocs/

### Phase 2: PDF Compilation
**Agent:** interactive-pdf-compiler-midcourse
**Input:** WorkingDocs/[all analysis files]
**Actions:**
1. Read all working documents
2. Format CFGs with proper notation
3. Render derivation trees visually
4. Format proofs with LaTeX
5. Compile final PDF → Save to Construct/

---

## Key Concepts by Section

### Section 5.1: Context-Free Grammars
- Definition of CFG (V, T, S, P)
- Productions: A → x where A ∈ V, x ∈ (V ∪ T)*
- Derivations and sentential forms
- Language generation: L(G)
- Examples: {a^n b^n}, {ww^R}, non-regular languages

### Section 5.2: Parsing and Ambiguity
- Parsing: Finding derivation sequence
- Membership algorithms
- Exhaustive search parsing
- Leftmost and rightmost derivations
- Derivation trees (parse trees)
- Ambiguous grammars: Multiple derivation trees for same string
- Inherently ambiguous languages: No unambiguous grammar exists

---

## Expected Deliverable

**File:** Assignment_5_Solution.pdf
**Location:** C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\

**Contents:**
- Problem 1 solution with CFG productions
- Problem 2 solution with CFG productions
- Problem 3 solution with derivation tree diagram
- Problem 4 solution with:
  - Proof of grammar ambiguity (multiple parse trees)
  - Proof that language is not inherently ambiguous (alternative grammar)
- Problem 5 solution with formal theoretical proof

**Due Date:** October 31, 2025 at 11:59pm

---

## Summary

Module 5 is VALIDATED and READY for the jflap-automata-builder-midcourse agent.

All infrastructure is in place:
- Navigation structure complete
- Section materials organized
- Work directories created
- Assignment clearly defined
- Agent workflow planned

**Next Action:** Run jflap-automata-builder-midcourse on Assignment 5.md

---

Generated: 2025-10-30
Validator: module-infrastructure-validator-midcourse
Status: COMPLETE
