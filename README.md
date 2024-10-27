


# Streamlit Chat Widget

![Streamlit Chat Widget](https://path-to-your-image/streamlit_chat_widget.png)

The `streamlit_chat_widget` is a custom chat input component designed for Streamlit applications, allowing users to send text and audio messages seamlessly. This widget can be integrated into Streamlit apps, making it ideal for building conversational AI interfaces, voice assistants, or any chat-based applications the component was developed by Mohammed Bahageel artificial Intelligence developer.

## Features

- **Text Input**: Users can type text messages and send them.
- **Audio Recording**: Built-in microphone functionality to capture audio messages.
- **Fixed Positioning**: The widget remains fixed at the bottom of the Streamlit app, similar to Streamlit's `st.chat_input`.

## Installation

Install the package directly from PyPI:

```bash
pip install streamlit_chat_widget
```

## Setup

### Step 1: Import and Initialize the Component

To use the component, import it into your Streamlit app. The widget will display at the bottom of the screen by default.

### Step 2: Set Up the Frontend Component

If you want to modify or rebuild the React component, you can find the source code in the `frontend` directory.

1. **Navigate to the `frontend` folder**:
   ```bash
   cd streamlit_chat_widget/frontend
   ```
2. **Install dependencies**:
   ```bash
   npm install
   ```
3. **Build the frontend**:
   ```bash
   npm run build
   ```
4. **Run the component locally** (for development):
   ```bash
   npm start
   ```

### Usage

Here’s a sample code to get you started with `streamlit_chat_widget`:

```python
import streamlit as st
from streamlit_chat_widget import chat_input_widget

def main():
    st.title("My Custom Chat Application")
    
    # Initialize chat history in Streamlit session state
    if "chat_history" not in st.session_state:
        st.session_state.chat_history = []

    # Display the chat history
    for message in st.session_state.chat_history:
        st.write(message)

    # Display the chat input widget at the bottom
    response = chat_input_widget()

    # Process the user's input from the widget
    if response:
        if "text" in response:
            user_text = response["text"]
            st.session_state.chat_history.append(f"You: {user_text}")
        elif "audioFile" in response:
            # Handle audio file processing
            audio_bytes = bytes(response["audioFile"])
            st.audio(audio_bytes)

if __name__ == "__main__":
    main()
```

## Example

To create a simple app with the chat widget:

```python
import os
import streamlit as st
from streamlit_chat_widget import chat_input_widget

def app():
    st.title("Doctor AI Assistant")
    
    if "chat_history" not in st.session_state:
        st.session_state.chat_history = [
            "Hello! I am your Doctor AI Assistant. How can I help you?"
        ]

    # Display chat history
    for message in st.session_state.chat_history:
        st.write(message)

    # Display the chat input widget at the bottom
    response = chat_input_widget()

    if response:
        if "text" in response:
            user_text = response["text"]
            st.session_state.chat_history.append(f"You: {user_text}")
        elif "audioFile" in response:
            audio_bytes = bytes(response["audioFile"])
            st.audio(audio_bytes)

if __name__ == "__main__":
    app()
```

### CSS Customization

To style the widget or customize its appearance, add custom CSS in your Streamlit app. Here’s a basic example:

```python
st.markdown("""
<style>
.chat-container {
    position: fixed;
    bottom: 0;
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
}
</style>
""", unsafe_allow_html=True)
```

### License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

---

This is a powerful, customizable chat widget for Streamlit applications. Feel free to contribute to its development or open issues for any bugs or feature requests!
```