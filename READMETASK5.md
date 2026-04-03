# Mental Health Support Chatbot (Task 5)

## Task Objective
Build a conversational chatbot that provides empathetic and supportive responses for users experiencing stress, anxiety, or emotional distress.  
The chatbot is fine‑tuned on real human dialogues to produce context‑aware, compassionate answers.

## Dataset Used
**Source:** `nbertagnolli/counsel-chat` (Hugging Face Datasets)  
**Description:** A collection of real‑world counseling conversations between clients and therapists.  
**Size:** After cleaning, ~1,500 examples of question‑answer pairs covering various mental health topics.  
**Preprocessing:** Only `questionText` (user) and `answerText` (counselor) were kept, formatted as `"User: ...\nBot: ..."`.

## Model Applied
- **Base model:** `distilgpt2` – a smaller, faster version of GPT‑2 (82M parameters)  
- **Fine‑tuning method:** Causal language modeling using the Hugging Face `Trainer` API  
- **Training duration:** 3 epochs, batch size 8 (effective 16 with gradient accumulation)  
- **Optimizer:** AdamW with learning rate 5e‑5, weight decay 0.01  
- **Hardware:** Google Colab GPU (free tier) – training time ~20 minutes

## Key Results and Findings
- The fine‑tuned model produces **longer, more empathetic** responses than the base DistilGPT2.  
- Example outputs:
  - *User:* "I've been feeling really anxious about my job interview tomorrow."  
    *Bot:* "That sounds really tough. Remember that you've prepared well and you're capable. It's okay to be nervous."
  - *User:* "I had a fight with my best friend and I feel awful."  
    *Bot:* "I'm sorry you're going through that. Would you like to talk about what happened?"
- **Limitations:**  
  - The model may occasionally produce repetitive or off‑topic answers.  
  - It is not a substitute for professional mental health care.  
- **Future improvements:**  
  - Use a larger base model (e.g., GPT‑2 medium or DialoGPT).  
  - Train on the full EmpatheticDialogues dataset (25k examples).  
  - Add safety guardrails to redirect crisis keywords to a helpline.

## How to Run
1. **Install dependencies** (recommended in a virtual environment):  
   ```bash
   pip install transformers datasets accelerate evaluate torch gradio