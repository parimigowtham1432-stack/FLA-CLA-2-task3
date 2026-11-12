 # Formal Language and Automata – Assignment 3
## Case Study-Based Analysis and Design Using PDA and CFG

### SRM Institute of Science and Technology, Tiruchirappalli

**Course Code:** 21CSC301T  
**Course Name:** Formal Language and Automata  
**Assignment:** Continuous Learning Assessment – 2 (Task 3)  
**Student Name:** PARIMI GOWTHAM  
**Register Number:** RA2411026050033  
**Department:** Artificial Intelligence and Machine Learning (AIML)  
**Semester:** V  
**Academic Year:** 2026–2027  
**Faculty:** Dr. C. Gunasundari  

---

## 1. Project Overview

This project presents a case-study-based analysis and implementation of Context-Free Grammars (CFG), Pushdown Automata (PDA), and Nondeterministic Pushdown Automata (NPDA).

Three practical language-validation problems are selected to demonstrate how formal language theory can be applied to programming-language syntax and string validation.

The project implements the validators using Python and demonstrates grammar productions, parsing procedures, stack operations, derivations, test cases, and visual representations.

## 2. Objectives

- Understand Context-Free Grammars and Pushdown Automata.
- Design CFG productions for selected languages.
- Implement stack-based language validation.
- Demonstrate derivations and stack operations.
- Analyze ambiguity and determinism.
- Explain why finite automata are insufficient for certain context-free languages.
- Test valid and invalid input strings.
- Generate test reports and visualizations.

## 3. Case Studies

### Case Study 1: Arithmetic Expression Validation Using CFG

**Objective:** Validate arithmetic expressions containing identifiers, numbers, operators, and parentheses.

Supported operators:
- Addition (+)
- Subtraction (-)
- Multiplication (*)
- Division (/)

**Context-Free Grammar:**

```text
E  -> T E'
E' -> + T E' | - T E' | epsilon

T  -> F T'
T' -> * F T' | / F T' | epsilon

F  -> ( E ) | id | num
```

**Implementation:**
- Tokenization
- Recursive-descent parsing
- Grammar production validation
- Parsing traces
- Accepted and rejected expressions

**Example inputs:**

| Input | Expected Result |
|---|---|
| `a+b` | Accept |
| `a+b*c` | Accept |
| `(a+b)*c` | Accept |
| `a++b` | Reject |
| `(a+b` | Reject |

### Case Study 2: Balanced Parentheses Validation Using PDA

**Objective:** Check whether parentheses are correctly balanced and nested.

**Context-Free Grammar:**

```text
S -> (S)S | epsilon
```

**PDA Components:**

- States: `Q = {q0, qaccept}`
- Input alphabet: `Σ = {(, )}`
- Stack alphabet: `Γ = {Z0, (}`
- Initial stack symbol: `Z0`

**Stack Operations:**

1. Read `(`: Push `(` onto the stack.
2. Read `)`: Pop `(` from the stack.
3. If no matching opening parenthesis exists, reject.
4. Accept if the input is completely consumed and only `Z0` remains.

**Example inputs:**

| Input | Expected Result |
|---|---|
| `()` | Accept |
| `(())` | Accept |
| `()()` | Accept |
| `(()` | Reject |
| `())` | Reject |

### Case Study 3: Palindrome Checking Using NPDA

**Objective:** Determine whether a string is a palindrome over the alphabet `{a,b}`.

**Context-Free Grammar:**

```text
S -> aSa
S -> bSb
S -> a
S -> b
S -> epsilon
```

**NPDA Working Principle:**

1. Read and push symbols from the first half onto the stack.
2. Nondeterministically guess the midpoint.
3. Consume the middle symbol for odd-length strings.
4. Match the remaining symbols against the stack.
5. Pop matching symbols.
6. Accept when the input is consumed and the stack is empty.

**Example inputs:**

| Input | Expected Result |
|---|---|
| `a` | Accept |
| `aba` | Accept |
| `abba` | Accept |
| `baab` | Accept |
| `aab` | Reject |
| `abab` | Reject |

**Implementation note:** The Python implementation simulates possible midpoint choices to demonstrate NPDA-style nondeterministic recognition.

---

## 4. Technologies Used

| Technology | Purpose |
|---|---|
| Python 3 | Main programming language |
| Google Colab | Code execution environment |
| Pandas | Test reports and comparison tables |
| Matplotlib | State diagrams and result charts |
| Regular Expressions | Arithmetic expression tokenization |
| IPython Display | Formatted notebook output |

## 5. Project Features

