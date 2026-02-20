# The Reliability Gap: A Multi-Dimensional Technical Audit of Memory Safety and Logical Integrity in LLM-Generated C Code

**Status:** Double-Blind Peer Review (39th Canadian Conference on Artificial Intelligence, 2026)

This repository contains the complete replication package, including the automated evaluation pipeline and the full 1195-response dataset, for our study on the technical reliability of Large Language Models (LLMs) in C programming education. 

Our audit evaluates four 2026 frontier models—**GPT-OSS 120B**, **Llama 3.3 70B Versatile**, **Moonshot Kimi K2 0905**, and **Qwen 3 32B** - across a gradient of complexity (Pointers, Dynamic Memory, and Data Structures) using both static structural analysis and dynamic runtime instrumentation.

---

## Dataset Overview
The dataset consists of **1195 validated generation examples** across three core C programming topics. 

For every iteration, the dataset captures:
* **Static Metrics:** Lines of Code (LOC), Cyclomatic Complexity (Max/Avg CCN), Static Error Density (SED), and style deviations based on LLVM standards.
* **Dynamic Metrics:** Compilation Success Rate (CSR), Valgrind memory safety status (leaks/invalid access), UndefinedBehaviorSanitizer (UBSan) triggers, and logical hangs (timeout execution).

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
