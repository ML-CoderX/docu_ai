# Render Deployment (Manual Service Setup)

If you create services manually in Render (instead of Blueprint), use these exact settings.

## Backend service
- **Root Directory:** `backend`
- **Build Command:** `pip install -r ../requirements.txt`
- **Start Command:** `gunicorn app:app --bind 0.0.0.0:$PORT`
- **Environment Variables:**
  - `PYTHON_VERSION=3.11.9`
  - `GEMINI_API_KEY=<your_key>`

## Frontend service (optional)
- **Root Directory:** `frontend`
- **Build Command:** `pip install -r ../requirements.txt`
- **Start Command:** `streamlit run App.py --server.port $PORT --server.address 0.0.0.0`
- **Environment Variables:**
  - `PYTHON_VERSION=3.11.9`
  - `BACKEND_URL=https://<your-backend>.onrender.com`

## Sanity checks
- Open `https://<backend>.onrender.com/` (should return JSON)
- Open `https://<backend>.onrender.com/health` (should return `{"status":"healthy"}`)
- Send `POST https://<backend>.onrender.com/assist`

> Note: `Not Found` on `/` means backend code is old or deploy did not pick latest commit.
