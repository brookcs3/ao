JFLAP Screenshot Tutorial: Assignment 5 Final Prep

CRITICAL INSTRUCTIONS:

Follow each step EXACTLY as written.

Save screenshots to the specified paths using the exact filenames.

Each screenshot must clearly show both the grammar productions AND the test results or tree structure.

Overview

You will be taking 7 screenshots in total. The goal is to capture the necessary evidence (Grammar + Test Results / Parse Trees) for your PDF submission.

File Path Root: C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\JF\Final\

Problem 1: CFG for L = {a^n b^m : 2n ≤ m ≤ 3n} (1 Screenshot)

JFLAP File to Open:

C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\JF\Final\Problem 1\Problem 1.jff

Screenshot Purpose:

Demonstrate correctness. The screenshot must confirm that the grammar $S \rightarrow aSbb \mid aSbbb \mid \lambda$ correctly accepts strings within the $2n \le m \le 3n$ ratio and rejects all others.

File Path to Save

Screenshot Content

...\Problem 1\Problem 1.png

Multiple Run: Shows the 3 grammar productions (LHS/RHS) and the Accept/Reject results for at least 15 test strings (7 Accept, 8 Reject).

Problem 2: CFG for L = {w ∈ {a,b}* : n_a(w) = 2n_b(w)} (1 Screenshot)

JFLAP File to Open:

C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\JF\Final\Problem 2\Problem 2.jff

Screenshot Purpose:

Demonstrate correctness for arbitrary order. The screenshot must confirm that the grammar $S \rightarrow aabS \mid abaS \mid baaS \mid \lambda$ accepts strings where $n_a = 2n_b$ regardless of the symbol order, and rejects unbalanced strings.

File Path to Save

Screenshot Content

...\Problem 2\Problem 2.png

Multiple Run: Shows the 4 grammar productions (LHS/RHS) and the Accept/Reject results for at least 16 test strings (8 Accept, 8 Reject).

Problem 3: Derivation Tree for (a + b) * c + d (2 Screenshots)

JFLAP File to Open:

C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\JF\Final\Problem 3\P3.jff

Screenshot Purpose 1 (Tests):

Confirm grammar viability. Confirms the expression grammar accepts standard arithmetic strings and rejects invalid ones.

File Path to Save

Screenshot Content

...\Problem 3\Problem 3.png

Multiple Run: Shows the 10 expression grammar productions (E, T, F, I rules) and the Accept/Reject results for approximately 19 test strings.

Screenshot Purpose 2 (Derivation Tree):

Provide the required solution. This must be the final derivation tree for the target string.

File Path to Save

Screenshot Content

...\Problem 3\Problem 3 B.png

Brute Force Parse Output: Shows the complete derivation tree structure for the input string (a+b)*c+d, visually confirming correct operator precedence.

Problem 4: Ambiguity Proof (3 Screenshots)

JFLAP File Root:

C:\Users\Owner\FALL 2025\INTRO TO THEORY OF COMPUTATION (CS_321_400_F2025)\Modue 5\JF\Final\Problem 4\

Screenshot Purpose 1 (Ambiguous Tests):

Show ambiguous grammar functionality. Confirms the initial ambiguous grammar ($S \rightarrow aSb \mid SS \mid \lambda$) works correctly.

File Path to Save

Screenshot Content

...\Problem 4\Ambiguous Grammar Tree 1 (aSb First)-Tests-BlowUp.png

Multiple Run: Shows the ambiguous grammar productions and the Accept/Reject results for test strings (must include aabb, ab, etc.).

Screenshot Purpose 2 (Ambiguous Parse Trees):

Prove the grammar is ambiguous. This is the core evidence for Part A of the proof.

File Path to Save

Screenshot Content

...\Problem 4\Ambiguous Grammar Tree 1 (aSb First).png AND ...\Problem 4\Ambiguous Grammar Tree 2 (SS First).png

Brute Force Parse Output: Shows the two distinct parse trees for the input string aabb. One tree will show the nested grouping, and the other will show the sequential grouping.

Screenshot Purpose 3 (Unambiguous Tests):

Prove the language is NOT inherently ambiguous. Confirms the unambiguous equivalent grammar ($S \rightarrow aSbS \mid \lambda$) generates the same language.

File Path to Save

Screenshot Content

...\Problem 4\Unambiguous Grammer-Tests.png

Multiple Run: Shows the unambiguous grammar productions and the identical Accept/Reject results for the same set of test strings used in the ambiguous test.

Final Checklist

Once complete, your agent will use these 7 images from the specified paths to compile the final PDF document.