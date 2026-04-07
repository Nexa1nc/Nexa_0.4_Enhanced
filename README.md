# Nexa 0.4 Enhanced (1.2B) 🚀

[![Model License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Unsloth](https://img.shields.io/badge/Powered%20by-Unsloth-orange.svg)](https://github.com/unslothai/unsloth)
[![Type](https://img.shields.io/badge/Task-Text--to--Text-green)](#)

**Nexa 0.4 Enhanced** is a high-performance, 1.2-billion parameter text-to-text model. It represents a significant evolution of the Nexa series, specifically engineered for **superior logical coherence** and **Italian linguistic fluidity**. 

By leveraging a high-density LoRA configuration, this model captures complex nuances that standard fine-tunes often miss.

---

## 🏗 Model Architecture & Heritage
* **Base Model:** [Nexa_0.3_Enhanced](https://huggingface.co/WeAreNexa/Nexa_0.3_Enhanced)
* **Engine:** Trained via **Unsloth** for maximum memory efficiency.
* **Parameters:** 1.2 Billion (1.2B)
* **Type:** Causal Language Modeling (Text-to-Text)
* **Version:** 0.4 "Enhanced"

## 🧪 Training Specifications
The model underwent fine-tuning using the **Alpaca-GPT4** dataset, focusing on instruction-following capabilities.

### LoRA Configuration (High-Density)
| Feature | Setting |
| :--- | :--- |
| **Rank (r)** | **128** (Maximum density for linguistic nuances) |
| **Alpha** | 128 |
| **Target Modules** | All-linear (q, k, v, o, gate, up, down_proj) |
| **Trainable Params** | ~11.2 Million (approx. 0.90% of total) |

### Hyperparameters
* **Steps:** 300
* **Optimizer:** AdamW 8-bit
* **Technique:** Memory-efficient Packing (Unsloth)

---

## 🔥 Key Strengths
1.  **Logical Reasoning:** Enhanced ability to follow multi-step instructions without losing context.
2.  **Italian Fluency:** Specifically optimized to eliminate "translation artifacts," providing natural and grammatically precise Italian output.
3.  **Efficiency:** At 1.2B parameters, it is optimized for fast inference on consumer hardware.

---

## 💻 Usage & Installation

### Installation
```bash
pip install unsloth
pip install --no-deps xformers trl peft accelerate bitsandbytes
```
Quick Start (Python)

```Python
from unsloth import FastLanguageModel
import torch

model, tokenizer = FastLanguageModel.from_pretrained(
    model_name = "YourUsername/Nexa_0.4_Enhanced",
    max_seq_length = 2048,
    load_in_4bit = True,
)

# Enable faster inference
FastLanguageModel.for_inference(model) 

# Example Inference
inputs = tokenizer(
    ["### Instruction:\nSpiegami come funziona l'intelligenza artificiale.\n\n### Response:\n"],
    return_tensors = "pt"
).to("cuda")

outputs = model.generate(**inputs, max_new_tokens = 128)
print(tokenizer.batch_decode(outputs))
```

📜 License
This project is licensed under the Apache License 2.0.

Developed with ❤️ by the Nexa Team.
