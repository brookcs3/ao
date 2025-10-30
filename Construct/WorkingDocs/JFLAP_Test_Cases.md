# JFLAP Test Cases for Assignment 5

## Problem 1: CFG for L = {a^n b^m : 2n ≤ m ≤ 3n}

**JFLAP File:** Problem1_CFG.jff

### Test Cases to Run in JFLAP:

**ACCEPT (Strings in the language):**
1. `` (empty string) - 0 a's, 0 b's → 2(0) ≤ 0 ≤ 3(0) ✓
2. `abb` - 1 a, 2 b's → 2(1) ≤ 2 ≤ 3(1) ✓
3. `abbb` - 1 a, 3 b's → 2(1) ≤ 3 ≤ 3(1) ✓
4. `aabbbb` - 2 a's, 4 b's → 2(2) ≤ 4 ≤ 3(2) ✓
5. `aabbbbb` - 2 a's, 5 b's → 2(2) ≤ 5 ≤ 3(2) ✓
6. `aabbbbbb` - 2 a's, 6 b's → 2(2) ≤ 6 ≤ 3(2) ✓
7. `aaabbbbbbb` - 3 a's, 7 b's → 2(3) ≤ 7 ≤ 3(3) ✓

**REJECT (Strings not in the language):**
1. `a` - 1 a, 0 b's → 2(1) = 2 > 0 ✗
2. `ab` - 1 a, 1 b → 2(1) = 2 > 1 ✗
3. `abbbb` - 1 a, 4 b's → 3(1) = 3 < 4 ✗
4. `aab` - 2 a's, 1 b → 2(2) = 4 > 1 ✗
5. `aabb` - 2 a's, 2 b's → 2(2) = 4 > 2 ✗
6. `aabbb` - 2 a's, 3 b's → 2(2) = 4 > 3 ✗
7. `ba` - Not in a^n b^m form ✗
8. `aaabbbb` - 3 a's, 4 b's → 2(3) = 6 > 4 ✗

---

## Problem 2: CFG for L = {w ∈ {a,b}* : n_a(w) = 2n_b(w)}

**JFLAP File:** Problem2_CFG.jff

### Test Cases to Run in JFLAP:

**ACCEPT (Strings in the language):**
1. `` (empty string) - 0 a's, 0 b's → 0 = 2(0) ✓
2. `aab` - 2 a's, 1 b → 2 = 2(1) ✓
3. `aba` - 2 a's, 1 b → 2 = 2(1) ✓
4. `baa` - 2 a's, 1 b → 2 = 2(1) ✓
5. `aabaab` - 4 a's, 2 b's → 4 = 2(2) ✓
6. `aabbaa` - 4 a's, 2 b's → 4 = 2(2) ✓
7. `baaaab` - 4 a's, 2 b's → 4 = 2(2) ✓
8. `aabaabaab` - 6 a's, 3 b's → 6 = 2(3) ✓

**REJECT (Strings not in the language):**
1. `a` - 1 a, 0 b's → 1 ≠ 2(0) ✗
2. `aa` - 2 a's, 0 b's → 2 ≠ 2(0) ✗
3. `b` - 0 a's, 1 b → 0 ≠ 2(1) ✗
4. `ab` - 1 a, 1 b → 1 ≠ 2(1) ✗
5. `aabb` - 2 a's, 2 b's → 2 ≠ 2(2) ✗
6. `aaab` - 3 a's, 1 b → 3 ≠ 2(1) ✗
7. `abab` - 2 a's, 2 b's → 2 ≠ 2(2) ✗
8. `aaabbb` - 3 a's, 3 b's → 3 ≠ 2(3) ✗

---

## Problem 3: Expression Grammar (Example 5.12)

**JFLAP File:** Problem3_Expression_Grammar.jff

### Test Cases to Run in JFLAP:

**ACCEPT (Valid expressions):**
1. `a` - Single variable
2. `a+b` - Simple addition
3. `a*b` - Simple multiplication
4. `(a+b)*c` - Parenthesized addition times c
5. `(a+b)*c+d` - The target expression from the problem
6. `a+b+c` - Multiple additions
7. `a*b*c` - Multiple multiplications
8. `(a)` - Parenthesized single variable
9. `((a+b))*c` - Nested parentheses
10. `a+b*c` - Mixed operators (multiplication has precedence)

**REJECT (Invalid expressions):**
1. `+a` - Starting with operator
2. `a+` - Ending with operator
3. `a++b` - Double operator
4. `(a+b` - Unmatched left parenthesis
5. `a+b)` - Unmatched right parenthesis
6. `()` - Empty parentheses
7. `a b` - Space between variables
8. `*` - Just an operator
9. `e` - Variable not in {a,b,c,d}
10. `ab` - Two variables without operator

---

## Problem 4: Ambiguous Grammar

**JFLAP File:** Problem4_Ambiguous_Grammar.jff (Ambiguous version)
**JFLAP File:** Problem4_Unambiguous_Grammar.jff (Unambiguous version)

### Test Cases for AMBIGUOUS Grammar (S → aSb | SS | λ):

**ACCEPT (Strings in the language):**
1. `` (empty string) - Balanced
2. `ab` - One pair
3. `aabb` - Two pairs (SHOWS AMBIGUITY - multiple parse trees!)
4. `aaabbb` - Three pairs
5. `abab` - Interleaved pairs
6. `aabbab` - Mixed structure
7. `ababab` - Alternating structure
8. `aaaabbbb` - Four pairs

**REJECT (Strings not in the language):**
1. `a` - Unbalanced (more a's)
2. `b` - Unbalanced (more b's)
3. `aab` - Unbalanced (more a's)
4. `abb` - Unbalanced (more b's)
5. `ba` - Wrong order (b before a at start)
6. `aabbb` - Unbalanced (more b's)
7. `aaabb` - Unbalanced (more a's)
8. `abba` - Invalid nesting

### Test Cases for UNAMBIGUOUS Grammar (S → aSbS | λ):

**Same ACCEPT/REJECT lists as above** - The unambiguous grammar generates the same language but with unique parse trees for each string.

---

## Problem 5: Theoretical Proof

**No JFLAP file needed** - This is a theoretical proof question about unambiguous grammars.

---

## Testing Instructions for JFLAP:

1. **Open JFLAP** and load the appropriate .jff file
2. Go to **Input → Multiple Run** to test multiple strings at once
3. Enter all test strings (both ACCEPT and REJECT lists)
4. Click **Run** to see which strings are accepted/rejected
5. **Take a screenshot** that shows:
   - The grammar productions
   - The test input strings
   - The accept/reject results for each string

### Important Notes:

- When taking screenshots, ensure the grammar is visible in the same window as the test results
- Use the "Multiple Run" feature to get all tests in one screenshot
- Group your test cases logically (e.g., all accepts together, then all rejects)
- Make sure the screenshot is clear and readable
- For Problem 4, test the string "aabb" in both grammars to demonstrate the ambiguity difference