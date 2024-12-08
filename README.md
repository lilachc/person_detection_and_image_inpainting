# Image Inpainting Framework

![Example Image](example.png)

## Project Overview
This project, developed by **Team #2: Daniel Yohan & Lilach Cohen**, focuses on implementing an image inpainting framework to synthesize realistic content in masked regions of images. Leveraging a pretrained generative adversarial network (GAN) model, the project aims to seamlessly replace empty or missing regions in images while maintaining high visual fidelity.

## Objectives
1. Perform image inpainting to replace masked areas with realistic synthesized content.
2. Utilize and evaluate a pretrained model based on the paper ["Free-Form Image Inpainting with Gated Convolution"](https://paperswithcode.com/paper/free-form-image-inpainting-with-gated).
3. Assess the model’s performance on various datasets and refine inputs for optimal results.

## Input and Output
- **Input**: Original images and corresponding masks.
- **Output**: Inpainted images where masked areas are replaced with synthesized content.

### Example
Using the pretrained model, masked regions in the input image are replaced with realistic content that mimics the original image's natural appearance.

## Technology Utilized
- **Pretrained Model**: A GAN model trained on the "Places2" and "CelebA" datasets.
- **Model Type**: Spectral-Normalized Patch GAN, incorporating Gated Convolutions for free-form image inpainting.

## Model Architecture
### Generator
- Comprises **Coarse** and **Refinement Networks**, each structured as encoder-decoder networks utilizing **Gated Convolutions**.
- The convolution operations consider masked pixels as invalid and apply only to valid pixels. Masks are learned iteratively and include **Dilated Gated Convolutions**.
- Features a **Contextual Attention Layer** to capture long-range spatial dependencies and handle free-form masks effectively.

### Discriminator
- A convolutional network evaluating Markovian patches within input images.
- Operates on various locations and semantics, enhancing its feedback quality for the generator.

### Loss Function
- Balanced ratio (1:1) of:
  - **Hinge Loss**: Applied per point on the discriminator’s output map.
  - **L1 Reconstruction Loss**: Pixel-wise loss for image reconstruction.

## Workflow
1. Initially aimed to develop a custom generative model but shifted to leveraging a pretrained model due to computational constraints.
2. Selected a pretrained model ranked #3 on the Places2 dataset, specifically designed for free-form inpainting.
3. Evaluated the model using images and masks from the COCO dataset and improved the masks using classical computer vision techniques.
4. Processed masks provided by Team #1, refining them to improve inpainting results.

## Results
### Inpainting Results with Original Dataset Masks
- **Strengths**:
  - High-quality results for natural backgrounds without distinct shapes or patterns.
  - Realistic and seamless integration of inpainted regions in simpler scenes.
- **Challenges**:
  1. Inconsistent inpainting when objects attached to a person (e.g., shadows, skates) were excluded from masks.
  2. Difficulty handling complex backgrounds with intricate patterns.
  3. Color reproduction issues in some inpainted areas.
  4. Smudged textures, detracting from visual quality.

### Inpainting Results with Team #1’s Masks
- Initial results were mediocre due to incomplete masks.
- Refining the masks by thickening and smoothing significantly improved results.
- Primary issues arose from incomplete masking, where residual person segments remained.

### Overall Observations
- The model performed better with high-quality, accurate masks and smaller masked segments.
- Simpler architectural design yielded good results, but limitations were evident in texture replication and complex scenes.

## Future Work
1. Address texture replication issues and enhance consistency in complex scenes.
2. Explore alternative models, such as those based on stable diffusion, for improved performance.
3. Experiment with additional datasets and training methods to enhance versatility.

## Tools and Libraries
- **Programming Language**: Python
- **Libraries**: PyTorch, OpenCV, NumPy
- **Datasets**: Places2, CelebA, COCO

## Team Members
- **Daniel Yohan**
- **Lilach Cohen**

## Acknowledgements

This project was inspired by and based on the work from the following repository:

- [nipponjo/deepfillv2-pytorch](https://github.com/nipponjo/deepfillv2-pytorch): A PyTorch reimplementation of the paper Free-Form Image Inpainting with Gated Convolution (DeepFillv2).
