# JFLAP Screenshot Tutorial for Assignment 5
# Context-Free Grammars and Ambiguity

**CRITICAL INSTRUCTIONS:**
- Follow each step EXACTLY as written
- Do NOT proceed to PDF creation until ALL screenshots are complete
- Save screenshots with the exact filenames specified
- Verify each screenshot is clear and readable before proceeding

---

## Overview

You will be taking 7 screenshots total:
1. **Problem 1:** CFG test results (1 screenshot)
2. **Problem 2:** CFG test results (1 screenshot)
3. **Problem 3:** Expression grammar test results + derivation tree (2 screenshots)
4. **Problem 4:** Ambiguous grammar tests + parse trees + unambiguous grammar tests (3 screenshots)

**All screenshots should be saved to:**
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`

---

## Problem 1: CFG for L = {a^n b^m : 2n ≤ m ≤ 3n}

### JFLAP File to Open:
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem1_CFG.jff`

### Grammar You Should See:
```
S → aSbb
S → aSbbb
S → λ
```

### Step-by-Step Instructions:

**STEP 1: Open the JFLAP File**
- Launch JFLAP application
- Click File → Open
- Navigate to the Construct folder: `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`
- Select `Problem1_CFG.jff`
- Click Open
- You should see a window showing the grammar productions

**STEP 2: Verify the Grammar**
- Confirm you see exactly 3 productions:
  * S → aSbb
  * S → aSbbb
  * S → λ (lambda/empty string)
- If the grammar looks different, STOP and notify me

**STEP 3: Open Multiple Run Interface**
- Click on "Input" in the menu bar
- Select "Multiple Run" from the dropdown

**STEP 4: Enter Test Strings**

**Accept Strings (should be ACCEPTED):**
- `` (empty string - leave blank and press Enter)
- `abb`
- `abbb`
- `aabbbb`
- `aabbbbb`
- `aabbbbbb`
- `aaabbbbbbb`

**Reject Strings (should be REJECTED):**
- `a`
- `ab`
- `abbbb`
- `aab`
- `aabb`
- `aabbb`
- `ba`
- `aaabbbb`

**How to Enter:**
- Type each string into the "Input" field
- Press Enter after each string
- You should see each string appear in the list
- Total: 15 test strings (7 Accept + 8 Reject)

**STEP 5: Run All Tests**
- After entering all 15 strings, click "Run Inputs" button
- Wait for JFLAP to process all strings
- Each string should now show either "Accept" or "Reject" in the results

**STEP 6: Verify Results**
- Check that all 7 Accept strings show "Accept"
- Check that all 8 Reject strings show "Reject"
- If any results are unexpected, STOP and notify me

**STEP 7: Arrange Window for Screenshot**
- Make sure BOTH are visible:
  1. The grammar productions (in the main grammar window)
  2. The Multiple Run test results (showing all strings with Accept/Reject)
- You may need to resize or reposition windows
- The goal: capture BOTH grammar AND test results in ONE screenshot

**STEP 8: Take Screenshot**
- Use your preferred screenshot tool (Snipping Tool, Print Screen, etc.)
- Capture the entire JFLAP window showing:
  * Grammar productions at top
  * All test strings with results below
- Save the screenshot as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem1_JFLAP_Tests.png`**

**STEP 9: Verify Screenshot**
- Open the saved PNG file
- Confirm both grammar and test results are clearly visible
- Confirm text is readable
- If blurry or incomplete, retake the screenshot

**STEP 10: Report Back**
Once complete, provide me with:
- Confirmation that screenshot was saved successfully
- The full path to the screenshot file
- Any issues or unexpected results

---

## Problem 2: CFG for L = {w ∈ {a,b}* : n_a(w) = 2n_b(w)}

### JFLAP File to Open:
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem2_CFG.jff`

### Grammar You Should See:
```
S → aabS
S → abaS
S → baaS
S → SS
S → λ
```

### Step-by-Step Instructions:

**STEP 1: Open the JFLAP File**
- If Problem 1 window is still open, you can leave it
- Click File → Open (or open a new JFLAP instance)
- Navigate to: `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`
- Select `Problem2_CFG.jff`
- Click Open

**STEP 2: Verify the Grammar**
- Confirm you see exactly 5 productions:
  * S → aabS
  * S → abaS
  * S → baaS
  * S → SS
  * S → λ (lambda/empty string)
- If different, STOP and notify me

**STEP 3: Open Multiple Run Interface**
- Click "Input" menu
- Select "Multiple Run"

**STEP 4: Enter Test Strings**

