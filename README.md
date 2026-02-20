# 🚀 Algo-Coder: Advanced LLM Fine-Tuning for Python Code Generation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Model-blue)](https://huggingface.co/)

## 📌 Project Overview
Algo-Coder is a machine learning project that fine-tunes a state-of-the-art small language model (`Qwen/Qwen2.5-Coder-0.5B`) specifically for generating high-quality algorithmic Python code. 

Instead of relying on basic text generation, this project implements **Parameter-Efficient Fine-Tuning (PEFT)** and **4-bit Quantization** to train a highly capable model within the memory constraints of a free Google Colab GPU. The training data is programmatically extracted from the renowned `TheAlgorithms/Python` repository, ensuring the model learns complex, structurally sound logic.

## ✨ Key Features & Engineering Practices
* **Abstract Syntax Tree (AST) Parsing:** Bypassed fragile regex scraping by implementing Python's `ast` module to mathematically guarantee the extraction of complete, valid function definitions.
* **Low-Rank Adaptation (LoRA):** Implemented PEFT to freeze the base model and train only ~1.5% of the parameters, drastically reducing compute requirements while maintaining high performance.
* **4-bit Quantization:** Utilized `bitsandbytes` (NF4 format) to compress model weights and optimize GPU VRAM usage.
* **Secure Secrets Management:** Integrated Google Colab's `userdata` API to securely manage Hugging Face and GitHub access tokens, ensuring zero credential leakage in the public codebase.
* **Automated MLOps Pipeline:** Configured the Hugging Face `Trainer` API to automatically push model checkpoints and final weights directly to the Model Hub.
* **Advanced Inference Controls:** Customized text generation parameters (low temperature, controlled top_p) to enforce deterministic and logically sound code outputs.

## 🛠️ Tech Stack
* **Language:** Python
* **Machine Learning:** Hugging Face `transformers`, `peft`, `bitsandbytes`, `accelerate`
* **Data Engineering:** `datasets`, `PyGithub`, Python `ast`
* **Environment:** Google Colab (T4 GPU)

## 🚀 Getting Started

### Prerequisites
To run this notebook, you will need:
1. A [Hugging Face](https://huggingface.co/) account and a Write-access Access Token.
2. A [GitHub](https://github.com/) account and a Personal Access Token (Classic).
3. A Google Colab environment.

### Installation & Execution
1. Open the provided `.ipynb` notebook in Google Colab.
2. Navigate to the **Secrets** tab (🔑) in Colab and add your tokens:
   * Name: `HF_TOKEN` | Value: [Your Hugging Face Token]
   * Name: `GITHUB_TOKEN` | Value: [Your GitHub Token]
   * *Ensure "Notebook access" is toggled ON for both.*
3. Update the `your_huggingface_username` variable in Step 5 to your actual Hugging Face handle.
4. Run the cells sequentially. The final model will automatically be pushed to your Hugging Face profile!

## 🔮 Future Improvements
* Expand the dataset extraction to include Object-Oriented Programming (OOP) class structures alongside standalone functions.
* Implement a rigorous evaluation metric (like HumanEval or BLEU score) to benchmark the fine-tuned model against the base model.
* Build a simple FastAPI or Gradio frontend to serve the model as an interactive web application.

## 🤝 Acknowledgments
* Base model provided by [Qwen](https://huggingface.co/Qwen).
* Training data sourced from [TheAlgorithms/Python](https://github.com/TheAlgorithms/Python).
