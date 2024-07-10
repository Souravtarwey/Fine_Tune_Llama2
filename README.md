# Fine_Tune_Llama2 using Qlora for Summarization task


This project demonstrates how to fine-tune the LLAMA2 model for the summarization task using the PubMed Summarization dataset from Hugging Face. The fine-tuned model can then be used locally to generate summaries for new articles.

# Note:
- Free Google Colab offers a 15GB Graphics Card (Limited Resources --> Barely enough to store Llama 2–7b’s weights)
- We also need to consider the overhead due to optimizer states, gradients, and forward activations
- Full fine-tuning is not possible here: we need parameter-efficient fine-tuning (PEFT) techniques like LoRA or QLoRA.
- To drastically reduce the VRAM usage, we must fine-tune the model in 4-bit precision, which is why we’ll use QLoRA here.
- 
## Project Overview

1. **Train the Model in Google Colab:**
   - Load and preprocess the PubMed Summarization dataset.
   - Fine-tune the LLAMA2 model usin qlora confiq. .
   - Save the fine-tuned model and tokenizer.

2. **Run Inference Locally:**
   - Load the saved model and tokenizer.
   - Preprocess input articles.
   - Generate summaries.

## Requirements

- Python 3.7+
- PyTorch
- Transformers
- Datasets
- Sentencepiece
- PEFT (Parameter Efficient Fine-Tuning)
- TRL (Transformer Reinforcement Learning)
- Rouge Score
## Installation

Install the necessary libraries using pip:

```bash
pip install torch transformers datasets sentencepiece rouge-score

for colab
!pip install -q accelerate==0.21.0 peft==0.4.0 bitsandbytes==0.40.2 transformers==4.31.0 trl==0.4.7
