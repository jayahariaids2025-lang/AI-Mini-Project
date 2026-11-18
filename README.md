# 🤖 AI Resume Analyzer

An AI-powered tool that compares a resume with a job description, scores the match, finds missing skills, and uses **Google Gemini** to suggest improvements.

Built as the mini project for the **AI Tools & Mini Project** module.

## ✨ Features
- **Match score (0-100)** combining skill coverage and text similarity
- **Skill-gap detection**: shows which job skills are matched and which are missing
- **AI suggestions** from Gemini: a fit summary, concrete improvements and rewritten bullet points (optional)
- **Web interface** built with Gradio
- **Unit tests** for the scoring logic

## 🧠 How It Works
| Step | Technique |
|---|---|
| 1. Clean the text | lowercase, strip punctuation |
| 2. Text similarity | TF-IDF vectors + cosine similarity (scikit-learn) |
| 3. Skill extraction | dictionary of skills and aliases with word-boundary matching |
| 4. Overall score | `60% skill coverage + 40% text similarity` |
| 5. AI feedback | Gemini API turns the analysis into personalised advice |

> The score is an estimate to guide improvements. It is **not** the result of a real ATS system.

## 📸 Demo
Add a screenshot of the app here:

![App screenshot](docs/screenshot.png)

Sample output (`data/` files):
```
Overall match score: 39.7 / 100
Text similarity: 24.3%
Skill coverage: 50.0%

Matched skills: data visualization, git, machine learning, matplotlib, numpy, pandas, python, scikit-learn, sql, teamwork
Missing skills: aws, cloud, communication, deep learning, excel, power bi, pytorch, statistics, tableau, tensorflow
```

## 🚀 Getting Started
**Requirements:** Python 3.9+

```bash
# 1. Clone the repo
git clone https://github.com/<your-username>/ai-resume-analyzer.git
cd ai-resume-analyzer

# 2. (Recommended) create a virtual environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. (Optional) enable Gemini suggestions
cp .env.example .env             # then paste your key into .env

# 5. Run the app
python app.py
```
Open the local URL printed in the terminal (usually http://127.0.0.1:7860).

Get a free Gemini API key at [Google AI Studio](https://aistudio.google.com). Without a key the app still works. It just skips the AI suggestions.

### Use it as a library
```python
from resume_analyzer import analyze

result = analyze(resume_text, job_description_text)
print(result.score, result.missing)
```

## 🧪 Run the Tests
```bash
pytest
```

## 📁 Project Structure
```
ai-resume-analyzer/
├── app.py                      # Gradio web app
├── resume_analyzer/
│   ├── analyzer.py             # TF-IDF similarity + scoring
│   ├── skills.py               # skill dictionary + extraction
│   └── ai_suggestions.py       # Gemini integration
├── data/                       # sample resume + job description
├── tests/test_analyzer.py
├── requirements.txt
└── .env.example
```

## 🛠️ Tech Stack
Python · scikit-learn · Gradio · Google Gemini API (`google-genai`)

## 🤝 AI Tools Used While Building
ChatGPT, Gemini and Microsoft Copilot were used for brainstorming, debugging and explaining concepts. *(Edit this section to describe what you actually used each tool for.)*

## 🔮 Future Improvements
- Read resumes directly from PDF/DOCX
- Expand the skills dictionary automatically with NLP
- Track scores across multiple job postings
- Deploy online (Hugging Face Spaces / Streamlit Cloud)

## 👤 Author
**R Jayahari**: [LinkedIn](https://www.linkedin.com/in/your-profile) · [GitHub](https://github.com/your-username)

## 📄 License
MIT: see [LICENSE](LICENSE).
