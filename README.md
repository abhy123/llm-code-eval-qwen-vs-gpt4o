# LLM Coding Evaluation: Hugging Face Qwen vs OpenAI GPT-4o

This project compares code generation and performance of two large language models (LLMs):

- **Hugging Face Qwen3-Coder-480B-A35B-Instruct**
- **OpenAI GPT-4o**

We evaluate their ability to solve a custom algorithmic coding problem in both **Python** and **Java**, and measure their accuracy and runtime.

## Problem Statement

  Read an array of integers from a file named `input_array.txt`. Compute the **maximum sum of any contiguous subarray of size exactly `k=5000`**, where you're allowed to **skip at most one 
  negative number** in the window to boost the sum.  
  Skipping means removing its contribution from the sum (optional, only one allowed per window).

## Dataset

- The input array was generated with 6000+ integers between -100 and 100, and written to `input_array.txt`.
- Both models were provided the **same prompt and input file** for fairness.

## Code Generation Process

- Each model generated Python code based on the problem prompt.
- That code was then converted to Java using the same LLM.
- All code was executed and timed in a local environment using Python's `subprocess`.

## Results

| Model            | Language | Output      | Time Taken |
|------------------|----------|-------------|------------|
| **OpenAI**       | Python   | -2,171,148  | 0.07s      |
|                  | Java     | -2,171,148  | 0.19s      |
| **HuggingFace**  | Python   | -2,164,046  | 0.10s      |
|                  | Java     | -2,164,046  | 0.18s      |

HuggingFace's Qwen model produced a different result than GPT-4o, and **upon manual inspection, Hugging Face's result was correct.**

## Files

- `HuggingFaceOpenAI.ipynb` – Main notebook containing prompt, generation, code saving, execution, and timing.
- `input_array.txt` – Integer dataset used for all test runs.
- `*_solution.py` and `*_solution.java` – Code files generated per model.

## Observations

- Both models generated runnable, reasonably optimized code.
- HuggingFace’s Qwen model handled the “skip negative” condition more accurately.
- Java implementations ran slightly slower than Python, but the difference was minimal.
