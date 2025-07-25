
# 🕵️‍♂️ Grifter Filter – Resume Claim Verifier & JD Matcher

This project automatically evaluates resumes for authenticity and relevance to a given Job Description (JD). It parses resumes, scrapes GitHub for real project proof, applies Retrieval-Augmented Generation (RAG) to verify claims, computes a matching score, and generates a detailed summary.

---

## 🧠 Models & Tools Used

| Task                         | Model / Library                              |
|-----------------------------|----------------------------------------------|
| Resume Parsing              | `spaCy`, `pdfplumber`, `regex`               |
| GitHub README Scraping      | `requests`, `BeautifulSoup`                  |
| Embeddings                  | `sentence-transformers` (e.g., MiniLM)       |
| Claim Verification (RAG)    | Cosine similarity + LLM check (`T5/BART`)    |
| Summarization               | `t5-base` or `facebook/bart-large-cnn`       |
| Score & Output              | `pandas`, `sklearn`, `transformers`          |

---

## 🧩 Pipeline Overview

1. **Parse Resume PDF**  
   Extracts name, email, CGPA, skills, GitHub link, and project titles from raw text using NLP.

2. **Scrape GitHub Projects**  
   Fetches README files of linked repositories and cleans them for context.

3. **Verify Projects (RAG Style)**  
   Uses Sentence Embeddings and LLM to check if claimed projects actually exist in GitHub content.

4. **Score Resume Against JD**  
   - Skills match
   - CGPA score
   - Project-JD similarity
   - Claim authenticity
   - Leadership detection

5. **Generate Summary**  
   Creates a concise overview of how the resume aligns with the JD, along with a final score.

---

## 📥 Example Input

### 📄 Resume (Parsed JSON)

```json
{
  "name": "Tejas Venugopalan",
  "github": "https://github.com/tejasvenu45",
  "cgpa": 8.73,
  "skills": ["Python", "FastAPI", "MongoDB", "Kafka", "Docker", "ReactJS"],
  "projects": [
    "Real-Time Warehouse Inventory Management using FastAPI, Kafka, MongoDB",
    "AI-Powered Sales Forecasting Engine"
  ],
  "has_leadership": true
}
```

### 📋 Job Description

```
We are hiring Software Development Engineers with strong fundamentals in Python and experience with FastAPI, MongoDB, and real-time data. Projects involving ML pipelines, open-source contributions, and leadership in tech clubs are a plus.
```

---

## ✅ Example Output

### 📈 Score Breakdown

| Metric                  | Score |
|-------------------------|-------|
| Project Claim Verified  | 0.90  |
| Project-JD Similarity   | 0.85  |
| CGPA Score              | 0.86  |
| Skills Match            | 0.90  |
| Leadership              | 1.00  |
| Bonus                   | 1.00  |
| **Final Score**         | **0.902** |

View the output in grifter_final_ranking.csv folder which has the analysis of my resume

---

### 📝 Generated Summary

> **Tejas Venugopalan** is a graduate of PES University in Mumbai, India. He is currently working as a Web Development Intern at Smart Swift Innovations. He has worked on building an AI-powered Smart Budgeting Web App.
**JD Alignment:** CGPA of 8.74 meets the requirement. Leadership experience demonstrated.
---



## 🧪 Future Improvements

- Integrate LangChain for richer RAG-style grounding  
- Support more resume formats (.docx)  
- Deploy as web app using Streamlit / FastAPI  
- Fine-tune scoring based on recruiter feedback  

---

## 📬 Contact

Feel free to reach out: [tenacioustejas@gmail.com](mailto:tenacioustejas@gmail.com)

---
