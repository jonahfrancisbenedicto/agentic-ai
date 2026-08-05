# Onboarding

1. Create a hugging face account.
2. Run Model Locally with Ollama
    1. [Install Ollama](https://ollama.com/download)
    2. Pull model locally
    
    ```bash
    ollama pull qwen2:7b
    ```

    3. Run Ollama
    
    ```bash
    ollama serve
    ```

    4. Use `LiteLLMModel` Instead of `InferenceClientModel`
    
        **Create and change directory:**
        ```bash
        mkdir <directory>
        cd <directory>
        ```
        **Setup virtual environment:**
        ```bash
        python3 -m venv venv
        ```
        **Activate virtual environment:**
        ```bash
        source venv/bin/activate
        ```
        **Install Lite LLM Model:**
        ```bash
        pip3 install 'smolagents[litellm]'
        ```
        **Initialise Lite LLM Model:**
        ```python
        from smolagents import LiteLLMModel

        model = LiteLLMModel(
            model_id="ollama_chat/qwen2:7b",
            api_base="http://127.0.0.1:11434",
            num_ctx=8192,
        )
        ```
