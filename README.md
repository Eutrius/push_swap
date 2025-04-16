# 🔄 Push_Swap

#### ✅ [125/125]

> A sorting algorithm challenge using two stacks and a limited set of operations

## 📑 Table of Contents

- [The Challenge](#-the-challenge)
- [Operations Arsenal](#️-operations-arsenal)
- [Getting Started](#-getting-started)
  - [Installation](#installation)
  - [Running Push_Swap](#running-push_swap)
  - [Testing with Checker](#testing-with-checker)
- [Behind the Algorithm](#-behind-the-algorithm)
- [Performance](#-performance)
- [Error Handling](#-error-handling)
- [Makefile Commands](#-makefile-commands)
- [Testing Your Solution](#-testing-your-solution)
- [License](#license)

## 🎯 The Challenge

Push_swap is a fascinating algorithmic puzzle: **sort a random list of integers using only two stacks and a limited set of operations in the fewest moves possible**.

Imagine you have two stacks (A and B) and a toolbox with only 11 specific operations. Your mission is to transform stack A from a random pile of integers into a beautifully sorted ascending sequence, while stack B remains empty at the end.

## ⚙️ Operations Arsenal

Your sorting toolbox contains these 11 operations:

| Operation | Description         | Effect                                          |
| --------- | ------------------- | ----------------------------------------------- |
| `sa`      | Swap A              | Swaps the first two elements of stack A         |
| `sb`      | Swap B              | Swaps the first two elements of stack B         |
| `ss`      | Swap Both           | Executes both `sa` and `sb` simultaneously      |
| `pa`      | Push to A           | Takes the top element from B and pushes it to A |
| `pb`      | Push to B           | Takes the top element from A and pushes it to B |
| `ra`      | Rotate A            | Shifts up all elements of stack A by 1          |
| `rb`      | Rotate B            | Shifts up all elements of stack B by 1          |
| `rr`      | Rotate Both         | Executes both `ra` and `rb` simultaneously      |
| `rra`     | Reverse Rotate A    | Shifts down all elements of stack A by 1        |
| `rrb`     | Reverse Rotate B    | Shifts down all elements of stack B by 1        |
| `rrr`     | Reverse Rotate Both | Executes both `rra` and `rrb` simultaneously    |

## 🚀 Getting Started

### Installation

```bash
git clone <repository_url>
cd push_swap
make
```

This will compile both the main `push_swap` program and the bonus `checker` program.

### Running Push_Swap

```bash
./push_swap 4 67 3 87 23
```

The program will output a sequence of operations needed to sort these numbers.

### Testing with Checker

The bonus `checker` program validates whether a sequence of operations properly sorts the stack:

```bash
./push_swap 4 67 3 87 23 | ./checker 4 67 3 87 23
```

If the stack is properly sorted, it will output `OK`. Otherwise, it will output `KO`.

## 🧠 Behind the Algorithm

The sorting strategy uses a combination of techniques:

1. **Smart Selection**: The algorithm calculates the "cost" of each move and chooses the one with the lowest cost
2. **Dual-Stack Efficiency**: By leveraging both stacks, we can reduce the number of operations
3. **Rotation Optimization**: The algorithm determines whether to rotate or reverse-rotate based on position

For very small sets (2-3 numbers), the algorithm uses optimized mini-sorting techniques to handle these edge cases efficiently.

## 🏆 Performance

For different input sizes, here's what you can expect:

- **3 numbers**: ≤ 3 operations
- **5 numbers**: ≤ 12 operations
- **100 numbers**: < 700 operations (efficient algorithm)
- **500 numbers**: < 5500 operations (efficient algorithm)

## 🔍 Error Handling

The program handles various edge cases:

- Duplicate numbers? ❌ Error
- Non-integer arguments? ❌ Error
- Integer overflow? ❌ Error
- Empty input? ✅ No operation

## 📋 Makefile Commands

| Command       | Action                               |
| ------------- | ------------------------------------ |
| `make`        | Compiles push_swap program           |
| `make bonus`  | Compiles checker program             |
| `make all`    | Compiles both programs               |
| `make clean`  | Removes object files                 |
| `make fclean` | Removes object files and executables |
| `make re`     | Cleans everything and recompiles     |

## 🧪 Testing Your Solution

Want to test your push_swap implementation?

```bash
# Generate 100 random numbers and count operations
ARG=$(shuf -i 1-1000 -n 100 | tr "\n" " "); ./push_swap $ARG | wc -l

# Check if sorting is correct
ARG=$(shuf -i 1-1000 -n 100 | tr "\n" " "); ./push_swap $ARG | ./checker $ARG
```

## License

This project is part of the 42 curriculum and follows its academic policies.
