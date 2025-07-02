# **Adversarial Reasoning at Jailbreaking Time**
This is the official implementation of our paper in ICML 2025 "[Adversarial Reasoning at Jailbreaking Time](https://arxiv.org/abs/2502.01633)".

## Abstract
As large language models (LLMs) are becoming more capable and widespread, the study of their failure cases is becoming increasingly important. 
Recent advances in standardizing, measuring, and scaling test-time compute suggest new methodologies for optimizing models to achieve high performance on hard tasks.
In this paper, we apply these advances to the task of ``model jailbreaking'': eliciting harmful responses from aligned LLMs.
We develop an adversarial reasoning approach to automatic jailbreaking via test-time computation that achieves SOTA attack success rates (ASR) against many aligned LLMs, even the ones that aim to trade inference-time compute for adversarial robustness. Our approach introduces a new paradigm in understanding LLM vulnerabilities, laying the foundation for the development of more robust and trustworthy AI systems.
![Screenshot of the Application](data/Overall.png)

## Getting started
Before running the experiments, you need to configure your API keys, log in to your WandB account, and set the target LLM address.
- To query the black-box models, you must provide your API key(s) as environment variables. For example, if you are using TogetherAI’s API, set the key as follows:
  ```
  export TOGETHERAI_API_KEY=[YOUR_API_KEY_HERE]
  ```
  Alternatively, you can set your key in the first cell of `perc.ipynb`. 

- Log in to your WandB account (used for logging) before running the code. You can do this by running `wandb login`.

- To read log-probability vectors from the target LLM, specify the appropriate address in the second cell of perc.ipynb.

## Run Experiments
For the demo, run the notebook perc.ipynb which loads the target LLM and executes the attack. If you are attacking a black-box model, you will need to:
- Specify the address of the surrogate model in the notebook, and
- Call `get_target_responses_API_prop` from `utils.py` to query the black-box LLM.
  

The default parameters for the attack are `num_iters = 15` (number of iterations for refinement), `num_branches = 8` (number of genrated children from each reasoning string), `memory = 32` (buffer size for the search method), and `K = 2` (bucket size for adding randomness to the feedabacks). 