**Accept Strings (should be ACCEPTED):**
- `` (empty string)
- `aab`
- `aba`
- `baa`
- `aabaab`
- `aabbaa`
- `baaaab`
- `aabaabaab`

**Reject Strings (should be REJECTED):**
- `a`
- `aa`
- `b`
- `ab`
- `aabb`
- `aaab`
- `abab`
- `aaabbb`

**How to Enter:**
- Type each string and press Enter
- Total: 16 test strings (8 Accept + 8 Reject)

**STEP 5: Run All Tests**
- Click "Run Inputs" button
- Wait for processing
- Verify results show Accept/Reject for each string

**STEP 6: Verify Results**
- Check all 8 Accept strings show "Accept"
- Check all 8 Reject strings show "Reject"
- If unexpected results, STOP and notify me

**STEP 7: Arrange Window for Screenshot**
- Ensure both grammar and test results are visible
- Resize/reposition as needed

**STEP 8: Take Screenshot**
- Capture grammar productions + all test results
- Save as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem2_JFLAP_Tests.png`**

**STEP 9: Verify Screenshot**
- Open PNG file to confirm clarity
- Retake if needed

**STEP 10: Report Back**
- Confirm screenshot saved
- Provide full path
- Report any issues

---

## Problem 3: Derivation Tree for (a + b) * c + d

### JFLAP File to Open:
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem3_Expression_Grammar.jff`

### Grammar You Should See:
```
E → T
E → E + T
T → F
T → T * F
F → I
F → (E)
I → a
I → b
I → c
I → d
```

### Part A: Test Multiple Strings (Screenshot 1)

**STEP 1: Open the JFLAP File**
- File → Open
- Navigate to: `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`
- Select `Problem3_Expression_Grammar.jff`
- Click Open

**STEP 2: Verify the Grammar**
- Confirm you see all 10 productions listed above
- This is the standard expression grammar with precedence
- If different, STOP and notify me

**STEP 3: Open Multiple Run Interface**
- Click "Input" menu
- Select "Multiple Run"

**STEP 4: Enter Test Strings**

**Accept Strings (valid expressions):**
- `a`
- `a+b`
- `a*b`
- `(a+b)*c`
- `(a+b)*c+d` (this is our target string!)
- `a+b+c`
- `a*b*c`
- `(a)`
- `((a+b))*c`
- `a+b*c`

**Reject Strings (invalid expressions):**
- `+a`
- `a+`
- `a++b`
- `(a+b`
- `a+b)`
- `()`
- `*`
- `e`
- `ab`

**How to Enter:**
- Type each string and press Enter
- Total: 19 test strings (10 Accept + 9 Reject)

**STEP 5: Run All Tests**
- Click "Run Inputs"
- Verify results

**STEP 6: Verify Results**
- All Accept strings should show "Accept"
- All Reject strings should show "Reject"
- If unexpected, STOP and notify me

**STEP 7: Take Screenshot 1**
- Capture grammar + test results
- Save as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem3_JFLAP_Tests.png`**

**STEP 8: Verify Screenshot 1**
- Check clarity
- Retake if needed

### Part B: Generate Derivation Tree (Screenshot 2)

**CRITICAL:** This is the derivation tree for the assignment question!

**STEP 1: Close Multiple Run Window**
- Close the Multiple Run window (not the grammar window)
- You should be back at the grammar editor view

**STEP 2: Open Brute Force Parse**
- Click "Input" menu
- Select "Brute Force Parse"
- A new window will open

**STEP 3: Enter Target String**
- In the input field, type: `(a+b)*c+d`
- This is the EXACT string from the assignment question
- Double-check spelling and symbols

**STEP 4: Start Parsing**
- Click "Start" button
- JFLAP will begin generating the parse tree
- This may take a few seconds
- Wait until parsing completes

**STEP 5: View the Derivation Tree**
- Once complete, you should see a tree structure
- The tree should show:
  * Root node: E
  * Branches showing the derivation structure
  * Leaves spelling out: ( a + b ) * c + d
- This tree represents how the grammar parses the expression

**STEP 6: Verify Tree Structure**
- Check that the leaves read (left to right): ( a + b ) * c + d
- The tree should show proper operator precedence:
  * Multiplication (*) binds tighter than addition (+)
  * Parentheses force (a+b) to be evaluated first
- If the tree looks wrong, STOP and notify me

**STEP 7: Arrange for Screenshot**
- Make sure the ENTIRE tree is visible
- You may need to scroll or zoom to fit it all
- The tree can be quite large - that's normal

**STEP 8: Take Screenshot 2**
- Capture the complete derivation tree
- Make sure all nodes and edges are visible
- Save as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem3_Derivation_Tree.png`**

