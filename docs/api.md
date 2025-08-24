# API Reference

This project exposes public user-facing components through Streamlit apps and a few cached helpers. Below is a consolidated reference.

## Module: `app.py`

### Function: `get_model(api_key: str, model_name: str, system_instruction: str) -> GenerativeModel`
Creates and caches a Google Generative AI model instance.

- Parameters:
  - `api_key`: Your Gemini API key.
  - `model_name`: e.g., `"gemini-2.0-flash"`, `"gemini-1.5-flash"`, `"gemini-2.5-flash"`.
  - `system_instruction`: System prompt to steer responses.
- Raises:
  - `ImportError` if `google-generativeai` is not installed.
  - `ValueError` if `api_key` is missing.
- Returns:
  - `genai.GenerativeModel` instance configured with the provided parameters.

Example:
```python
from app import get_model
model = get_model(api_key, "gemini-2.0-flash", "You are a concise assistant.")
resp = model.generate_content("Say hi!")
print(resp.text)
```

### Session State
- `st.session_state.messages: list[dict]` — chat history with `{"role": "user|assistant", "content": str}`
- `st.session_state.chat` — Gemini chat session created via `model.start_chat(...)`

### Streamlit Components
- Sidebar controls:
  - `st.text_input` for `GEMINI_API_KEY`
  - `st.selectbox` for model selection
  - `st.text_area` for system instruction
  - Sliders for temperature, top-p, top-k, max tokens
- Chat UI:
  - `st.chat_message` to render messages
  - `st.chat_input` to accept user prompts

## Module: `streamlit_widgets_demo.py`

### Function: `count_text_bytes(text: str) -> int`
Returns the byte-length of a string. Cached with `st.cache_data`.

Example:
```python
from streamlit_widgets_demo import count_text_bytes
print(count_text_bytes("hello"))  # 5
```

### Function: `get_placeholder_image() -> PIL.Image.Image`
Returns a small generated placeholder image. Cached with `st.cache_resource`.

Example:
```python
from streamlit_widgets_demo import get_placeholder_image
img = get_placeholder_image()
# Use in your UI: st.image(img)
```

### Streamlit Components
- Sidebar: title, visit counter (`st.sidebar.metric`)
- Inputs: `st.text_input`, `st.number_input`, `st.checkbox`, `st.selectbox`, `st.slider`, `st.file_uploader`
- Display: `st.image`, `st.code`, `st.json`, `st.info`
- Chat preview: `st.chat_message`, `st.chat_input`

## Notebook: `gemini_basics.ipynb`
Key code cells demonstrate:
- Client configuration via `google.generativeai`
- Text generation with `generation_config`
- Multi-turn chat via `model.start_chat`
- Text + image prompts using byte payloads

Example snippet:
```python
import google.generativeai as genai
model = genai.GenerativeModel("gemini-2.0-flash")
resp = model.generate_content("Hello")
print(resp.text)
```