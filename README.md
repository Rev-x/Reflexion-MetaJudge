# Reflexion-MetaJudge

This project is an implementation and improvement of the frameworks proposed in the papers:

- [LLM as a Meta-Judge](https://arxiv.org/abs/2407.19594)
- [Reflexion](https://arxiv.org/abs/2303.11366)

## Setup

1. Clone the repository:

   ```
   git clone https://github.com/Rev-x/Reflexion-MetaJudge.git
   ```
2. Navigate to the project directory:

   ```
   cd Reflexion-MetaJudge
   ```
3. Install the required dependencies:

   ```
   pip install -r requirements.txt
   ```

## Configuration

Before running the project, you need to configure a few files:

1. Update `prompts.py` with your specific use case.
2. If you plan to use Hugging Face models:

   - Install the Hugging Face CLI:
     ```
     pip install -U "huggingface_hub[cli]"
     ```
   - Log in to Hugging Face and generate an "allow gated models" token.
   - Use the token to log in via the command line:
     ```
     huggingface-cli login
     ```
   - Paste the token when prompted.
3. Update `constants.py` with your preferred model names:

   - For Hugging Face: Update `MODEL_PATH`
   - For Ollama: Update `MODEL_NAME`

## Usage

You have three options for running the project:

### 1. Using Ollama Framework

1. Navigate to the Ollama directory:

   ```
   cd ollama
   ```
2. Modify `sample.py` according to your task and parameters.
3. Run the script:

   ```
   python sample.py
   ```

### 2. Using Hugging Face Framework

1. Ensure you've completed the Hugging Face CLI login steps mentioned in the Configuration section.
2. Modify `sample.py` according to your task and parameters.
3. Run the sample script:

   ```
   python sample.py
   ```

### 3. Using the Pipeline (Ollama and Hugging Face)

To use both frameworks in a pipeline:

1. Ensure you've updated `constants.py` and `prompts.py` as mentioned in the Configuration section.
2. Run the meta-reflection script:

   ```
   python meta_reflexion.py
   ```
3. When prompted, enter 'o' for Ollama or 'h' for Hugging Face to decide which model to use.

## Important Notes

- Always update `prompts.py` and `constants.py` before running any scripts.
- For Hugging Face usage, logging in via the CLI is crucial.
- The pipeline option (metareflection.py) allows you to choose between Ollama and Hugging Face models at runtime.
- When running metareflection.py, you will be prompted to enter 'o' for Ollama or 'h' for Hugging Face to select the model.

## Contributing

Contributions to improve this framework are welcome. Please feel free to submit issues or pull requests.

## Acknowledgements

This project builds upon the research presented in:

- "LLM as a Meta-Judge" (https://arxiv.org/abs/2407.19594)
- "Reflexion" (https://arxiv.org/abs/2303.11366)
