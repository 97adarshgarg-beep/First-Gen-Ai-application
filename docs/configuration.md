# Configuration & Setup

## Requirements
- Python 3.8+
- Packages from `requirements.txt`

## Install
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## Environment variables
- `GEMINI_API_KEY`: Your Google Gemini API key

You can provide it via:
- `.env` file (auto-loaded by the apps)
- OS environment variable
- Sidebar input in `app.py`

Example `.env`:
```env
GEMINI_API_KEY=your_actual_api_key_here
```

## Running the apps
```bash
streamlit run app.py
# or
streamlit run streamlit_widgets_demo.py
```

## Troubleshooting
- Ensure the API key is set and valid
- Upgrade `google-generativeai` if you see model-not-found errors
- If images are large, downscale before sending to the model