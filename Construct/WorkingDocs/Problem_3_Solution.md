# Problem 3 Solution: Derivation Tree for (a + b) * c + d

## Problem Statement
Give the derivation tree for (a + b) * c + d, using the grammar in Example 5.12, but with I → a|b|c|d.

## Grammar (from Example 5.12, modified)

```
E → T | E + T
T → F | T * F
F → I | (E)
I → a | b | c | d
```

## String to Derive
(a + b) * c + d

## Analysis

### Parsing the String
The string is: ( a + b ) * c + d

With standard precedence:
- Parentheses have highest precedence (force grouping)
- Multiplication (*) has higher precedence than addition (+)
- Addition (+) has lowest precedence

So the expression parses as: ((a + b) * c) + d

### Structure Breakdown
- Top level: addition E + T
  - Left side: (a + b) * c (this is an E)
    - This is a multiplication T * F
      - Left: (a + b) (this is a F containing (E))
        - Inside: a + b (this is E + T)
      - Right: c (this is a F)
  - Right side: d (this is a T, which reduces to F, which is I)

## Step-by-Step Derivation

Let me trace through the derivation:

1. E (start symbol)
2. E → E + T (top-level addition)
3. E → T * F (left E becomes multiplication)
4. T → F (left T becomes factor)
5. F → (E) (factor is parenthesized expression)
6. E → E + T (inside parentheses: a + b)
7. E → T (left side of +)
8. T → F
9. F → I
10. I → a
11. T → F (right side of + in parentheses)
12. F → I
13. I → b
14. F → I (right side of * outside parentheses)
15. I → c
16. T → F (right side of top-level +)
17. F → I
18. I → d

## Derivation Tree Structure

```
                               E
                              /|\
                            /  |  \
                          E    +   T
                          |         |
                          T         F
                         /|\        |
                       /  |  \      I
                      T   *   F     |
                      |       |     d
                      F       I
                      |       |
                     (E)      c
                     /|\
                    / | \
                   E  +  T
                   |     |
                   T     F
                   |     |
                   F     I
                   |     |
                   I     b
                   |
                   a
```

## LaTeX Tree Code (using qtree syntax)

```latex
\Tree [.E
        [.E
          [.T
            [.T
              [.F
                (
                [.E
                  [.E
                    [.T
                      [.F
                        [.I a ]
                      ]
                    ]
                  ]
                  +
                  [.T
                    [.F
                      [.I b ]
                    ]
                  ]
                ]
                )
              ]
            ]
            *
            [.F
              [.I c ]
            ]
          ]
        ]
        +
        [.T
          [.F
            [.I d ]
          ]
        ]
      ]
```

## Alternative LaTeX Tree Code (using forest syntax)

```latex
[E
  [E
    [T
      [T
        [F
          [(]
          [E
            [E
              [T
                [F
                  [I
                    [a]
                  ]
                ]
              ]
            ]
            [+]
            [T
              [F
                [I
                  [b]
                ]
              ]
            ]
          ]
          [)]
        ]
      ]
      [*]
      [F
        [I
          [c]
        ]
      ]
    ]
  ]
  [+]
  [T
    [F
      [I
        [d]
      ]
    ]
  ]
]
```

## Verification

Let me verify by reading the leaves left to right:
- ( a + b ) * c + d ✓

The tree correctly represents the derivation with proper precedence:
- The multiplication (*) binds tighter than the top-level addition (+)
- The parentheses force (a + b) to be evaluated first
- The result is ((a + b) * c) + d

## Leftmost Derivation

For completeness, here's the leftmost derivation:

```
E
⇒ E + T                    [production E → E + T]
⇒ T + T                    [production E → T]
⇒ T * F + T                [production T → T * F]
⇒ F * F + T                [production T → F]
⇒ (E) * F + T              [production F → (E)]
⇒ (E + T) * F + T          [production E → E + T]
⇒ (T + T) * F + T          [production E → T]
⇒ (F + T) * F + T          [production T → F]
⇒ (I + T) * F + T          [production F → I]
⇒ (a + T) * F + T          [production I → a]
⇒ (a + F) * F + T          [production T → F]
⇒ (a + I) * F + T          [production F → I]
⇒ (a + b) * F + T          [production I → b]
⇒ (a + b) * I + T          [production F → I]
⇒ (a + b) * c + T          [production I → c]
⇒ (a + b) * c + F          [production T → F]
⇒ (a + b) * c + I          [production F → I]
⇒ (a + b) * c + d          [production I → d]
```

This confirms our derivation tree is correct.
