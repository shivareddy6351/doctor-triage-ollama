# 🏥 AI-Powered Doctor Triage Chatbot

This project is a **FastAPI-based intelligent healthcare chatbot** that simulates a **virtual doctor** capable of collecting patient symptoms, performing **triage evaluation**, and providing guideline-based recommendations.
It integrates **pre-trained AI models (via Ollama API)** and multiple logic modules for structured data extraction, triage evaluation, and medical guideline verification.

---

## 🚀 Features

* 🔐 **Secure authentication** using JWT & password hashing
* 🤖 **AI Doctor Agent** — generates empathetic medical replies
* 🧠 **Symptom Extractor** — turns chat into structured symptom data
* ⚕️ **Triage Engine** — classifies condition as Emergency/Urgent/Routine
* 📚 **Guideline Verifier** — adjusts triage using medical guidelines
* 💾 **MongoDB Atlas Integration** for users and logs
* 🌐 **FastAPI Backend + Static Frontend** for easy web use

---

## 🧩 Project Structure

```
├── main.py                     # FastAPI entry point
├── doctor_agent.py             # AI doctor conversational logic
├── symptom_extractor.py        # Extracts structured data from chat
├── triage_engine.py            # Determines urgency level
├── guideline_verifier.py       # Verifies triage per medical rules
├── utils.py                    # Logging, constants, helper functions
├── static/
│   ├── login.html
│   ├── index.html
│   └── style.css
├── data/
│   └── guidelines.json         # Medical guideline reference
├── .env                        # Environment variables
└── requirements.txt
```

---

## ⚙️ Setup Instructions

### 1️⃣ **Clone the repository**

```bash
git clone https://github.com/shivareddy6351/doctor-triage-ollama.git
cd doctor-triage-chatbot
```

### 2️⃣ **Create a virtual environment**

```bash
python -m venv venv
venv\Scripts\activate      # (Windows)
source venv/bin/activate   # (Mac/Linux)
```

### 3️⃣ **Install dependencies**

```bash
pip install -r requirements.txt
```

## 🔑 Environment Variables (.env file)

Create a `.env` file in the project root with:

```
MONGO_URL=mongodb+srv://<user>:<password>@cluster.mongodb.net/
SECRET_KEY=your_secret_key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=60
OLLAMA_URL=http://localhost:11434
MODEL_NAME=llama3:instruct
APP_PORT=8000
```

> 💡 Ensure your **Ollama model** is running locally or accessible from the given URL.

---

## 🧠 Running the Application

Run the FastAPI app:

```bash
uvicorn main:app --reload
```

Then open your browser:

```
http://127.0.0.1:8000
```

✅ **Login Page:**
You’ll first see `login.html` for user authentication.

✅ **Chat Interface:**
After login, `/chat` opens the AI Doctor Chat interface.

---

## 🩺 Usage Flow

1. **User registers or logs in** — JWT authentication is generated.
2. **User enters symptoms** — message sent to `/api/chat`.
3. **Doctor agent (AI model)** replies using Ollama LLM.
4. **Symptom Extractor** processes the full conversation into structured data.
5. **Triage Engine** evaluates if the case is Emergency, Urgent, or Routine.
6. **Guideline Verifier** upgrades triage based on `guidelines.json`.
7. **Session Logs** are stored via `utils.log_session()`.
8. The final AI reply + triage result is sent back to the frontend.

---

## 🏗️ Architecture Overview

**Frontend:** Static HTML/CSS (served by FastAPI)
**Backend:** FastAPI REST API
**Modules:**

* `doctor_agent.py` → calls AI model for conversational reply
* `symptom_extractor.py` → extracts structured data
* `triage_engine.py` → checks severity level
* `guideline_verifier.py` → adjusts based on guidelines
* `utils.py` → logs sessions, manages constants

**Database:** MongoDB Atlas
**AI Model:** Pre-trained model via Ollama API (e.g., LLaMA, Mistral, etc.)

---

## 🧾 Logging

Each chat session is logged:

```
/logs/session_<session_id>.json
```

It includes:

* Chat messages
* Extracted structured data
* Triage result
* Timestamp

---

## 📊 Example Output

```json
{
  "reply": "Based on your symptoms, it may be a mild infection. Keep hydrated and rest.",
  "structured": {
    "chief_complaint": "fever and sore throat",
    "onset": "2 days",
    "severity": "moderate",
    "associated_symptoms": ["fatigue"],
    "vitals": {"temp": "38.5"}
  },
  "triage": {"level": "Urgent", "reason": "High fever detected."}
}
```

---

## 🧾 Execution Details (Step-by-Step)

1. **Start Ollama model server**
   Example (if using LLaMA 3 model):

   ```bash
   ollama run llama3:instruct
   ```

2. **Run FastAPI app**

   ```bash
   uvicorn main:app --reload
   ```

3. **Access the app**

   * Visit `http://127.0.0.1:8000`
   * Register → Login → Start chatting

4. **Each message triggers:**

   * Doctor agent reply (AI)
   * Symptom extraction
   * Triage evaluation
   * Guideline verification
   * Logging of session data

5. **Results are displayed instantly** on the frontend.

---

## 🧩 Team & Project Details

* **Team ID:** G459
* **Project Title:** *AI Agents for Conversational Patient Triage*
* **Member:** *Shiva Vardhan Markala (22BD1A6736)*

---

## 📘 License

Released under the **MIT License** — free to use, modify, and extend.

---
