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

Files
- [problems.ipynb](problems.ipynb) : full notebook .
- [common_passwords_10000.txt](common_passwords_10000.txt) : wordlist used by the demo.
- [requirements.txt](requirements.txt) : Python dependencies.

Requirements 
- Python 3.8+ - https://www.python.org/ : runtime required to run the notebook and scripts.
- NumPy - https://numpy.org/doc/stable/ : used for numeric types and vector ops (`numpy.uint32`, `numpy.cbrt`).
- SymPy - https://docs.sympy.org/latest/ : used for prime generation (see `sp.primerange`, `sp.prime`).
- Jupyter - https://jupyter.org/ : view & run [problems.ipynb](problems.ipynb).
- VS Code Notebooks - https://code.visualstudio.com/docs/datascience/jupyter-notebooks : convenient in‑IDE execution.
- FIPS 180‑4 (SHA spec) - https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf : authoritative reference for constants and algorithm steps.


Prerequisites
- Python 3.8+ with numpy and sympy installed:
```sh
pip install numpy sympy
```



