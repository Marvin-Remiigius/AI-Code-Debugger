### **Project Prompt for AI App Builder**

**\#\# Project Overview**

You are to build a full-stack, end-to-end web application called "AI Code Debugger." This application will function as a smart code editor that uses a large language model (LLM) to analyze user-written code. It will identify, explain, and highlight syntax errors, logical issues, and suggestions for improvement directly within the editor.

**\#\# Core User Flow**

1.  A user visits the web application and is presented with a code editor.
2.  The user types or pastes their code into the editor.
3.  The user clicks an "Analyze Code" button.
4.  The application displays a loading indicator while it processes the request.
5.  The code is sent to the backend server, which in turn calls the Gemini API for analysis.
6.  The Gemini API returns a structured list of issues (errors and suggestions).
7.  The backend forwards this list to the frontend.
8.  The frontend receives the list and visually highlights the corresponding lines in the code editor: red for errors and yellow for suggestions.
9.  When the user hovers their mouse over a highlighted line, a tooltip appears showing the detailed explanation of the issue.

**\#\# Technology Stack**

  * **Frontend:** React (using Vite for setup) and styled with Tailwind CSS.
  * **Backend:** Python using the Flask web framework.
  * **AI Integration:** Google's Gemini API via its Python SDK.

**\#\# Frontend Details**

  * **Setup:** Use `Vite` to bootstrap the React project.
  * **Key Library:** The core of the UI is the **Monaco Editor**. It must be integrated into a React component.
  * **Components:** Structure the app with the following components inside a `src/components/` directory:
      * `Header.jsx`: A simple header for the application title.
      * `CodeEditor.jsx`: A component that wraps the Monaco Editor instance. It should be able to receive the code and an array of "decorations" (highlights) as props.
      * `AnalyzeButton.jsx`: A button that triggers the analysis. It should be disabled and show a loading state when a request is in progress.
  * **State Management:** In the main `App.jsx` component, use `useState` to manage the application's state: `code`, `analysisResults`, and `isLoading`.
  * **Styling:** Use **Tailwind CSS** for all styling. Define the highlight colors in `index.css`.
  * **Functionality:** The frontend must make a `POST` request to the backend's `/analyze` endpoint and use the returned data to create decorations for the Monaco Editor.

**\#\# Backend Details**

  * **Framework:** Use **Python** with **Flask**. Ensure `Flask-Cors` is configured to allow requests from the frontend.
  * **API Endpoint:** Create a single `POST` endpoint at `/analyze`.
  * **API Contract:** The endpoint must adhere to this strict JSON contract:
      * **Request Body:** `{ "code": "THE_USER_CODE_STRING" }`
      * **Success Response Body:** A JSON array of issue objects, like so:
        ```json
        [
          {"line": 4, "severity": "error", "message": "Description of the error."},
          {"line": 10, "severity": "suggestion", "message": "Suggestion for improvement."}
        ]
        ```

**\#\# AI Integration (Gemini API)**

  * **Backend Logic:** The `/analyze` endpoint in the Flask app will call the Gemini API.

  * **The Gemini Prompt:** Use the following prompt when calling the Gemini API to ensure a structured JSON response. The `[USER_CODE]` placeholder should be replaced with the code from the frontend.

    > "You are an expert code review assistant. Analyze the following code for bugs and areas for improvement. Your task is to identify issues and return them in a structured JSON array format. Each object in the array should contain: a 'line' number, a 'severity' ('error' for breaking issues, 'suggestion' for improvements), and a 'message' explaining the issue. Do not include any text, explanations, or markdown formatting outside of the JSON array itself. Here is the code:

    > ```
    > [USER_CODE]
    > ```

    > "

**\#\# Folder Structure**

Generate the project with the following folder structure:

```
ai-code-debugger/
├── backend/
│   ├── app.py
│   └── requirements.txt
└── frontend/
    ├── src/
    │   ├── components/
    │   │   ├── CodeEditor.jsx
    │   │   ├── AnalyzeButton.jsx
    │   │   └── Header.jsx
    │   ├── App.jsx
    │   └── index.css
    ├── index.html
    └── tailwind.config.js
```

**\#\# Final Instructions**

Generate the complete, runnable code for both the frontend and backend based on all the specifications above. Include all necessary configurations, such as the `vite.config.js`, `tailwind.config.js`, and `package.json` for the frontend, and the `requirements.txt` for the backend. The code should be clean, well-commented, and ready to run after installing dependencies.