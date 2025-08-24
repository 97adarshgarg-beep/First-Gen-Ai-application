# Gemini Chat App (`app.py`)

A multi-turn chat interface powered by Google's Gemini models with configurable parameters and session history.

## Features
- Model selection: `gemini-2.0-flash`, `gemini-1.5-flash`, `gemini-2.5-flash`
- System instruction to steer behavior
- Generation parameters: temperature, top-p, top-k, max tokens
- Persistent session history via `st.session_state`
- Chat UI using `st.chat_message` and `st.chat_input`

## Run
```bash
streamlit run app.py
```
Open your browser at `http://localhost:8501`.

## Configuration
- Provide `GEMINI_API_KEY` in the sidebar or via environment variables.
- See [Configuration & Setup](./configuration.md) for details.

## How it works
1. Reads API key and settings from the sidebar
2. Caches a `genai.GenerativeModel` via `get_model(...)`
3. Maintains `st.session_state.messages` and starts a chat session
4. Sends user prompts and renders assistant responses in the chat UI

## Example usage
- Set system instruction: "You are a concise, helpful assistant."
- Select `gemini-2.0-flash`, temperature 0.7, top-p 0.9, top-k 40
- Ask: "Summarize the benefits of testing in one paragraph."

## Error handling
- If the SDK is missing, you will see `ImportError`
- If `GEMINI_API_KEY` is missing, a helpful error is displayed
- Model call exceptions are caught and shown inline in the chat

## Tips
- Lower temperature for focused, deterministic answers
- Increase max tokens for longer outputs
- Use system instruction to set tone and constraints