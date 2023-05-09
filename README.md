# OpenGPT

A framework for creating grounded instruction based datasets and training conversational domain expert Large Language Models (LLMs). Read more in our blog post: <<<<<<<<< LINK

<p align="center">
  <img height='300px' src='https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffeb6ed86-0dc8-42b8-84e4-9e09f5c95d6b_1318x688.png' />
</p>


## NHS-LLM
A conversational model for healthcare trained using OpenGPT. All the datasets used to train this model were created using OpenGPT and are available below. If you want to learn more about the model have a look at our blogpos. [LINK]

## Available datasets (`./data` folder)
- [NHS UK](./data) Q/A, 24,665 Questions and Answers, Prompt used: f53cf99826, Generated using data available on the [NHS UK Website](https://www.nhs.uk/conditions/)
- [NHS UK](./data) Conversations, 2,354 unique conversations, Prompt used: f4df95ec69, Generated using data available on the [NHS UK Website](https://www.nhs.uk/conditions/)
- [Medical Task/Solution](./data), 4688 pairs generated using GPT-4, prompt used: 5755564c19

We also have a couple of small datasets for testing available in the `./data/example_project` and `nhs_conditions_small_sample` folder.

## Installation
```
pip install opengpt
```
If you are working with LLaMA models, then install the extra requirements from the repo:
```
pip install ./train_requirements.txt
```

## How to

OpenGPT helps to train conversational LLMs and create grounded instruction based datasets using OpenAI ChatGPT, or Google Bard, or any other *Teacher* model. In some way it is similar to Alpaca by Standford, but grounds the instructions in a certain domain and accurate information.

The config files available in `./configs` control the whole workflow, make sure to go through them. I've also provide three Jupyter notebooks (in `./experiments`) that can be used to *Create prompts*, *Generate datasets* and *Train models*.

1. We start by collecting a base dataset in a certain domain. For example, collect definitions of all disases (e.g. from the NHS UK website). Sample dataset HERE, it is important that the collected dataset has a column named `text` where each row of the CSV has one disease definition.

2. Create prompts or use existing prompts from the prompt database (link). A prompt will be used to generate tasks/solutions based on the `context` (the dataset collected in step 1.)
  - Once we have a prompt (or many of them), we edit the config file for dataset generation and add the appropirate promtps and datasets.
  - Run the Dataset creation notebook (link)

3. Edit the `train_config` file and add the datasets you want to use for training.
