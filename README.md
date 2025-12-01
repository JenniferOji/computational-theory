# computational-theory
This repository contains the assessment work for the 2025 Computational Theory module. The work is implemented and demonstrated in the notebook:

- problems.ipynb : step-by-step printed demonstrations of SHA-style bit operations, message padding, message scheduling, compression rounds and a small dictionary attack demo.

Key sections (see [problems.ipynb](problems.ipynb)):
- Problem 1 : Binary word helpers and unit tests:
  - Bitwise helpers: [`parity`](problems.ipynb), [`ch`](problems.ipynb), [`maj`](problems.ipynb)
  - Rotation and sigma helpers: [`rotr`](problems.ipynb), [`sigma_upper_0`](problems.ipynb), [`sigma_upper_1`](problems.ipynb), [`sigma_lower_0`](problems.ipynb), [`sigma_lower_1`](problems.ipynb)
- Problem 2 : Compute SHA-256 constants from fractional cube roots:
  - Prime helper: [`primes`](problems.ipynb)
- Problem 3 : SHA-256 padding / block parsing:
  - Padding generator: [`block_parse`](problems.ipynb)
  - Visualiser: [`print_blocks`](problems.ipynb)
- Problem 4 : SHA-256 compression implementation:
  - Message block conversion: [`get_message_blocks`](problems.ipynb)
  - Initialisation: [`H_0`](problems.ipynb)
  - Compression / full hash: [`hash`](problems.ipynb)
- Problem 5 : Simple dictionary attack demo:
  - Uses [`find_password`](problems.ipynb) and the included wordlist [common_passwords_10000.txt](common_passwords_10000.txt)

Prerequisites
- Python 3.8+ with numpy and sympy installed:
```sh
pip install numpy sympy
```

