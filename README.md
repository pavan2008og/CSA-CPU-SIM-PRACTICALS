# Computer System Architecture: CPU Sim Practicals

Simulating Mano's **Basic Computer** in **CPU Sim 4.0.11** (Java 8 with JavaFX).
All 11 practicals from the DSC02 / DSC03 / GE2c syllabus, Ramanujan College, University of Delhi.

**Name:** _your name_
**Roll No.:** _your roll number_
**Course / Semester:** _your course and semester_

---

## Repository structure

```
.
├── README.md
├── BasicComputer.cpu          (machine file, Practicals 1 and 2)
├── P03_ADD.a, practical04.a, PR05.a ... PR09.a, pr10.a, pr11.a   (assembly programs)
└── SCREENSHOTS/
    ├── P01/
    ├── p02/
    └── ... p11/
```

## How to run

1. Install a Java 8 build that includes JavaFX (e.g. Azul Zulu JDK FX 8).
2. Download CPU Sim 4.0.11 and start it with `Cpusim4.bat`.
3. `File > Open machine...` and choose `BasicComputer.cpu`.
4. `File > Open text...` and choose a program from ``.
5. Press `Ctrl+2` (Assemble & load), then `Ctrl+R` (Run) or `Ctrl+D` (Debug mode).

---

## Index

