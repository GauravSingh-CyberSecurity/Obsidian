
Here’s a **comprehensive list of resources** (like PortSwigger) for learning and practicing **LLM (Large Language Model) security and attacks**, including labs, guides, papers, and open-source tools:

---

## 🧠 **Interactive Labs and Platforms**

### 1. **[AI Red Team Gym by Microsoft](https://github.com/microsoft/AI-Red-Team-Gym)**

- Open-source sandbox to simulate and test prompt injection, jailbreaks, and LLM misuse.
- Includes **offensive scenarios** and **evaluation metrics**.
- GitHub repo: [microsoft/AI-Red-Team-Gym](https://github.com/microsoft/AI-Red-Team-Gym)

---

### 2. **[Prompt Injection Playground](https://promptattack.dev/)**

- Simulates prompt injection vulnerabilities.
- Great for experimenting with different prompt attacks and bypasses.

---

### 3. **[Shellcoder's LLM Security Labs](https://llmshellcoder.com/)**

- Hands-on labs designed like **PortSwigger Web Security Academy**, but for LLMs.
- Covers:
    - Prompt injection (direct & indirect)
    - Jailbreaking
    - Data extraction
    - Function misuse

---

### 4. **[LLM-Hack-Lab](https://github.com/WizardMac/LLM-Hack-Lab)**

- Docker-based lab with open-source LLMs like GPT-J, Vicuna, etc.
- Practice red-teaming on LLMs locally.

---

## 📚 **Learning and Documentation**

### 5. **[OWASP Top 10 for LLMs](https://owasp.org/www-project-top-10-for-large-language-model-applications/)**

- Like OWASP for web, but focused on LLM risks:
    - Prompt Injection
    - Training Data Poisoning
    - Insecure Output Handling
    - Model Denial of Service, etc.
- A must-read foundational doc.

---

### 6. **[LangChain Security Guide](https://docs.langchain.com/docs/security/)**

- Focuses on secure development of LLM apps using LangChain.
- Covers:
    - Injection prevention
    - Output validation
    - Agent control

---

## 🔧 **Open Source Tools for Testing and Attacking**

### 7. **[PromptBench](https://github.com/llm-attacks/PromptBench)**

- Framework to benchmark LLMs against attacks.
- Automates prompt injection & response evaluation.

---

### 8. **[RedTeamingLLMs](https://github.com/cs14775/RedTeamingLLMs)**

- Scripts and prompts to perform adversarial testing.
- Includes indirect attacks and prompt leaks.

---

### 9. **[Gandalf Game](https://gandalf.lakera.ai/)**

- Fun game to bypass a filter LLM and extract a secret password.
- Gets harder with each level.

---

## 🎓 **Research Papers and Reading**

### 10. **[Universal Prompt Injection (Simon Willison)](https://simonwillison.net/2023/May/3/universal-prompt-injection/)**

- Great overview of how indirect prompt injection works across tools like ChatGPT, Bing, Bard.

---

### 11. **[LLM Exploitation 101 (Ben Schmidt)](https://blog.benjojo.co.uk/post/llm-prompt-injection)**

- Very accessible writeup on practical attacks and defenses.

---

### 12. **[Adversarial Prompting Papers List](https://github.com/thunlp/PromptBench#papers)**

- Collection of academic research around LLM prompt manipulation.

---

## ⚙️ **Other Tools Worth Exploring**

|Tool|Purpose|
|---|---|
|[Rebuff](https://github.com/RebuffAI/Rebuff)|Prompt injection detection|
|[Guardrails AI](https://github.com/shreyashankar/gpt-guardrails)|Control what LLMs can and can't say|
|[PromptGuard](https://github.com/PromptGuard/PromptGuard)|Validate LLM outputs against harmful or incorrect info|
|[OpenAI Red Teaming](https://openai.com/red-teaming-network)|OpenAI's structured approach to LLM red teaming|

---

Would you like a **structured roadmap** (beginner → advanced) to master LLM attacks using these resources?