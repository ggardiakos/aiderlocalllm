<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeepSeek-Coder-V2 Setup and Aider Integration</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            line-height: 1.6;
        }
        h1, h2, h3 {
            color: #333;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            white-space: pre-wrap;
        }
        code {
            background-color: #eee;
            padding: 2px 4px;
            border-radius: 4px;
        }
        ul {
            list-style-type: square;
        }
    </style>
</head>
<body>

    <h1>DeepSeek-Coder-V2 Setup and Aider Integration</h1>

    <p>This project automates the setup of DeepSeek-Coder-V2, a code generation model, and integrates it with Aider, an AI-powered code assistant. The setup script handles everything from environment setup to running a local API server.</p>

    <h2>Prerequisites</h2>
    <p>Ensure the following software is installed:</p>
    <ul>
        <li><strong>Python 3.8+</strong></li>
        <li><strong>Git</strong></li>
        <li><strong>Virtualenv</strong> (run: <code>python3 -m venv</code>)</li>
    </ul>

    <h2>Installation</h2>

    <h3>1. Clone the Repository</h3>
    <p>Clone the DeepSeek-Coder-V2 repository:</p>
    <pre><code>git clone &lt;REPO_URL&gt; &lt;REPO_DIR&gt;</code></pre>

    <h3>2. Set Up Python Virtual Environment</h3>
    <p>Create and activate a Python virtual environment:</p>
    <pre><code>python3 -m venv &lt;VENV_DIR&gt;
source &lt;VENV_DIR&gt;/bin/activate</code></pre>

    <h3>3. Install Dependencies</h3>
    <p>The script installs required dependencies from <code>requirements.txt</code>. If the file doesn't exist, the script will create one with the following dependencies:</p>
    <pre><code>torch
transformers
fastapi
uvicorn
pydantic
requests
vllm</code></pre>

    <p>To install the dependencies:</p>
    <pre><code>pip install --upgrade pip
pip install -r requirements.txt</code></pre>

    <h3>4. Download Pre-trained Models</h3>
    <p>Download the pre-trained models from Hugging Face using the following command:</p>
    <pre><code>python -c "from transformers import AutoTokenizer, AutoModelForCausalLM; AutoTokenizer.from_pretrained('deepseek-ai/deepseek-coder-6.7b-base', trust_remote_code=True); AutoModelForCausalLM.from_pretrained('deepseek-ai/deepseek-coder-6.7b-base', trust_remote_code=True)"</code></pre>

    <h3>5. Set Up the Local LLM API with FastAPI</h3>
    <p>A FastAPI server is created and run locally to serve the LLM for code completion. The server is started on the specified port:</p>
    <pre><code>nohup uvicorn local_llm_api:app --host 0.0.0.0 --port &lt;API_PORT&gt; &gt; api_server.log 2&gt;&1 &</code></pre>

    <h3>6. Configure Aider</h3>
    <p>Install Aider using <code>pip</code>:</p>
    <pre><code>pip install aider</code></pre>

    <h3>7. Run Aider on a Sample File</h3>
    <p>After installation, you can test Aider on a sample file. The script will create a <code>sample.py</code> file if one doesn't exist.</p>
    <p>Example sample file (<code>sample.py</code>):</p>
    <pre><code>def add(a, b):
    return a + b</code></pre>

    <p>Run Aider on the sample file:</p>
    <pre><code>aider sample.py</code></pre>

    <h2>Environment Variables</h2>
    <p>Ensure the following environment variables are set in your shell configuration file (e.g., <code>.bashrc</code>, <code>.zshrc</code>):</p>
    <pre><code>export OPENAI_API_KEY=dummy_key
export OPENAI_API_BASE=http://localhost:&lt;API_PORT&gt;
export PATH="&lt;VENV_DIR&gt;/bin:$PATH"</code></pre>

    <p>After modifying the shell configuration file, run:</p>
    <pre><code>source &lt;SHELL_CONFIG_FILE&gt;</code></pre>

    <h2>Contributing</h2>
    <p>Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.</p>

    <h2>License</h2>
    <p>This project is licensed under the MIT License.</p>

</body>
</html>
