# HireLens — AI-Powered Resume Screening & Candidate Ranking Tool

Built by **Hammad Tanveer** | [LinkedIn](https://linkedin.com/hammad-tanveer-) | [GitHub](https://github.com/Hammadtanveer)

A complete, self-contained Flask + scikit-learn web app that ranks a batch
of resumes (PDF, DOCX, or TXT) against a job description, using an
explainable two-part AI score — no external API keys, no cloud calls,
everything runs locally.

## 🎯 Why I Built This

As someone actively applying to Software/AI Engineering roles, I wanted
to understand how ATS (Applicant Tracking Systems) and resume screening
tools actually score candidates — so I built one myself. HireLens uses
TF-IDF similarity and skill-taxonomy matching to give recruiters an
explainable, transparent shortlist instead of a black-box score.

## 📸 Screenshot

*(screenshot placeholder — add later)*

## ⚙️ Tech Stack

- **Backend**: Flask (Python)
- **Scoring Engine**: scikit-learn (TF-IDF + Cosine Similarity)
- **File Parsing**: pypdf, python-docx
- **Frontend**: HTML, CSS (custom dark theme), Vanilla JS

## What's inside
HireLens/
├── app.py                          # Flask app (routes: /, /rank, /api/rank, /about)
├── requirements.txt
├── engine/
│   ├── parser.py                   # Extracts text from .pdf / .docx / .txt uploads
│   ├── skills.py                   # Curated skills taxonomy + email/phone/experience extraction
│   └── ranker.py                   # TF-IDF similarity + skill-overlap scoring & ranking
├── sample_data/
│   ├── job_description_sample.txt
│   └── resumes/                    # Sample resumes to try immediately
├── templates/
│   ├── base.html
│   ├── index.html                  # Upload form (job description + resumes)
│   ├── results.html                # Ranked candidate list
│   └── about.html                  # Scoring methodology
└── static/
├── css/style.css
└── js/script.js

## 🚀 Setup

1. Clone this repo:
```bash
   git clone https://github.com/Hammadtanveer/HireLens.git
   cd HireLens
```

2. Create a virtual environment:
```bash
   python -m venv venv
```
   Activate it:
   - Windows: `venv\Scripts\activate`
   - macOS / Linux: `source venv/bin/activate`

3. Install dependencies:
```bash
   pip install -r requirements.txt
```

4. Run the app:
```bash
   python app.py
```

5. Open **http://127.0.0.1:5000** in your browser.

## 🧪 Try it immediately with the sample data

No real resumes handy? Use what's included:
- Paste the contents of `sample_data/job_description_sample.txt` into the job description box.
- Upload all files in `sample_data/resumes/`.

## 🧠 How Scoring Works

Each candidate gets one combined score from two signals:

- **JD relevance (60%)** — TF-IDF cosine similarity between the job
  description and the resume's full text.
- **Skill coverage (40%)** — the percentage of the job description's
  required skills (matched against a curated skill taxonomy in
  `engine/skills.py`) that are actually present in the resume.

The results page shows both sub-scores and the exact matched/missing
skills — the ranking is explainable, not a black box.

You can change the 60/40 weighting in `engine/ranker.py` (`WEIGHTS` dict).

## ⚠️ Honest Limitations

This is a heuristic screening aid, not a hiring decision-maker:
- It can't judge quality or depth of experience, only presence of terms.
- PDF text extraction can struggle with heavily designed, multi-column templates.
- The skill taxonomy is a fixed list — unusually phrased skills may be missed.

Always have a human review the shortlist before making hiring decisions.

## 🙏 Credits

Original scoring engine concept adapted and rebuilt with custom UI/UX
by Hammad Tanveer.
