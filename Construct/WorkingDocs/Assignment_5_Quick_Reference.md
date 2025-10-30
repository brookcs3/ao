# Assignment 5 Quick Reference Guide

## Assignment Overview
- **Topic**: Context-Free Grammars, Parsing, and Ambiguity
- **Due Date**: Wednesday, Oct 31 by 11:59pm
- **Total Points**: 60 (12 points per problem)
- **Course Learning Outcomes**: CLOs 4-5

## Problems Summary

### Section 5.1 Problems (CFG Construction)
1. **Problem 1**: Create CFG for L = {a^n b^m : 2n ≤ m ≤ 3n}
2. **Problem 2**: Create CFG for L = {w ∈ {a, b}* : n_a(w) = 2n_b(w)}

### Section 5.2 Problems (Parsing and Ambiguity)
3. **Problem 3**: Derivation tree for (a + b) * c + d using modified Example 5.12 grammar
4. **Problem 4**: Prove S → aSb|SS|ε is ambiguous but language not inherently ambiguous
5. **Problem 5**: Prove that grammars with unique left-side variables are unambiguous

## Submission Requirements

### Two Files Required:
1. **PDF File**:
   - All written explanations
   - Test case screenshots (showing Accept/Reject)
   - Screenshots must include the automaton/grammar
   - Use JFLAP's Input/Multiple Run for test cases

2. **ZIP File**:
   - All JFLAP .jff files
   - Do not use RAR format
   - Only needed if automata/grammars are created

## Key Resources
- **Section 5.1 Reading**: Context-free grammars basics
- **Section 5.2 Reading**: Parsing and ambiguity
- **Practice Exercises**: Similar problems for reference
- **Figures**: fig5.4.png, fig5.5.png, fig5.6.png for visual reference

## JFLAP Tips for CFGs
- Use Grammar mode for Problems 1-2
- Use Parse Tree feature for Problem 3
- Use Brute Force Parse for ambiguity demonstration (Problem 4)
- Test with both accepting and rejecting strings
- Include edge cases in test suites

## Grading Rubric Per Problem
- **12-11 pts**: Correct and complete solution
- **11-7 pts**: Nearly complete (minor errors)
- **7-0 pts**: Shows understanding but major issues
- **0 pts**: Not attempted