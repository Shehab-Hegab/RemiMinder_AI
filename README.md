

# 🧠 RemiMinder AI (Data Science Core)

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Model](https://img.shields.io/badge/Model-Gemini_2.5_Flash-orange?style=for-the-badge&logo=google&logoColor=white)](https://deepmind.google/technologies/gemini/)
[![Status](https://img.shields.io/badge/Phase_1-Complete-green?style=for-the-badge)](https://github.com/Shehab-Hegab/RemiMinder_AI)
[![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)](LICENSE)

**The AI inference engine transforming unstructured patient voice data into actionable medical adherence protocols.**

[Project Context](https://remiminderai-care-t8y271i.gamma.site/) • [View Notebooks](notebooks/) • [Report Bug](https://github.com/Shehab-Hegab/RemiMinder_AI/issues)

</div>

---

## 📖 Overview (Phase 1: Audio Intelligence)

**RemiMinder AI** tackles the "communication crisis" in caregiving—where 7 in 10 caregivers feel left in the dark—by structuring the messy reality of medical interactions.

As the **Data Science Core**, this repository contains the logic for **Phase 1**, focusing on converting unstructured voice recordings (e.g., *"Doctor said take 50mg of Zinc after breakfast"*) into a strict **Universal Data Model (JSON)** that powers the frontend application.

### 🎯 Key Data Science Objectives
-   **Structure Unstructured Data:** Transforming conversational audio into rigid database schemas using LLMs.
-   **Latency Optimization:** Utilizing **Google Gemini 1.5 Flash** for sub-second inference speeds.
-   **Prompt Engineering:** Developing robust system instructions to handle medical jargon, dosage abbreviations (BID, QID), and implicit dates.
-   **Schema Validation:** Ensuring all AI outputs conform to strict JSON requirements before reaching the application layer.

---

## 🏗️ AI Pipeline Architecture

The system operates on a "Listen, Extract, Validate" pipeline designed for high accuracy and low latency.

```mermaid
graph LR;
    A[🎤 Raw Audio Input] -->|Transcription| B[📄 Unstructured Text];
    B -->|Context Injection| C[🧠 Gemini 1.5 Flash];
    C -->|Zero-Shot Extraction| D{JSON Schema Validator};
    D -- Pass --> E[✅ Structured Data (Postgres Ready)];
    D -- Fail --> C[🔄 Retry / Error Handling];
    E --> F[📅 Task Scheduler / API Response];
🧩 The Universal Data Model (JSON)

One of the primary data science achievements in Phase 1 is the definition of the Canonical Schema. This standardizes data regardless of input phrasing.

Example Input:

"Mom needs to take her heart pill, the Atorvastatin, 20 milligrams, every night at 8 PM starting today."

AI Output:

code
JSON
download
content_copy
expand_less
{
  "medication": "Atorvastatin",
  "dosage": "20mg",
  "category": "Cardiology",
  "schedule": {
    "frequency": "Daily",
    "time": "20:00",
    "start_date": "2024-11-24"
  },
  "priority": "High",
  "intent": "new_prescription"
}
📂 Repository Structure

This repository focuses on the modeling, pipelines, and evaluation logic.

code
Bash
download
content_copy
expand_less
RemiMinder_AI/
├── data/
│   ├── raw_audio/           # Sample medical audio clips for testing
│   └── synthetic_transcripts/ # Generated text data for prompt tuning
├── models/
│   ├── prompts/             # System instructions & Few-Shot examples
│   └── validators/          # Pydantic models for schema enforcement
├── notebooks/               # Jupyter notebooks for EDA and Model Prototyping
├── src/
│   ├── pipeline.py          # Main inference pipeline (Audio -> JSON)
│   ├── gemini_client.py     # Wrapper for Google Gemini API
│   └── utils.py             # Text cleaning and normalization
├── tests/                   # Unit tests for extraction accuracy
├── requirements.txt         # Python dependencies
└── README.md
🚀 Getting Started

Follow these steps to set up the Data Science environment locally.

Prerequisites

Python 3.10+

Google Gemini API Key

Installation

Clone the Repo

code
Bash
download
content_copy
expand_less
git clone https://github.com/Shehab-Hegab/RemiMinder_AI.git
cd RemiMinder_AI

Install Dependencies

code
Bash
download
content_copy
expand_less
pip install -r requirements.txt

Configure API Keys
Create a .env file in the root directory:

code
Bash
download
content_copy
expand_less
GOOGLE_API_KEY=your_gemini_api_key_here
🔬 Running the Pipeline

To test the extraction logic on a text input (simulating a transcript):

code
Bash
download
content_copy
expand_less
python src/pipeline.py --input "Take Amoxicillin 500mg three times a day for 7 days"

To run the exploratory notebooks:

code
Bash
download
content_copy
expand_less
jupyter notebook notebooks/01_prompt_engineering.ipynb
🔮 Roadmap: Phase 2 & Beyond

While Phase 1 focused on Audio, Phase 2 (In Progress) shifts focus to Computer Vision (RemiScan) and deeper Predictive Modeling.

Feature	Status	Tech Stack
Audio-to-JSON Pipeline	✅ Completed	Gemini Flash, Python
RemiScan (OCR + Visual Grounding)	🚧 In Progress	Gemini VLM, OpenCV
Conflict Detection	⏳ Planned	NLP Consistency Check
Adherence Prediction	⏳ Planned	Scikit-Learn / XGBoost
👨‍💻 Author

Shehab Hegab
Lead Data Scientist & AI Engineer

Developing AI solutions that bridge the gap between clinical data and patient reality.

LinkedIn • GitHub

code
Code
download
content_copy
expand_less
### 💡 What I changed for you:
1.  **Role Specificity:** I removed the "Mobile App" and "React Native" sections. This now looks like a pure Data Science/AI Engineering repo.
2.  **Phase 1 Focus:** I highlighted "Audio Intelligence" and "Gemini Flash" as the current achievements, matching your PDF's timeline.
3.  **PDF Integration:** I used terms like "Universal Data Model" and "Gemini 1.5 Flash" (updated from 2.5 in text to standard naming, or you can keep 2.5 if you have early access) and referenced the specific output examples found in your documents.
4.  **Tech Stack:** Switched to Python, Jupyter, and API wrappers, which are the tools you actually used.
