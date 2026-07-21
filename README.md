# Propositional Logic Solver

An interactive command-line proof assistant for propositional logic, built in OCaml. Users can add premises, set a goal, apply inference rules, inspect the proof state, and explore possible derivations through a REPL.

Built as a team project for Cornell CS 3110.

## Features

- Parses and validates propositional-logic formulas
- Represents formulas with algebraic data types and recursive AST operations
- Maintains a proof state of premises, derived formulas, and an optional goal
- Automatically applies core inference rules when premises or goals are added
- Exhaustively applies supported rules with `applyall`
- Tracks whether the current goal has been reached
- Explains possible derivations for a formula
- Supports loading premises from a file and exporting the current proof state
- Includes OUnit tests for parsing, AST utilities, inference rules, and proof-state operations

## Supported Logic

| Operator | Meaning | Example |
| --- | --- | --- |
| `!` | Negation | `!A` |
| `&` | Conjunction | `A & B` |
| `\|` | Disjunction | `A \| B` |
| `->` | Implication | `A -> B` |

Supported inference rules include:

- Modus Ponens
- Modus Tollens
- Conjunction Introduction
- Conjunction Elimination
- Hypothetical Syllogism
- Contraposition

## Getting Started

### Prerequisites

- OCaml
- Dune

### Build and run

```bash
git clone https://github.com/Shirleywu537/propositional-logic-solver.git
cd propositional-logic-solver
dune build
dune exec ./src/main.exe
```

## Example Session

```text
> premise A
> premise (A -> B)
> goal B
> show
```

The solver derives `B` through Modus Ponens and reports that the goal has been reached.

## Commands

| Command | Description |
| --- | --- |
| `premise <formula>` or `p <formula>` | Add a premise |
| `goal <formula>` or `g <formula>` | Set a goal |
| `applyall` or `aa` | Apply all supported inference rules exhaustively |
| `show` or `s` | Display the current proof state |
| `find <formula>` | Show possible derivations for a formula |
| `stats` | Display proof-state statistics |
| `rules` | List supported inference rules |
| `load <file>` | Load commands from a script file |
| `export <file>` | Export the current proof state |
| `remove <formula>` | Remove a premise |
| `clearderived` | Clear derived formulas while keeping premises |
| `cleargoal` | Clear the current goal |
| `reset` | Clear the entire proof state |
| `help` | Show command help |
| `quit` or `q` | Exit the REPL |

## Test

Run the test suite with:

```bash
dune test
```

## Project Structure

```text
├── lib/
│   ├── ast.ml          # Formula representation and AST utilities
│   ├── parser.ml       # Formula parser and validation
│   ├── rule.ml         # Individual inference rules
│   └── sequent.ml      # Proof-state and derivation management
├── src/
│   └── main.ml         # Interactive REPL
├── test/
│   └── parser_tests.ml # OUnit test suite
├── data/
│   └── premises.txt    # Example premise script
└── README.md
```

## Team

- Nicole Luo
- Tyson Yoshikawa
- Shirley Wu
- Anna Sahakyan
