# DOCU AI
##🧠 AI Clinical Assistance

An intelligent medical support tool that helps doctors make informed decisions by combining Machine Learning predictions and Generative AI suggestions — all through a beautiful, interactive UI.



###🚀 What It Does

This project is a smart assistant for healthcare professionals. Given a list of patient symptoms, it:

🔍 Predicts possible diseases using a trained ML model

💡 Provides AI-generated suggestions using Gemini Pro

🌐 Offers a modern, interactive web interface with 3D visuals

⚠️ This tool does not diagnose patients — it supports doctors with insights and guidance.

###🧰 Tech Stack

Component    	Tech
Frontend -	Streamlit, HTML/CSS, Spline 3D
Backend -	Flask, scikit-learn, NumPy
AI/ML -	Disease prediction ML model + Gemini Pro (Google AI)
Deployment Ready	- Yes (Localhost / Cloud-compatible)


### ☁️ Deploy on Render

This project includes a `render.yaml` blueprint that deploys:

- `docu-ai-backend` (Flask API)
- `docu-ai-frontend` (Streamlit UI)

Steps:
1. Push this repository to GitHub.
2. In Render, create a new **Blueprint** and select this repo.
3. Set `GEMINI_API_KEY` for the backend service in Render environment variables.
4. After the backend URL is created, update `BACKEND_URL` (if needed) for the frontend service.

Render will use:
- Build command: `pip install -r ../requirements.txt`
- Backend start: `gunicorn app:app --bind 0.0.0.0:$PORT`
- Frontend start: `streamlit run App.py --server.port $PORT --server.address 0.0.0.0`


### Alternative frontend hosting

You can absolutely host the frontend somewhere else (for example Streamlit Community Cloud) and keep only the Flask API on Render. In that case:
- Deploy only `docu-ai-backend` on Render.
- Set `BACKEND_URL` in your frontend host to the Render backend URL.
- Keep CORS enabled in backend (already enabled in this project).
