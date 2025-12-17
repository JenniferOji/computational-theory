# SHA-256 Implementation and Cryptographic Analysis

This repository contains a complete implementation of the SHA-256 cryptographic hash algorithm built from scratch as part of the 2025 Computational Theory module. The project demonstrates every aspect of SHA-256 functionality through detailed code examples, mathematical explanations, and practical applications including a password cracking demonstration.

## Table of Contents

- [Key Sections](#key-sections)
- [Repository Structure](#repository-structure)
- [How to Run the Code](#how-to-run-the-code)
- [Technical Reference](#technical-reference)

## Key Sections

See [problems.ipynb](problems.ipynb) for detailed implementations: 

**Problem 1: Binary Words and Operations**

The foundation begins with implementing the essential 32-bit operations used throughout SHA-256. This includes bitwise helper functions like [`parity`](problems.ipynb#parity-function), [`ch`](problems.ipynb#ch-choose-function) (choose), and [`maj`](problems.ipynb#majority-function) (majority), along with rotation operations ([`rotr`](problems.ipynb#rotate-right-rotr)) and the four sigma functions ([`sigma_upper_0`](problems.ipynb#sigma0-function)/[`sigma_upper_1`](problems.ipynb#sigma1-function) and [`sigma_lower_0`](problems.ipynb#the-sigma0-function)/[`sigma_lower_1`](problems.ipynb#the-sigma1-function)) that provide the non-linear transformations critical to SHA-256's security. These operations rely on [NumPy](https://numpy.org/)'s precise 32-bit unsigned integer type (`numpy.uint32`) to ensure cryptographically accurate arithmetic without overflow issues that could occur with standard Python integers.

**Problem 2: Fractional Parts of Cube Roots**

This section demonstrates how the 64 round constants are mathematically derived from the fractional parts of cube roots of the first 64 prime numbers. The [`primes`](problems.ipynb#problem-2-primes) function generates the required prime numbers using [SymPy](https://www.sympy.org/)'s efficient prime generation functions (`sympy.primerange` and `sympy.prime`), which provide mathematically verified prime sequences essential for cryptographic constant generation. The notebook shows the complete process of extracting the 32-bit constants used in the compression algorithm.

**Problem 3: Padding**

Here we implement SHA-256's padding and block parsing requirements. The [`block_parse`](problems.ipynb#problem-3-padding) function handles the complex padding rules that ensure messages are properly formatted into 512-bit blocks, utilising [NumPy](https://numpy.org/)'s array operations to efficiently manage byte-level data manipulation and ensure proper alignment for cryptographic processing. The [`print_blocks`](problems.ipynb#helper-function) provides visualisation of how the padding process transforms input data.

**Problem 4: Hashes**

This is the heart of the implementation, featuring the complete SHA-256 compression function. The [`get_message_blocks`](problems.ipynb#problem-4-hashes) function converts padded data into the required 32-bit word format using [NumPy](https://numpy.org/)'s vectorised operations for efficient array processing and precise modular arithmetic operations. [`H_0`](problems.ipynb#problem-4-hashes) provides the initial hash values, and the main [`hash`](problems.ipynb#problem-4-hashes) function implements the full 64-round compression algorithm that transforms message blocks into cryptographic digests.

**Problem 5: Passwords**

The final section demonstrates a real-world application through a dictionary attack on SHA-256 hashed passwords. Using the [`find_password`](problems.ipynb#problem-5-passwords) function and the included wordlist of common passwords, this shows both the practical use of the hash implementation and the security implications of weak password choices.

## Repository Structure

```
computational-theory/
├── README.md                           # This file - project overview and setup guide
├── problems.ipynb                      # Main notebook with all SHA-256 implementations
├── requirements.txt                    # Python package dependencies
├── . gitignore                         # Git ignore rules for Python projects
└── data/                               # Supporting data files
    └── common_passwords_10000.txt      # Dictionary of 10,000 common passwords for Problem 5
```

### File and Folder Descriptions

- **README.md**:  Provides an overview of the project, setup instructions, and navigation guide. 
- **problems.ipynb**:  The main Jupyter notebook containing all five problem solutions with detailed explanations, code implementations, and test cases.
- **requirements.txt**: Lists all Python packages required to run the code (numpy, sympy, jupyter).
- **.gitignore**: Standard Python gitignore file to exclude unnecessary files from version control.
- **data/**: Directory containing supporting data files. 
  - **common_passwords_10000.txt**: A curated list of 10,000 commonly used passwords used in Problem 5 to demonstrate dictionary attacks against SHA-256 hashed passwords.

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
2. You can run all cells sequentially by selecting **Cell -> Run All** from the menu
3. Alternatively, run cells individually by selecting them and pressing **Shift + Enter**

### Step 5: Explore Each Problem

Each problem is clearly marked with a Level 2 heading in the notebook.  Work through them sequentially, as later problems build upon earlier implementations.


## Technical Reference

This implementation strictly adheres to the [FIPS 180-4 Secure Hash Standard](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf), ensuring compatibility with official SHA-256 specifications.  All function implementations, constants, and algorithms follow the standard's definitions precisely.

---

**Author**:  Jennifer Oji  
**Repository**: [github.com/JenniferOji/computational-theory](https://github.com/JenniferOji/computational-theory)  
**Last Updated**: December 2025