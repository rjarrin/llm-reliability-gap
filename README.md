# The Reliability Gap: A Multi-Dimensional Technical Audit of Memory Safety and Logical Integrity in LLM-Generated C Code

**Status:** Double-Blind Peer Review (39th Canadian Conference on Artificial Intelligence, 2026)

This repository contains the complete replication package, including the automated evaluation pipeline and the full 1195-response dataset, for our study on the technical reliability of Large Language Models (LLMs) in C programming education. 

Our audit evaluates four 2026 frontier models - **GPT-OSS 120B**, **Llama 3.3 70B Versatile**, **Moonshot Kimi K2 0905**, and **Qwen 3 32B** - across a gradient of complexity (Pointers, Dynamic Memory, and Data Structures) using both static structural analysis and dynamic runtime instrumentation.

---

## Dataset Overview
The dataset consists of **1195 validated generation examples** across three core C programming topics. 

For every iteration, the dataset captures:
* **Static Metrics:** Lines of Code (LOC), Cyclomatic Complexity (Max/Avg CCN), Static Error Density (SED), and style deviations based on LLVM standards.
* **Dynamic Metrics:** Compilation Success Rate (CSR), Valgrind memory safety status (leaks/invalid access), UndefinedBehaviorSanitizer (UBSan) triggers, and logical hangs (timeout execution).

---
## Replication Guide

This repository is designed for one-click reproducibility using Google Colab or a local Jupyter environment.

### Phase 1: Problem Bank Generation & Standardization
Run `01_Phase1_Problem_Bank_Generation.ipynb` to execute the multi-turn conversational loop. This queries the target teacher LLMs (via API) to dynamically generate novel C programming problems. The script then isolates the "Step 1: Problem" texts, removes duplicates, and packages them into standardized batches of 100 per topic (Pointers, Dynamic Memory Allocation, Data Structures).

### Phase 2: The Automated Audit Pipeline
Run `02_Phase2_Automated_Audit_Pipeline.ipynb` to feed the standardized problems back into the four models. Operating in a stateful, multi-turn conversational loop, the models are prompted to generate the corresponding C11 solutions, conceptual explanations, hints, learning objective summaries, and the machine-readable JSON test suites.

### Phase 3: Technical Evaluation & Visualization
Run `03_Automated_Technical_Evaluation.ipynb` to execute the rigorous auditing pipeline on the generated C code and visualize the results.
* **Static Analysis:** Uses `lizard` (v1.20.0) for Cyclomatic Complexity, `cppcheck` (v.2.7-1) for Static Error Density, and `clang-format` (v1:14.0.0-1ubuntu1.1) for stylistic adherence.
* **Dynamic Analysis:** Compiles code via `gcc` (v11.4.0) with strict academic flags (`-Wall -Werror -std=c11`). Successfully compiled binaries are executed via `valgrind` (v.1:3.18.1-1ubuntu2) and `UBSan` to catch "Definitely Lost" heap memory, invalid read/writes, and silent logic failures (e.g., integer overflows).
* **Data Visualization:** Ingests the consolidated `Phase3_Master_Evaluation_Stats.csv` and generates the figures and table information presented in the manuscript (Figures 2-6 and Tables 1-2).

---
## Environment Requirements
To run the dynamic auditing pipeline locally, ensure your Linux environment (or WSL) has the following installed:
* `gcc` (>= 11.4.0) 
* `valgrind` (>= 3.18.1) 
* `cppcheck` (>= 2.7) 
* `clang-format` (>= 14.0.0)
* Python 3.10+ (`pandas`, `matplotlib`, `seaborn`, `tqdm`, `lizard`)

---

## License
This dataset and code are released under an anonymized MIT License for double-blind peer review.