**STEP 9: Verify Screenshot 2**
- Open the PNG file
- Confirm the entire tree is visible
- Confirm all node labels are readable
- The tree should be complete from root to all leaves
- Retake if any part is cut off or unclear

**STEP 10: Report Back**
- Confirm BOTH screenshots saved (tests + tree)
- Provide full paths
- Report any issues

---

## Problem 4: Ambiguity Proof (3 Screenshots)

### Overview
Problem 4 requires THREE screenshots:
1. **Screenshot 1:** Ambiguous grammar test results
2. **Screenshot 2:** Multiple parse trees for "aabb" (proves ambiguity)
3. **Screenshot 3:** Unambiguous grammar test results

---

### Part A: Ambiguous Grammar Test Results (Screenshot 1)

**JFLAP File to Open:**
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem4_Ambiguous_Grammar.jff`

**Grammar You Should See:**
```
S → aSb
S → SS
S → λ
```

**STEP 1: Open the Ambiguous Grammar File**
- File → Open
- Navigate to: `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`
- Select `Problem4_Ambiguous_Grammar.jff`
- Click Open

**STEP 2: Verify the Grammar**
- Confirm exactly 3 productions:
  * S → aSb
  * S → SS
  * S → λ
- This is the AMBIGUOUS grammar
- If different, STOP and notify me

**STEP 3: Open Multiple Run**
- Click "Input" menu
- Select "Multiple Run"

**STEP 4: Enter Test Strings**

**Accept Strings:**
- `` (empty)
- `ab`
- `aabb`
- `aaabbb`
- `abab`
- `aabbab`
- `ababab`
- `aaaabbbb`

**Reject Strings:**
- `a`
- `b`
- `aab`
- `abb`
- `ba`
- `aabbb`
- `aaabb`
- `abba`

**How to Enter:**
- Type each string and press Enter
- Total: 16 strings (8 Accept + 8 Reject)

**STEP 5: Run Tests**
- Click "Run Inputs"
- Verify results

**STEP 6: Take Screenshot 1**
- Capture grammar + test results
- Save as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem4_Ambiguous_Tests.png`**

**STEP 7: Verify Screenshot 1**
- Check clarity and completeness

---

### Part B: Multiple Parse Trees for "aabb" (Screenshot 2)

**CRITICAL:** This screenshot PROVES the grammar is ambiguous!

**STEP 1: Close Multiple Run Window**
- Close Multiple Run
- Return to grammar editor view
- The ambiguous grammar should still be loaded

**STEP 2: Open Brute Force Parse**
- Click "Input" menu
- Select "Brute Force Parse"

**STEP 3: Enter Test String**
- Type: `aabb`
- This is the string that has multiple parse trees

**STEP 4: Start Parsing**
- Click "Start" button
- Wait for parsing to complete

**STEP 5: View Parse Trees**
- **CRITICAL:** JFLAP should show MULTIPLE trees
- You should see at least 2 different parse trees for "aabb"
- These trees will have different structures:
  * **Tree 1:** S → SS, then left S → aSb, right S → aSb
  * **Tree 2:** S → aSb, then inner S → SS, then each S → aSb or λ
- The existence of multiple trees proves ambiguity!

**STEP 6: View All Trees**
- JFLAP may show trees one at a time or side-by-side
- If shown one at a time, there should be navigation buttons (Next/Previous)
- Make sure you can see that there are multiple trees
- You might see a counter like "Tree 1 of 2" or similar

**STEP 7: Arrange for Screenshot**
- **Ideal:** If JFLAP shows both trees side-by-side, capture that
- **Alternative:** If shown one at a time, capture one tree but make sure the interface shows there are multiple trees (e.g., "Tree 1 of 2")
- The goal: prove visually that "aabb" has more than one parse tree

**STEP 8: Take Screenshot 2**
- Capture the parse tree(s) showing multiple derivations
- Save as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem4_Ambiguous_ParseTrees.png`**

**STEP 9: Verify Screenshot 2**
- Confirm it's clear that multiple parse trees exist
- This is crucial evidence for the ambiguity proof
- Retake if not clear

---

### Part C: Unambiguous Grammar Test Results (Screenshot 3)

**JFLAP File to Open:**
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem4_Unambiguous_Grammar.jff`

**Grammar You Should See:**
```
S → aSbS
S → λ
```

