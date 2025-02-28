# CustomGPT-LLM Hugging Face Space Setup

This guide provides step-by-step instructions for setting up a Hugging Face Space with a fine-tuned CustomGPT-LLM model.

## Overview

We will create a Hugging Face Space, clone necessary repositories, and push a fine-tuned model with the required code to deploy a working instance of CustomGPT-LLM.

## Prerequisites

- A Hugging Face account
- Git installed on your local machine
- Git Large File Storage (LFS) installed
- Access to the required model checkpoints

## Setup Instructions

### 1. Create a Hugging Face Space

1. Go to [Hugging Face New Space](https://huggingface.co/new-space).
2. Select a random Gradio template.
3. Name the space accordingly: **customgpt-llm** for example.
4. Choose a GPU with **>20GB VRAM** (1xL4 is recommended).
5. Click "Create Space".

### 2. Clone the Hugging Face Repository

Run the following command to clone the newly created Space locally:

```bash
git clone https://huggingface.co/spaces/customgpt/customgpt-llm customgpt-space
```

### 3. Clone the Fine-Tuned Model Checkpoints Repository

First, ensure that Git LFS is installed:

```bash
git lfs install
```

Then, clone the repository containing the fine-tuned checkpoints and gradio app:

```bash
git clone https://huggingface.co/customgpt/customgpt-llm customgpt-checkpoints
```

### 4. Copy the Code and Checkpoints

Move the cloned files from step 3 into the repository cloned in step 2:

```bash
cp -r customgpt-checkpoints/* customgpt-space/
```

### 5. Navigate to the Repository Directory

```bash
cd customgpt-space
```

### 6. Push the Code to Hugging Face Space

Commit and push the changes to update the Hugging Face Space:

```bash
git add .
git commit -m "Add fine-tuned model and setup files"
git push
```

## Deployment

Once the push is complete, the Hugging Face Space will automatically spin up and deploy the CustomGPT-LLM instance.

## Usage

You can interact with the chatbot in two ways:

1. **Through the UI:** Once the Hugging Face Space is live, you can chat directly with the chatbot via the Gradio-based interface.
2. **Using an API endpoint:** You can send messages programmatically using the `gradio_client` package:

```python
from gradio_client import Client

client = Client("customgpt/llm")

result = client.predict(
    message="what is customGPT?",
    history=[],
    api_name="/predict"
)
print(result)
```

## Troubleshooting

- Ensure you have Git LFS installed and set up correctly.
- Verify that you have the correct permissions to push to the Hugging Face Space.
- Check the logs in the Hugging Face Space UI if the deployment fails.

---

This process ensures that your Hugging Face Space is correctly configured and ready to run the fine-tuned CustomGPT-LLM model.