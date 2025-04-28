# POC on Self-Learning Capabilities of the OpenAI Engine

## Overview
This proof of concept (POC) explores the possibility of improving OpenAI prompt performance through iterative self-learning, using OpenAI itself as both the model and the optimizer.

## Goal
The main objective is to validate whether it is feasible to automatically refine prompts based on feedback from classification tasks, leading to improved performance without manual intervention.

## Experiment Design
- A labeled dataset is used alongside an initial starting prompt.
- For each input, the model is queried to classify it according to the prompt.
- If the model fails to predict the correct label, a technical request is made to OpenAI to generate an improved version of the prompt aimed at better classification.
- The cycle continues: the newly generated prompt is then used for further predictions and evaluated again.
- Throughout the process, detailed statistics are collected for each version of the prompt, including classification accuracy and error patterns.

## Technologies
- **Azure OpenAI Service** — used for prompt execution and self-optimization requests.
- **Python** — for orchestration of experiments and data handling.

## Architecture
The system consists of:
- A data manager that iterates over the dataset and submits prompts to Azure OpenAI.
- A feedback loop that detects misclassifications and generates new optimized prompts through meta-requests to OpenAI.
- A statistics tracker that records prompt performance metrics for analysis and comparison.

## Notes
- Prompt evolution is fully automatic based on model responses and errors.
- No manual intervention is involved in adjusting or crafting prompts.
- Statistical analysis over time will determine whether the self-learning approach provides significant improvements.