**STEP 1: Close Current Windows**
- Close the Brute Force Parse window
- Close the ambiguous grammar window

**STEP 2: Open the Unambiguous Grammar File**
- File → Open
- Navigate to: `C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`
- Select `Problem4_Unambiguous_Grammar.jff`
- Click Open

**STEP 3: Verify the Grammar**
- Confirm exactly 2 productions:
  * S → aSbS
  * S → λ
- This is the UNAMBIGUOUS grammar
- Note: Different from ambiguous version!
- If different, STOP and notify me

**STEP 4: Open Multiple Run**
- Click "Input" menu
- Select "Multiple Run"

**STEP 5: Enter Test Strings**
- Use the SAME test strings as the ambiguous grammar:

**Accept Strings:**
- `` (empty)
- `ab`
- `aabb`
- `aaabbb`
- `abab`
- `aabbab`
- `ababab`
- `aaaabbbb`

**Reject Strings:**
- `a`
- `b`
- `aab`
- `abb`
- `ba`
- `aabbb`
- `aaabb`
- `abba`

**STEP 6: Run Tests**
- Click "Run Inputs"
- Verify results

**STEP 7: Verify Results Match**
- **CRITICAL:** The unambiguous grammar should accept/reject the SAME strings as the ambiguous grammar
- This proves both grammars generate the same language
- If results differ, STOP and notify me immediately

**STEP 8: Take Screenshot 3**
- Capture grammar + test results
- Save as:
  **`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\Problem4_Unambiguous_Tests.png`**

**STEP 9: Verify Screenshot 3**
- Check clarity and completeness

**STEP 10: Report Back**
- Confirm ALL THREE screenshots saved:
  1. Ambiguous grammar tests
  2. Multiple parse trees for "aabb"
  3. Unambiguous grammar tests
- Provide full paths
- Report any issues

---

## Summary Checklist

Before proceeding to PDF creation, verify you have ALL 7 screenshots:

- [ ] **Problem1_JFLAP_Tests.png** - CFG for a^n b^m where 2n ≤ m ≤ 3n
- [ ] **Problem2_JFLAP_Tests.png** - CFG for n_a(w) = 2n_b(w)
- [ ] **Problem3_JFLAP_Tests.png** - Expression grammar test results
- [ ] **Problem3_Derivation_Tree.png** - Derivation tree for (a+b)*c+d
- [ ] **Problem4_Ambiguous_Tests.png** - Ambiguous grammar test results
- [ ] **Problem4_Ambiguous_ParseTrees.png** - Multiple parse trees proving ambiguity
- [ ] **Problem4_Unambiguous_Tests.png** - Unambiguous grammar test results

**All screenshots should be saved in:**
`C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\Construct\`

---

## What to Report Back to Me

Once you have completed ALL screenshots, provide me with:

1. **Confirmation:** "All 7 screenshots have been taken and saved"

2. **File Paths:** List the full path for each screenshot:
   - Problem1_JFLAP_Tests.png: [full path]
   - Problem2_JFLAP_Tests.png: [full path]
   - Problem3_JFLAP_Tests.png: [full path]
   - Problem3_Derivation_Tree.png: [full path]
   - Problem4_Ambiguous_Tests.png: [full path]
   - Problem4_Ambiguous_ParseTrees.png: [full path]
   - Problem4_Unambiguous_Tests.png: [full path]

3. **Issues:** Report any issues encountered:
   - Unexpected test results?
   - Missing parse trees?
   - Unclear screenshots?
   - Any other problems?

4. **Verification:** Confirm:
   - All screenshots are clear and readable
   - All test results match expectations (Accept/Reject as specified)
   - Derivation tree is complete
   - Multiple parse trees are visible for "aabb"

---

## Important Notes

**DO NOT proceed to PDF creation until:**
- All 7 screenshots are complete
- All screenshots are verified for clarity
- All file paths are confirmed
- You have reported back to me

**If you encounter any issues:**
- STOP immediately
- Take a screenshot of the issue
- Report back to me with details
- Do NOT continue until resolved

**Quality Standards:**
- Screenshots must be clear and readable
- All text in JFLAP windows must be legible
- Grammar productions must be visible
- Test results must show Accept/Reject clearly
- Trees must be complete (not cut off)

---

## After Screenshots Are Complete

Once you confirm all screenshots are ready, I will:
1. Verify the file paths
2. Begin the LaTeX PDF compilation process
3. Insert each screenshot into the appropriate section
4. Create the final submission PDF

**Remember:** NO PDF creation until ALL screenshots are confirmed!
