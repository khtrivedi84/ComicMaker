# ComicMaker

Welcome to the Comic Maker project! This repository provides a creative tool that combines the power of Dreambooth, Stable Diffusion, and OpenAI API to generate custom comic book panels based on user-provided images.


## Overview

Comic Maker utilizes a combination of cutting-edge techniques to create unique and personalized comic book panels. It leverages the following components:

Dreambooth: A technique that injects subject images into a text-to-image model, known as Stable Diffusion. By incorporating user-provided images, Dreambooth enables the generation of new images of the subject.

Stable Diffusion: A text-to-image model that has been fine-tuned using Dreambooth to include user images. This model generates images based on pre-defined text prompts, providing a visual representation of the desired comic book scenes.

OpenAI API: The GPT-3.5-turbo model is utilized to generate the pre-defined text prompts for the Stable Diffusion model. The prompts are engineered within the code to create a concise storyline with five dialogues.


## Getting Started

### Installation

To use Comic Maker, follow these steps:

Clone this repository to your local machine.

```bash
  git clone https://github.com/kishan12345/ComicMaker.git
```
In the first cell of the notebook, make following changes: 
```bash
  openai.api_key = '<YOUR_KEY>'
  HUGGINGFACE_TOKEN = '<YOUR_TOKEN>'
```
       
Run cell 1 and 2 to install the dependencies

## Model Training

This is the most crucial part of the project. The following parameters were used by me to train the model based on my image dataset and might need to be updated based on your dataset if the output is not as desired.

Learning rate should be either 1e-6 or 2e-6 while max_train_steps can be ( number_of_images_in_dataset * 100 ). For example, if training data has 10 user images, --max_train_steps will be 1000).

```bash
   --instance_prompt="photo of <your_initials> person" 
   --learning_rate=1e-6 
   --max_train_steps=1000
```
--instance_data_dir is the path to user images

  ```bash
   --instance_data_dir="<YOUR_PATH_TO_IMAGES>" \
```
If the model is overfitting, the max_train_steps can be reduced gradually by 100 until an acceptable output is obtained. Similarly, in case it is underfitting, the steps can be increased by 100.

## Model Inference

If a powerful GPU is available, the below line of code in the Model inference step can be commented. Else, it is recommended to run it.

```bash 
  pipe.enable_xformers_memory_efficient_attention()
```

## Comic generation

Run the Comic Generation cell and you'll be prompted for two inputs.

For "Clothing Style", you can use a super hero costume like Iron man armor.

For image style, it is recommended to use "Oil painting" or "Watercolor painting" for best results.


## Screenshots

Sample image 1

Inputs:
Clothing Style: Superman Costume
Image style: Watercolor painting

![App Screenshot](https://i.imgur.com/wzJ8gcL.jpg)

Sample image 2

Clothing Style: Green lantern costume
Image style: Oil painting

![App Screenshot](https://i.imgur.com/aACPtaG.jpg)

More samples are available in Sample Outputs folder.


## References

OpenAI: https://openai.com/blog/openai-api

Stable Diffusion 1.5: https://huggingface.co/runwayml/stable-diffusion-v1-5

HuggingFace: https://huggingface.co/

ShivamShrirao's github repo: https://github.com/ShivamShrirao/diffusers

Model was trained based on recommendations on this post and by few other youtube tutorials: https://wandb.ai/psuraj/dreambooth/reports/Training-Stable-Diffusion-with-Dreambooth--VmlldzoyNzk0NDc3


## Authors

- [@kishan12345](https://github.com/kishan12345)
