# General Health Query Chatbot (Task 4) – Mistral‑7B‑Instruct

## Task Objective
Build a conversational AI that answers general health‑related questions using a large language model. The chatbot must:
- Use **prompt engineering** to act as a helpful, non‑diagnostic medical assistant.
- Implement **safety filters** to block emergencies, prescriptions, and diagnostic requests.
- Integrate with a free LLM API (Hugging Face Inference API).

## Model Applied
- **Model:** `mistralai/Mistral-7B-Instruct-v0.3`
- **Why this model:** Instruction‑tuned for chat, follows system prompts, provides detailed and natural responses.
- **Access:** Hugging Face free Inference API (requires a free token).

## Key Features
| Feature | Implementation |
|---------|----------------|
| Prompt engineering | Mistral’s `[INST] <<SYS>> ... <</SYS>>` format with a custom system prompt |
| Safety filters | Hardcoded keyword lists for emergencies, prescriptions, and diagnostic phrases |
| Fallback responses | Rule‑based answers for common queries (sore throat, chest pain, blood pressure) when the API fails |
| Rate‑limit handling | Retry on 503 (model loading) and user‑friendly message on 429 (rate limit) |

## Key Results and Findings
- **Safety filters work correctly:** Queries containing “kill myself”, “prescribe”, or “diagnose me” are blocked immediately.
- **Mistral‑7B‑Instruct produces high‑quality, natural responses** for health questions (e.g., causes of sore throat, blood pressure management).
- **Fallback mechanism ensures the user always receives an answer** – even when the API is slow or rate‑limited.
- **Limitations:** Free API has rate limits (~30 requests per minute). Response time can be 5–15 seconds.

### Example Interaction
> **User:** What causes a sore throat?  
> **Bot:** Sore throats are most commonly caused by viral infections (e.g., cold or flu), but can also result from allergies, dry air, or bacterial infections like strep throat. Rest, hydration, and warm liquids may help. If symptoms persist or are severe, consult a doctor.

## How to Run

1. **Get a free Hugging Face token**  
   - Sign up at [huggingface.co](https://huggingface.co/)  
   - Go to Settings → Access Tokens → Create new token (type: **Read**)

2. **Clone the repository** and navigate to the task folder:
   ```bash
   cd task4_general_health_chatbot