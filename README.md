# 🛡️ MetaGuard: A Multi-Layer Classification Framework for Controlled and Safe LLM Response Generation

MetaGuard is a security-aware framework designed to defend Large Language Models (LLMs) from unsafe prompts through **multi-layer classification** and **metadata-guided SYSTEM prompts**. The system leverages both **binary and multi-class classifiers** to assess prompt safety and dynamically steer LLM behavior with fine-grained control over response generation.

---

## 🚀 Key Features

- **Binary Classifier**: Detects whether an input prompt is safe (Benign) or potentially harmful (Malicious).
- **Multi-Class Classifier**: Categorizes prompts across 28 domain-subdomain threat classes (e.g., Malware, Privacy Violation, Racism).
- **Dynamic SYSTEM Prompting**: Injects classification metadata into the SYSTEM prompt to guide the LLM’s behavior.
- **LLM Integration**: Works seamlessly with local LLaMA models via [Ollama](https://ollama.com/).
- **Interactive Streamlit UI**: Test prompts, view predictions, and visualize metadata in real-time.
- **Logging & Feedback Loop**: Captures prompts and responses for analysis and potential retraining.


---

## 📊 Datasets Used

| Dataset Name                           | Purpose            | Type             | Notes                               |
|----------------------------------------|--------------------|------------------|-------------------------------------|
| `safe-guard-prompt-injection`          | Binary Classifier  | 0 = Benign, 1 = Malicious | Realistic prompt attacks      |
| `SPML_Chatbot_Prompt_Injection`        | Binary Classifier  | 0/1 Labels       | Diverse attack types                |
| `jailbreak-classification`             | Binary Classifier  | 0/1 Labels       | Focused on jailbreak prompts        |
| `gentelbench-v1`                       | Multi-Class Classifier | Domain/Subdomain | 28 Subcategories + Safe            |

---

## 🧠 Model Overview

- **Model Type**: `roberta-base` (HuggingFace Transformers)
- **Binary Classifier**: Fine-tuned for 2-class classification (Malicious vs. Benign)
- **Multi-Class Classifier**: Fine-tuned for 29-class classification (28 threat types + Safe)
- **Precision**: Mixed-precision (fp16) used for efficient training
- **Evaluation**: F1-score, accuracy, confusion matrix visualization

---

## 🖥️ Streamlit UI

Run the interactive web interface to test classifiers and view metadata-aware LLM responses.

```bash
streamlit run streamlit_app/app.py