- Three case-study implementations.
- CFG production definitions.
- PDA and NPDA working principles.
- Recursive-descent arithmetic parser.
- Stack-based balanced-parentheses validator.
- NPDA-style palindrome validator.
- Parsing and stack-operation traces.
- Accepted and rejected test cases.
- Formal model comparison.
- Ambiguity and determinism analysis.
- Finite automata limitations.
- Automatically generated diagrams.
- Test-result visualization.
- CSV report generation.
- Interactive testing.

## 6. Repository Structure

```text
FLA-Assignment-3/
│
├── FLA_Task3_Full_One_Cell_Colab.ipynb
│
├── FLA_Task3_Test_Results.csv
├── FLA_Task3_Comparative_Analysis.csv
├── FLA_Task3_Overall_Summary.csv
├── FLA_Task3_Case_Wise_Summary.csv
│
└── README.md
```

The CSV files are generated after executing the notebook.

## 7. How to Run the Project

### Step 1: Open Google Colab

Visit:

https://colab.research.google.com/

### Step 2: Create a Notebook

Create a new Google Colab notebook.

### Step 3: Copy the Python Code

Copy the complete Assignment 3 Python implementation into a single code cell.

### Step 4: Execute the Code

Click the Run button.

The notebook will execute all three case studies and generate the diagrams, parsing traces, test results, and comparison tables.

### Step 5: Interactive Testing

Choose a validator when prompted:

```text
1 - Arithmetic Expression Validator
2 - Balanced Parentheses Validator
3 - Palindrome Validator
0 - Skip Interactive Testing
```

### Step 6: Download Reports

Download the generated CSV files from the Colab Files panel.

---

## 8. Test Cases and Evaluation

The implementation contains:

- 12 arithmetic-expression test cases.
- 12 balanced-parentheses test cases.
- 12 palindrome test cases.

**Total: 36 test cases.**

The program compares expected and actual results and generates:

- Test-case report.
- Case-wise performance summary.
- Overall execution summary.
- Success-rate chart.

The final success rate is calculated automatically after execution.

## 9. Comparative Analysis

| Feature | Arithmetic | Parentheses | Palindrome |
|---|---|---|---|
| Formal Model | CFG | PDA | NPDA |
| Parser Technique | Recursive descent | Stack operations | Midpoint simulation |
| Stack Usage | Recursive parser stack | Push and pop | Push and matching pop |
| Nondeterminism | No | No | Yes |
| Main Purpose | Expression syntax | Balanced nesting | Reverse symmetry |

## 10. Why Finite Automata Are Insufficient

Finite automata have a finite number of states and cannot maintain an unbounded stack.

- Arithmetic expressions can contain arbitrarily nested parentheses.
- Balanced-parentheses validation requires remembering unmatched opening symbols.
- Palindrome checking requires remembering an arbitrarily long first half and comparing it with the second half.

CFGs and PDAs provide the additional computational structure needed for these examples.

## 11. Ambiguity and Determinism

**Arithmetic expressions:** The grammar separates expressions, terms, and factors to establish operator precedence.

**Balanced parentheses:** The grammar `S → (S)S | ε` describes balanced parentheses, and the stack operations are deterministic.

**Palindrome:** The grammar `S → aSa | bSb | a | b | ε` describes palindromes over `{a,b}`. The NPDA simulation guesses the midpoint.

## 12. Limitations

- The arithmetic parser validates syntax but does not evaluate expressions.
- The balanced-parentheses validator supports only parentheses, not other delimiter types.
- The palindrome validator supports only the alphabet `{a,b}`.
- The palindrome implementation simulates possible NPDA midpoint choices rather than implementing a general-purpose NPDA engine.
- The generated diagrams are conceptual illustrations of the formal models.

## 13. Conclusion

This project demonstrates the practical application of Context-Free Grammars, Pushdown Automata, and Nondeterministic Pushdown Automata through three language-validation case studies.

The arithmetic-expression validator demonstrates grammar-based parsing and operator precedence. The balanced-parentheses validator demonstrates deterministic stack operations. The palindrome validator demonstrates nondeterministic midpoint selection and stack-based comparison.

The project also illustrates why finite automata are insufficient for languages that require unbounded nesting or memory.

## 14. References

1. Course material: Formal Language and Automata, SRM Institute of Science and Technology.
2. Hopcroft, J. E., Motwani, R., and Ullman, J. D., *Introduction to Automata Theory, Languages, and Computation*.
3. Python Documentation: https://docs.python.org/3/
4. Pandas Documentation: https://pandas.pydata.org/docs/
5. Matplotlib Documentation: https://matplotlib.org/stable/

---

**Course:** 21CSC301T – Formal Language and Automata  
**Assignment:** CLA-2 – Task 3  
**Student:** PARIMI GOWTHAM  
**Register Number:** RA2411026050033

**End of README**
