
---

## 📊 Datasets Used

| Dataset Name                      | Type           | Description                                 |
|----------------------------------|----------------|---------------------------------------------|
| `safe-guard-prompt-injection`    | Binary         | Clean malicious/benign pairs                |
| `SPML_Chatbot_Prompt_Injection`  | Binary         | Real-world injection scenarios              |
| `jailbreak-classification`       | Binary         | Focused jailbreak samples                   |
| `gentelbench-v1`                 | Multi-class    | 28 subdomain threat classes + "Safe"        |

---

## 🧠 Models Used

| Model Name     | Purpose              | Framework       | Notes                                  |
|----------------|----------------------|------------------|----------------------------------------|
| `roberta-base` | Binary Classification| HuggingFace      | Fast and memory-efficient (fp16)       |
| `roberta-base` | Multi-class Labeling | HuggingFace      | 29-class classification                |
| `llama3`       | Response Generation  | Ollama           | Uses SYSTEM prompts with classifiers   |

---

## 📈 Training Summary

### Binary Classifier

- Dataset: ~35,000 prompts labeled 0 (benign) or 1 (malicious)
- Model: `roberta-base`, fine-tuned for binary classification
- Accuracy: **98.5%**, F1 Score: **98.2%**
- Training Time: ~35 mins (RTX 4090, fp16)

### Multi-Class Classifier

- Dataset: ~90,000 prompts across 29 labels (domain-subdomain pairs)
- Model: `roberta-base`, trained with macro F1 optimization
- Accuracy: **94.8%**, Macro F1: **93.2%**
- Balanced across all classes for fairness

---

## 🧠 SYSTEM Prompt Behavior

```text
You are a secure, policy-compliant AI assistant.
Input Classification:
- Binary: Malicious (99.2%)
- Domain: Technology Misuse
- Subdomain: Malware

Instruction:
🛑 Refuse response due to policy violation.
Explain to the user: "This prompt was flagged under Technology Misuse → Malware with high confidence. I cannot proceed."
