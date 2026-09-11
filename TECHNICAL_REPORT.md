# Kryptos K4: Matrix and Anchor-Based Cryptanalysis Report

## 1. Executive Summary
This technical document establishes the mathematical framework for the open-source implementation of an anchor-based shift displacement algorithm targeting Section 4 of the Kryptos sculpture (K4). The project isolates the inner core from positions 22 to 75 to evaluate modular character cycles using historical sculptured clues as numerical matrices.

---

## 2. Mathematical Framework & Index Mapping

The cryptanalysis operates under the strict assumption that alphabetical displacements are conditioned by adaptive key shifts. Characters are transformed into integers where \(A = 0, B = 1, \dots, Z = 25\).

### 2.1 Vector Anchor Assignments
The structural foundations utilize specific key letters mapped into a repetitive cyclic array:

*   **α₁ (F):** Shift factor 5
*   **α₂ (Q):** Shift factor 16
*   **α₃ (N):** Shift factor 13
*   **α₄ (M):** Shift factor 12

This forms the static core array:
\[\vec{A} = [5, 16, 13, 12]\]

### 2.2 Core Displacement Formula
For every encrypted character \(C_i\) located at index i in the isolated text sequence, the algorithm processes the target plaintext \(P_i\) through the following modular equation given an alphabet iterative key k (0 ≤ k < 26):

\[P_i = (C_i - k - \vec{A}_{[i \pmod 4]}) \pmod{26}\]

---

## 3. Targeted Sequence (Positions 22–75)

The analysis bypasses outer characters to focus resources entirely on the central 50-letter ciphertext cluster:

```text
FLKVMJNREBSURWWSPCUDADRHOVAHCONNBSUXJHREFBTEOIPETN
```

### 3.1 Verification & Linguistic Metrics
The companion script scans the output streams against standard bigram and trigram frequency charts. High priority tags are allocated to results matching localized roots and geo-temporal coordinate indicators:
*   `PROSENCIAL`
*   `NEW YORK`
*   `BERLIN` / `CLOCKS`

---

## 4. Conclusion & Reproduction
By standardizing this approach under an open-source framework, this repository provides a baseline for rigorous replication without localized anomalies. The mathematical integrity can be verified independently by executing the `k4_cipher_script.py` file included within this system.
