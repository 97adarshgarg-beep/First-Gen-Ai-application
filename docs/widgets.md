# Widgets Demo (`streamlit_widgets_demo.py`)

A compact tour of Streamlit widgets, session state, caching, and simple chat UI preview.

## Run
```bash
streamlit run streamlit_widgets_demo.py
```

## Highlights
- Sidebar with a visit counter using `st.session_state`
- Inputs: text, number, checkbox, selectbox, slider
- File upload with image preview
- Cached helpers: `count_text_bytes`, `get_placeholder_image`
- Chat UI preview using `st.chat_message` and `st.chat_input`

## Usage walkthrough
1. Enter your name and age; toggle the mood and confidence level
2. Upload an image to preview; otherwise a placeholder is shown
3. Type into the chat input to see messages echoed back

## Public helpers
### `count_text_bytes(text: str) -> int`
Returns byte-length of a string. Cached via `st.cache_data`.

### `get_placeholder_image() -> PIL.Image.Image`
Returns a generated placeholder image. Cached via `st.cache_resource`.

## Tips
- Explore the raw session state via the expander in the right column
- Caching reduces recomputation for repeated inputs
- Use this file as a template for broader UI experiments