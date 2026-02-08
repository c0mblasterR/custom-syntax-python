
Turkish-Based Custom Syntax Python Core (Piton)

A deep-level modification of the **CPython (Python 3.13+)** core that enables writing Python code with Turkish-based syntax by modifying the language's internal grammar and parser mechanics.

## 🚀 Overview

This project is **not** a simple search-and-replace script. It involves direct intervention in Python's **PEG Parser**, **Lexer**, and **Grammar** layers. The language has been recompiled from C source code to recognize Turkish keywords at the engine level. It supports both original English and new Turkish syntax simultaneously (Bilingual).

### 🛠️ Key Transformations

The standard BNF grammar (`python.gram`) has been modified to support the following dual-syntax:

| Standard Python | Custom Turkish Syntax | Context |
| --- | --- | --- |
| `def` | `islev` | Function Definition |
| `if` | `eger` | Conditional |
| `else` | `degilse` | Else |
| `for` | `ozyinele` | Loops |
| `in` | `icinde` | Membership / Iteration |
| `return` | `dondur` | Function Return |
| `and` | `ve` | Logic |
| `or` | `veya` | Logic |
| `not` | `degil` | Logic |
| `:` | `ise` | Block Delimiter |

---

## 💻 Code Example

Behold, the new syntax in action (completely valid in this core):

```python
islev kontrol_et(sayi) ise
    # Mantıksal operatör ve dondur (return) testi
    eger sayi > 0 ve degil sayi == 10 ise
        dondur "Gecerli"
    elif sayi == 10 ise
        dondur "Tam On"
    degilse ise
        dondur "Gecersiz"

# Ozyinele (for) ve icinde (in) testi
liste = [2, 5, 10, -3]

ozyinele eleman icinde liste ise
    sonuc = kontrol_et(eleman)
    print(f"Sayi: {eleman} -> Durum: {sonuc}")

```

---

## ⚙️ Technical Implementation

1. **Grammar Overhaul:** Modified `Grammar/python.gram` to introduce new rules for compound statements using the `('keyword' | 'yeni_kelime')` pattern.
2. **Parser Generation:** Integrated with Python's modern **PEG Parser**. Used `make regen-pegen` to re-generate `Parser/parser.c`.
3. **Keyword Recognition:** Updated the internal keyword mapping to ensure new terms are treated as first-class citizens (Lexical Analysis).
4. **Hardware:** Successfully built and tested on **Raspberry Pi (ARM64)** architecture.

---

## 🏗️ How to Build

To build this custom core on your local machine:

1. **Clone the repository:**
```bash
git clone https://github.com/c0mblasterR/custom-syntax-python
cd custom-syntax-python

```


2. **Configure and Prepare:**
```bash
./configure
make regen-pegen  # Mandatory to apply grammar changes!

```


3. **Compile:**
```bash
make -j$(nproc)

```


4. **Launch:**
```bash
./python

```



---

## 📜 License


AGPLv3 -> LICENSE-AGPLV3.md
PSF license -> LICENSE-PSFL.md
This project is licensed under **AGPLv3**. (Note: Original CPython source files maintain their respective PSF license history where applicable.)
---
