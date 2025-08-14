# AI Code Debugger

A full-stack web application that lets users write or paste code, then uses Google's Gemini AI to detect errors and suggest improvements. Errors are highlighted in **red** and suggestions in **yellow** directly inside the Monaco Editor.

---

## 🚀 Features

- **Live Code Editor** using [Monaco Editor](https://microsoft.github.io/monaco-editor/).
- **AI-Powered Analysis** with Gemini API.
- **Visual Highlights** for errors and suggestions.
- **Simple, Minimal UI** built with React and Tailwind CSS.
- **Backend API** built with Flask and CORS support.

---

## 🛠 Technology Stack

- **Frontend:** React (Vite), Tailwind CSS
- **Backend:** Python (Flask), Flask-CORS
- **AI API:** Gemini API via the official Python SDK

---

## 📂 Project Structure

```
project-root/
├── backend/
│   ├── app.py
│   └── requirements.txt
└── frontend/
    ├── src/
    │   ├── components/
    │   │   ├── Header.jsx
    │   │   ├── CodeEditor.jsx
    │   │   └── AnalyzeButton.jsx
    │   └── App.jsx
    ├── package.json
    └── vite.config.js
```

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/ai-code-debugger.git
cd ai-code-debugger
```

---

### 2. Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Run the Flask server:
```bash
python app.py
```
The backend will run at `http://localhost:5000`.

---

### 3. Frontend Setup
```bash
cd ../frontend
npm install
```

---

### 4. Create `.env.local` for API Key
Inside the `frontend` folder, create a `.env.local` file:
```bash
touch .env.local
```

Add your Gemini API key:
```
VITE_GEMINI_API_KEY=your_api_key_here
```

> **Note:** You can get your Gemini API key from [Google AI Studio](https://makersuite.google.com/app/apikey).

---

### 5. Start the Frontend
```bash
npm run dev
```
The frontend will run at `http://localhost:5173`.

---

## 📡 API Contract

### Endpoint
```
POST /analyze
```

### Request Body
```json
{
  "code": "your code here"
}
```

### Response Body
```json
[
  {
    "line": 3,
    "severity": "error",
    "message": "Syntax error: missing semicolon"
  },
  {
    "line": 5,
    "severity": "suggestion",
    "message": "Consider renaming variable for clarity"
  }
]
```

---

## 🤖 How It Works

1. User writes or pastes code into Monaco Editor.
2. On clicking **Analyze**, the frontend sends the code to `/analyze`.
3. The Flask backend sends the code to Gemini API with a **strict JSON output prompt**.
4. The AI's response is parsed and displayed as highlights in the editor.

---

## 🙌 Built by
**Team Hackcelerate**
