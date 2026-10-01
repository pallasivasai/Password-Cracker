# Password-Cracker

A small **educational brute-force password cracking demonstration** written in Python.

The program generates candidate strings from a configured character set, compares them with a locally entered target password, counts attempts, and measures elapsed time.

> **Ethical use:** This repository is for learning and controlled lab environments. Do not use password-cracking code against accounts, systems, or credentials you do not own or have explicit permission to test.

## How it works

The implementation is contained in `password cracker.py`.

### 1. Enter a target password

The program prompts:

```text
Password >
```

The entered value becomes the local target string.

### 2. Define the search characters

The configured character set contains digits, lowercase letters, uppercase letters, and punctuation/special characters.

### 3. Generate candidates

`tryPassword()` uses `itertools.product()` and enumerates candidate lengths from **1 through 8**.

For each candidate it:

1. increments the attempt counter
2. joins the generated tuple into a string
3. compares the candidate with the target
4. returns as soon as the exact string is found

### 4. Measure the search

The function records the start time and returns the number of attempts and elapsed seconds.

## Search-space model

If the configured character set contains C characters, the maximum number of candidates considered is:

```text
C^1 + C^2 + C^3 + ... + C^8
```

This demonstrates why the brute-force search space grows rapidly as character variety and password length increase.

## File

| File | Purpose |
|---|---|
| `password cracker.py` | Candidate generation, comparison, attempt counting and timing |

## Run locally

### Requirement

- Python 3

### Command

```bash
git clone https://github.com/pallasivasai/Password-Cracker.git
cd Password-Cracker
python "password cracker.py"
```

Then enter a password when prompted.

## Current implementation notes

- Search length is limited to **1–8 characters**.
- Matching is a direct local string comparison.
- No remote service authentication is performed.
- No wordlist or hash database is used.
- If the target is outside the configured search space, the current function does not define a normal “not found” return path.

## Learning goals

This project demonstrates brute-force enumeration, combinatorial search spaces, Python iterators, `itertools.product`, attempt counting, runtime measurement, and why longer and more varied passwords increase search cost.

## Links

- [GitHub Repository](https://github.com/pallasivasai/Password-Cracker)
