# Image-Segementation-with-GANs

# Satellite Image Segmentation with GANs (LLNL Internship, 2022)

**Note:** This repository provides a high-level summary of a segmentation project conducted during my internship at Lawrence Livermore National Laboratory (LLNL) in 2022. Due to institutional policy, code and quantitative results are not publicly shareable.

---

## 📌 Project Overview

The goal of this project was to develop a data-efficient method for segmenting images (satellite and face) in low-label, variable conditions. Traditional segmentation approaches often struggle when faced with sparse annotations and domain shifts, which are common in remote sensing applications.

---

## 🧠 Problem Statement

- Segment satellite images with limited labeled data
- Operate under significant environmental and spatial variability
- Evaluate feasibility of adapting generative models for segmentation tasks

---

## 🛠️ Approach

To address these challenges, I repurposed a StyleGAN-based foundation model with the following strategy:

- Introduced a custom **"ToRGB" module** into the generator to produce stylized RGB segmentation masks as the generator output
- Treated **segmentation as a form of style transfer**, building on ideas from DatasetGAN and JoJoGAN
- Fine-tuned the model on a low-resource satellite dataset using a small number of annotated images
- Evaluated performance using internal metrics such as mean IoU and class-wise accuracy

  Public Dataset: Celeb-A Mask

---

## 🧩 Pipeline

The generatore requires a latent code as input, which is generated using a pre-trained pSp inverter. Note - this is not retrained but just used in inference mode.

During training, multiple instances of pre-existing segmentation masks from the dataset are used as "varied" instances for a single input image. This ensures the modified generator learns the segmentation mask as the required style. The output of the training stage is a segmented style mask for the input image.

The training pipeline is as follows

![Training image](training.png)

During testing, sampling from the trained GAN generates the segementation as style for the test images. The metrics are then calculated as shown:

![Testing pipeline](testing.png)

---

## 🚀 Outcomes

- The generative approach significantly outperformed traditional off-the-shelf segmentation models in internal LLNL tests
- Demonstrated the potential of **generative pretraining** and **style-based adaptation** for low-label segmentation
- Validated GAN-based architectures as a practical tool for scientific image segmentation

---

## 🔧 Tools & Frameworks

- PyTorch
- StyleGAN2
- JoJoGAN adaptation
- HPC compute environments (Linux-based cluster)
- Remote sensing image datasets (restricted)

---

## 🙋 Author

Sinjini Mitra  
PhD, Electrical Engineering (AI/ML), Arizona State University  
[GitHub Portfolio](https://sinjini15.github.io/) | [LinkedIn](https://www.linkedin.com/in/sinjinimitra/)  
