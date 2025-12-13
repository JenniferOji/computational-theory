# SHA-256 Implementation and Cryptographic Analysis

This repository contains a complete implementation of the SHA-256 cryptographic hash algorithm built from scratch as part of the 2025 Computational Theory module. The project demonstrates every aspect of SHA-256 functionality through detailed code examples, mathematical explanations, and practical applications including a password cracking demonstration.


## Key sections (see [problems.ipynb](problems.ipynb)):


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

The project includes [problems.ipynb](problems.ipynb) as the main notebook containing all implementations and explanations. Supporting files include [common_passwords_10000.txt](common_passwords_10000.txt) which provides the password dictionary for the attack demonstration, and [requirements.txt](requirements.txt) listing all Python dependencies needed to run the code.

## Getting Started

To use this implementation, you'll need [Python 3.8+](https://www.python.org/downloads/) or later along with the mathematical and scientific computing libraries used throughout the different problems.

**Installation:**
```bash
pip install numpy sympy jupyter
```

Once dependencies are installed, simply open [problems.ipynb](problems.ipynb) in [Jupyter](https://jupyter.org/) to explore the complete SHA-256 implementation. Each section builds upon the previous ones, so running the notebook from beginning to end provides the full experience.

## Technical Reference

This implementation strictly adheres to the [FIPS 180-4 Secure Hash Standard](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf), ensuring compatibility with official SHA-256 specifications. The code demonstrates not just how SHA-256 works, but why each component is necessary for cryptographic security, making it valuable for practical understanding of modern cryptographic systems.
