Turkish Based Custom Syntax Python Core
=====================================

A deep-level modification of the **CPython (Python 3.15a)** core that enables writing Python code with Turkish-based syntax by modifying the language's internal grammar and parser mechanics.

## 🚀 Overview
This project is not a simple pre-processor or a "search-and-replace" script. It involves direct intervention in Python's **Lexer**, **Parser**, and **Grammar** layers. The language has been recompiled from C source code to recognize Turkish keywords at the root level.

### 🛠️ Key Transformations
The standard BNF grammar (`python.gram`) and keyword definitions have been modified to support the following syntax:

| Standard Python | Custom Turkish Syntax |
| :--- | :--- |
| `def` | `islev` |
| `if` | `eger` |
| `else` | `degilse` |
| `:` (Block Opener) | `ise` |

## 💻 Code Example
Behold, the new syntax in action:

```python
islev greet(name) ise
    eger name == "World" ise
        print("Hello World!")
    degilse ise
        print("Hello", name)
    
    return True
⚙️ Technical Implementation
Grammar Overhaul: Modified Grammar/python.gram to introduce new rules for compound statements.

Parser Integration: Updated the PEG Parser logic to treat the ise token as a block delimiter, replacing/augmenting the standard colon behavior.

Build Process: Re-generated the parser using make regen-pegen and compiled the core on a Raspberry Pi (ARM64) architecture.

🏗️ How to Build
To build this custom core on your local machine:

Clone the repository.

Run ./configure

Execute make regen-pegen (mandatory to apply grammar changes).

Run make -j$(nproc)

Launch your custom shell: ./python

📜 License
This project is licensed under AGPLv3. (Note: Original CPython source files maintain their respective PSF license history where applicable.)
