# Notebook: Gemini Basics (`gemini_basics.ipynb`)

Demonstrates Gemini 2.0 Flash basics:
- Client setup with API key
- Text generation with `generation_config`
- Multi-turn chat with `model.start_chat`
- Text + image prompts using raw bytes

## Run locally
1. Create a virtual environment and install dependencies
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install pillow jupyter
```
2. Set `GEMINI_API_KEY` in your environment or `.env`
3. Launch Jupyter and open the notebook
```bash
jupyter notebook
```

## Key cells
- Configure client and model name: `gemini-2.0-flash`
- Generation parameters: temperature, top_p, top_k, max_output_tokens
- Start a chat and send messages
- Optional: provide an image via `Path("images.jpeg")`

## Notes
- If you see permission or model errors, upgrade the SDK and validate access
- Keep API keys secure; do not commit `.env` files