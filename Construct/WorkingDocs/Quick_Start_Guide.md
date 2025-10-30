# Module 5 - Quick Start Guide

## Assignment 5 Overview

**Due:** Wednesday, Oct 31 at 11:59pm
**Points:** 60 points
**Focus:** Context-Free Grammars, Derivation Trees, and Ambiguity Proofs

---

## Problems at a Glance

1. **Problem 1:** CFG for L = {a^n b^m : 2n <= m <= 3n}
2. **Problem 2:** CFG for L = {w in {a,b}* : n_a(w) = 2n_b(w)}
3. **Problem 3:** Derivation tree for (a + b) * c + d
4. **Problem 4:** Prove grammar is ambiguous, language is not inherently ambiguous
5. **Problem 5:** Prove single-production grammars are unambiguous

---

## File Locations

### Key Module Files
- **Module Overview:** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Module 5 - Overview.md`
- **Exploration:** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Module 5 - Exploration.md`
- **Assignment:** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Assignment 5.md`

### Course Materials
- **Section 5.1 (CFGs):** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Section 5-1\5.1.txt`
- **Section 5.2 (Parsing):** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Section 5-2\5.2.txt`
- **Figures:** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Section 5-2\fig5.4.png` (+ fig5.5, fig5.6)

### Working Directories
- **Deliverables:** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`
- **Analysis/Work:** `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\WorkingDocs\`

---

## Recommended Workflow

### Step 1: Study Phase
1. Read Section 5.1 (Context-Free Grammars)
2. Read Section 5.2 (Parsing and Ambiguity)
3. Review practice exercises and answers
4. Study figures 5.4, 5.5, 5.6

### Step 2: Agent Execution Phase

#### Run jflap-automata-builder-midcourse
```
Point agent at: C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Assignment 5.md
```

**What this agent will do:**
- Analyze all 5 assignment problems
- Construct CFGs for Problems 1 and 2
- Generate derivation tree for Problem 3
- Create ambiguity proof with multiple parse trees for Problem 4
- Write formal proof for Problem 5
- Save all work to WorkingDocs/

**Expected outputs in WorkingDocs:**
- `Problem_1_CFG_Analysis.md`
- `Problem_2_CFG_Analysis.md`
- `Problem_3_Derivation_Tree.md`
- `Problem_4_Ambiguity_Proof.md`
- `Problem_5_Theoretical_Proof.md`

#### Run interactive-pdf-compiler-midcourse
```
After jflap-automata-builder-midcourse completes
```

**What this agent will do:**
- Compile all solutions into a single PDF
- Format CFG productions professionally
- Render derivation trees
- Format proofs with proper mathematical notation
- Integrate test case screenshots
- Save final PDF to Construct/

**Expected output:**
- `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Assignment_5_Solution.pdf`

### Step 3: Review and Submit
1. Review `Assignment_5_Solution.pdf` in Construct/
2. Verify all 5 problems are complete
3. Check all proofs and derivations
4. Submit PDF before deadline (Oct 31, 11:59pm)

---

## Agent Summary

### jflap-automata-builder-midcourse (PRIMARY)
- **Handles:** CFG construction, derivation trees, ambiguity proofs, theoretical proofs
- **Input:** Assignment 5.md
- **Output:** Working documents with complete solutions

### interactive-pdf-compiler-midcourse (SECONDARY)
- **Handles:** LaTeX compilation, professional formatting, PDF generation
- **Input:** Working documents from jflap-automata-builder-midcourse
- **Output:** Assignment_5_Solution.pdf

---

## Important Notes

1. **This is a Module 5+ (midcourse) assignment** - Use the `-midcourse` agent variants
2. **No JFLAP files needed** - This assignment is pure CFG/proof work (despite the submission instructions mentioning JFLAP)
3. **Focus areas:**
   - CFG construction techniques
   - Derivation tree visualization
   - Ambiguity vs. inherent ambiguity
   - Formal proof writing
4. **Deadline:** Oct 31 at 11:59pm

---

## Questions?

Refer to:
- Full validation report: `Module_5_Validation_Report.md` (this folder)
- Assignment details: `../Assignment 5.md`
- Course materials: `../Section 5-1/` and `../Section 5-2/`

---

**Status:** Module 5 infrastructure is VALIDATED and READY
**Next Step:** Run jflap-automata-builder-midcourse on Assignment 5.md