| No. | Practical | Program |
|-----|-----------|---------|
| 1 | [Create a machine (Basic Computer)](#practical-1-create-a-machine) | `BasicComputer.cpu` |
| 2 | [Fetch routine of the instruction cycle](#practical-2-fetch-routine) | `BasicComputer.cpu` |
| 3 | [ADD two numbers](#practical-3-add) | `P03_ADD.a` |
| 4 | [SUBTRACT two numbers](#practical-4-subtract) | `practical04.a` |
| 5 | [Logical operations](#practical-5-logical-operations) | `PR05.a` |
| 6 | [Memory-reference instructions](#practical-6-memory-reference-instructions) | `PR06.a` |
| 7 | [CLA, CMA, CME, HLT](#practical-7-cla-cma-cme-hlt) | `PR07.a` |
| 8 | [INC, SPA, SNA, SZE](#practical-8-inc-spa-sna-sze) | `PR08.a` |
| 9 | [CIR, CIL](#practical-9-cir-cil) | `PR09.a` |
| 10 | [Sum until a negative number](#practical-10-sum-until-negative) | `pr10.a` |
| 11 | [Sum until zero](#practical-11-sum-until-zero) | `pr11.a` |

---

## Practical 1: Create a Machine

**Aim:** Create a machine in CPU Sim based on the Basic Computer architecture: registers, memory, microinstructions, instruction fields and machine instructions.

**Machine:** 8 registers (AC, DR, AR, PC, IR, E, TMP, S), 2 condition bits (carry-E, halt-S), 4096 x 16-bit RAM, 33 microinstructions and 20 machine instructions.

**File:** [`BasicComputer.cpu`](BasicComputer.cpu)

**Screenshots:** [SCREENSHOTS/P01](SCREENSHOTS/P01)

**Result:** A machine based on the Basic Computer architecture was created and saved as `BasicComputer.cpu`.

---

## Practical 2: Fetch Routine

**Aim:** Create the fetch (and decode) routine of the instruction cycle and observe it one microinstruction at a time.

**Fetch sequence:**

```
PC->AR, M[AR]->IR, PC+1->PC, IR(0-11)->AR, decode-IR
```

**Screenshots:** [SCREENSHOTS/p02](SCREENSHOTS/p02)

**Result:** The fetch routine was created and verified by single-stepping the first instruction (INP, F800) of a program.

---

## Practical 3: ADD

**Aim:** Read two numbers from the user, add them and display the sum.

**Program:** [`P03_ADD.a`](P03_ADD.a)

**Sample run:** inputs `25`, `17` give output `42`.

**Screenshots:** [SCREENSHOTS/p03](SCREENSHOTS/p03)

**Result:** 25 + 17 = **42**.

---

## Practical 4: SUBTRACT

**Aim:** Read two numbers A and B and display A - B.

**Idea:** The Basic Computer has no subtract instruction, so A - B = A + (B' + 1), using CMA, INC and ADD.

**Program:** [`practical04.a`](practical04.a)

**Sample run:** inputs `18`, `50` give output `-32`.

**Screenshots:** [SCREENSHOTS/p04](SCREENSHOTS/p04)

**Result:** 18 - 50 = **-32**.

---

## Practical 5: Logical Operations

**Aim:** Perform AND, OR, NOT, XOR, NOR and NAND on two user-entered numbers.

**Idea:** Only AND and CMA exist, so the other operations are built from them using De Morgan's laws.

**Program:** [`PR05.a`](PR05.a)

**Sample run (A = 12, B = 10):**

| Operation | Output |
|-----------|--------|
| A AND B | 8 |
| A OR B | 14 |
| NOT A | -13 |
| NOT B | -11 |
| A XOR B | 6 |
| A NOR B | -15 |
| A NAND B | -9 |

**Screenshots:** [SCREENSHOTS/p05](SCREENSHOTS/p05)

---

## Practical 6: Memory-reference Instructions

**Aim:** Simulate ADD, LDA, STA, BUN and ISZ.

**Task:** Multiply 5 by 3 using repeated addition. ISZ counts the loop and BUN repeats it.

**Program:** [`PR06.a`](PR06.a)

**Screenshots:** [SCREENSHOTS/p06](SCREENSHOTS/p06)

**Result:** Final AC = PROD = **15**.

---

## Practical 7: CLA, CMA, CME, HLT

**Aim:** Simulate CLA, CMA, CME and HLT and note AC, E, PC, AR and IR in decimal.

**Program:** [`PR07.a`](PR07.a)

**Screenshots:** [SCREENSHOTS/p07](SCREENSHOTS/p07)

**Result:** AC = 65535 (-1), E = 1, PC = 5, AR = 1, IR = 28673.

---

## Practical 8: INC, SPA, SNA, SZE

**Aim:** Simulate INC, SPA, SNA and SZE and note AC, E, PC, AR and IR in decimal.

**Program:** [`PR08.a`](PR08.a)

**Screenshots:** [SCREENSHOTS/p08](SCREENSHOTS/p08)

**Result:** AC = 1, E = 0, PC = 11, AR = 1, IR = 28673. Every skip was verified.

---

## Practical 9: CIR, CIL

**Aim:** Simulate CIR and CIL and note AC, E, PC, AR and IR in decimal.

**Program:** [`PR09.a`](PR09.a)

**Screenshots:** [SCREENSHOTS/p09](SCREENSHOTS/p09)

**Result:** AC = 9, E = 0, PC = 6, AR = 1, IR = 28673. Two right rotations followed by two left rotations restore the original value.

---

## Practical 10: Sum until Negative

**Aim:** Read integers and add them until a negative number is read, then output the sum (the negative number is not included).

**Program:** [`pr10.a`](pr10.a)

**Sample run:** inputs `4, 10, 0, 6, -3` give output `20`.

**Screenshots:** [SCREENSHOTS/p10](SCREENSHOTS/p10)

**Result:** 4 + 10 + 0 + 6 = **20**.

---

## Practical 11: Sum until Zero

**Aim:** Read integers and add them until zero is read, then output the sum.

**Program:** [`pr11.a`](pr11.a)

**Sample run:** inputs `8, 12, -5, 0` give output `15`.

**Screenshots:** [SCREENSHOTS/p11](SCREENSHOTS/p11)

**Result:** 8 + 12 + (-5) = **15**.

---

## Tools used

- CPU Sim 4.0.11
- Java 8 with JavaFX (Azul Zulu JDK FX 8)
- Mano's Basic Computer architecture
