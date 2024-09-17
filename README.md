# MetaReflexion with Ollama

MetaReflexion is an AI-driven architecture built to generate responses, evaluate them, and refine the output iteratively through self-reflection and judgment. This module integrates with the Ollama API to perform multiple rounds of generation, evaluation (judging), and improvement (refining) of text outputs based on given prompts.

## Features

- **Actor**: Generates responses using Ollama models.
- **Judge**: Evaluates the responses based on a customizable judging prompt.
- **MetaJudge**: Compares and ranks judgments using meta-evaluation.
- **Self-Refinement**: Refines the response iteratively based on the best judgment, to achieve optimal output quality.

## Installation

### Requirements

You need to have Python installed on your system along with the dependencies listed in `requirements.txt`. To install the required dependencies:

```bash
pip install -r requirements.txt
```

### Dependencies

- `ollama` - Ollama API client to generate responses.
- `numpy` - For calculating variances and means in judgments.
- `json` - For handling JSON-based prompts and responses.

Make sure to add any other relevant dependencies to your `requirements.txt` file if needed.

## Usage

1. **Import Prompts**

   The necessary prompts (`SYS_PROMPT`, `JUDGE_PROMPT`, `METAJUDGE_PROMPT`, `IMPROVE_PROMPT`) and model name (`MODEL_NAME`) should be provided in the `prompts.py` file.

   ```python
   from prompts import SYS_PROMPT, JUDGE_PROMPT, METAJUDGE_PROMPT, IMPROVE_PROMPT, MODEL_NAME
   ```

2. **Create an Instance of MetaReflexion**

   Create an instance of the `MetaReflexion` class, passing in the model name and prompt configurations.

   ```python
   from ollama_meta_reflexion import MetaReflexion

   metareflexion_instance = MetaReflexion(
       model_name=MODEL_NAME,
       judge_prompt=JUDGE_PROMPT,
       sys_prompt=SYS_PROMPT,
       metajudge_prompt=METAJUDGE_PROMPT,
       improve_prompt=IMPROVE_PROMPT
   )
   ```

3. **Run the Task**

   Define your task as a string and run the MetaReflexion instance, specifying the number of iterations and judgments for each iteration.

   ```python
   task = "Explain the importance of renewable energy."
   output = metareflexion_instance.run(task, max_iterations=3, max_judgements=5)
   print(output)
   ```

   The `run()` function will return the final refined response based on multiple rounds of self-evaluation and refinement.

## File Structure

- **ollama_meta_reflexion.py**: Contains the `MetaReflexion` class with all the core logic for response generation, judgment, meta-judgment, and self-refinement.
- **prompts.py**: Holds all the prompts (`SYS_PROMPT`, `JUDGE_PROMPT`, `METAJUDGE_PROMPT`, `IMPROVE_PROMPT`) required for the system.
- **sample.py**: A sample script that demonstrates how to use the `MetaReflexion` module with Ollama to process tasks.
- **requirements.txt**: A file listing all the Python dependencies for this project.

## Prompts Configuration

You can modify the `SYS_PROMPT`, `JUDGE_PROMPT`, `METAJUDGE_PROMPT`, and `IMPROVE_PROMPT` in `prompts.py` according to your project requirements.

### Example Prompt Definitions

Here's a sample structure for the prompts:

```python
# prompts.py

MODEL_NAME = "llama"

SYS_PROMPT = "You are a helpful assistant..."

JUDGE_PROMPT = "Evaluate the given response based on..."

METAJUDGE_PROMPT = "Compare two judgments and select the better one..."

IMPROVE_PROMPT = "Refine the response based on the best judgment..."
```

## Contributing

Feel free to fork this repository, submit issues, or make pull requests to improve MetaReflexion or adapt it for other use cases.
