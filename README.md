# SHA-256 Implementation and Cryptographic Analysis

This repository contains a complete implementation of the SHA-256 cryptographic hash algorithm, built from scratch as part of the 2025 Computational Theory module. The project demonstrates every aspect of SHA-256 functionality through detailed code examples, mathematical explanations, and practical applications, including a password cracking demonstration.

## Table of Contents

- [Key Sections](#key-sections)
- [Repository Structure](#repository-structure)
- [How to Run the Code](#how-to-run-the-code)
- [Technical Reference](#technical-reference)
- [References](#references)

---

## Key Sections

See [problems.ipynb](problems.ipynb) for detailed implementations:

**Problem 1: Binary Words and Operations**  
The foundation begins with implementing the essential 32-bit operations used throughout SHA-256, such as [`parity`](problems.ipynb#parity-function), [`ch`](problems.ipynb#ch-function), [`maj`](problems.ipynb#maj-function) and four sigma functions. These core operations ensure cryptographically accurate transformations while preventing overflow errors.  

**Problem 2: Fractional Parts of Cube Roots**  
This section computes the 64 round constants used in SHA-256, derived from the fractional cube roots of prime numbers. The [`primes`](problems.ipynb#problem-2-primes) function leverages [SymPy](https://www.sympy.org/) for efficient prime computations.

**Problem 3: Padding**  
The [`block_parse`](problems.ipynb#problem-3-padding) function implements the padding rules outlined in the Secure Hash Standard, ensuring all messages are parsed into 512-bit blocks.  

**Problem 4: Hashes**  
The compression function simulates 64 SHA-256 rounds using [`get_message_blocks`](problems.ipynb#problem-4-hashes). Results are verified against theoretical values for accuracy.  

**Problem 5: Passwords**  
A real-world application demonstrates **dictionary attacks** on SHA-256 hashed passwords using [`find_password`](problems.ipynb#problem-4-hashes) and the included wordlist. 

---

## Repository Structure

```
computational-theory/
├── README.md                           # Project overview and setup instructions
├── problems.ipynb                      # Main Jupyter notebook with implementations
├── requirements.txt                    # Dependencies
├── .gitignore                          # Ignore unnecessary files
└── data/
    └── common_passwords_10000.txt      # Wordlist for Problem 5
```
Note: The common_passwords_10000.txt file is sourced from [SecLists](https://github.com/danielmiessler/SecLists/blob/9b890357aa0b05b61b82cf64ea2674e1a2a59ced/Passwords/Common-Credentials/Pwdb_top-10000.txt), a curated collection of datasets used in security assessments. It contains commonly used passwords for testing password-related cryptographic applications.


---

## How to Run the Code

Follow these step-by-step instructions to set up and run the project on your local machine:

### Prerequisites

- Python 3.8 or higher ([download here](https://www.python.org/downloads/))
- pip (Python package installer, typically included with Python)
- Git ([download here](https://git-scm.com/downloads))

### Step 1: Clone the Repository

Open your terminal or command prompt and run: 

```bash
git clone https://github.com/JenniferOji/computational-theory.git
```

Navigate into the cloned repository:

```bash
cd computational-theory
```

### Step 2: Install Dependencies

Install all required Python packages using pip:

```bash
pip install -r requirements.txt
```

Alternatively, install packages individually:

```bash
pip install numpy sympy jupyter
```

### Step 3: Launch Jupyter Notebook

Start the Jupyter Notebook server:

```bash
jupyter notebook
```

This will open a new browser window showing the repository contents.

### Step 4: Open and Run the Notebook

1. Click on `problems.ipynb` to open the main notebook
2. You can run all cells sequentially by selecting **Cell $\rightarrow$ Run All** from the menu
3. Alternatively, run cells individually by selecting them and pressing **Shift + Enter**

### Step 5: Explore Each Problem

Each problem is clearly marked with a Level 2 heading in the notebook.  Work through them sequentially, as later problems build upon earlier implementations.

---

## References

Below are key documentation and resources essential for understanding and using this project:

- [NIST FIPS 180-4: Secure Hash Standard (SHA)](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf): The official standard for SHA-256, which underpins the cryptographic functions and ensures compatibility with industry standards.
- [NumPy Documentation](https://numpy.org/doc/stable/): Used for efficient numerical operations and array handling throughout the implementation, especially for 32-bit integer arithmetic and data manipulation.
- [SymPy Documentation](https://docs.sympy.org/latest/index.html): Used for mathematical functions such as prime number generation, which are critical for cryptographic constant derivation.
- [Salting and Stretching Passwords](https://blogs.helixops.ai/salting-stretching-passwords/): Explains the importance of salting and key stretching for improved password hashing, as demonstrated in the password guidance section.
- [Diffusion](https://www.geeksforgeeks.org/computer-networks/difference-between-confusion-and-diffusion/): Overview of diffusion and its critical role in ensuring that small changes in input produce significant, unpredictable changes in hash outputs.
- [Avalanche Effect in Cryptography](https://www.geeksforgeeks.org/computer-networks/avalanche-effect-in-cryptography/): Introduction to the avalanche effect, illustrating how effective cryptographic algorithms amplify minor input differences into drastically different outputs.

---

**Author**: Jennifer Oji  
**Last Updated**: December 2025