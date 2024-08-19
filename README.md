# person_detection_and_image_inpainting

# Project Title: Image Inpainting - I/O Framework

## Team:
Team #2 - Daniel Yohan & Lilach Cohen

## Description:
This project focuses on image inpainting, where we developed a model to generate alternative synthesized content in place of missing or masked regions of images. Using a pretrained model from the “places2” and “celebA” datasets, as described in the paper “Free-Form Image Inpainting with Gated Convolution,” our approach aims to replace “empty masks” in images with realistic backgrounds that seamlessly blend with the original image.

## Technology Utilized:

Pretrained model on “places2” and “celebA” datasets
Spectral-Normalized Patch GAN
Gated Convolutions
Markovian patches for the discriminator
Model Overview:
Our model utilizes a Spectral-Normalized Patch GAN, consisting of two neural networks: a generator and a discriminator. The generator employs Coarse and Refinement networks, built with Gated Convolutions, to fill in missing parts of the image based on the given mask. The discriminator uses convolutional networks to evaluate the inpainted images, ensuring that the output is realistic by focusing on different locations and semantics within the input data.

## Functionality:

Image Inpainting: Replace masked regions with a realistic, generated background.
Contextual Attention: Captures long-range spatial dependencies to improve the handling of free-form masks.
Workflow:
Initially, we attempted to create a custom generative model but faced computational challenges. We then transitioned to using a pretrained model ranked #3 on the Places2 dataset, which was specifically designed for free-form inpainting. The model was tested on images and masks from the COCO dataset. We also refined and adjusted the masks provided by team #1 using classical computer vision techniques before running them through our pipeline.

## Results:
The model produced satisfactory inpainting results overall. It performed well with natural backgrounds but struggled with complex patterns and detailed backgrounds. Issues such as color reproduction and maintaining object consistency were noted, indicating areas for further improvement.


## Acknowledgements

This project was inspired by and built upon the work from the following repository:

- [nipponjo/deepfillv2-pytorch](https://github.com/nipponjo/deepfillv2-pytorch): A PyTorch reimplementation of the paper Free-Form Image Inpainting with Gated Convolution (DeepFillv2).
