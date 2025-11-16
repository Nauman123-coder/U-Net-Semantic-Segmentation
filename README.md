# Image Segmentation with U-Net

![Car Segmentation](images/carseg.png)

## Overview
This project builds a **custom U-Net** using TensorFlow and Keras to perform **semantic image segmentation** — assigning a class label to **every single pixel** in an image.

- **Goal**: Predict precise object masks (e.g., cars, people, roads) in self-driving car scenes  
- **Framework**: TensorFlow 2.x + Keras Functional API  
- **Key Task**: Pixel-wise classification using sparse categorical crossentropy  
- **Outcome**: A fully trainable model ready for autonomous driving perception  

---

## Why Semantic Segmentation?

Semantic segmentation goes **beyond bounding boxes**. Here's why it matters:

- **Object Detection**: Answers *"What and where?"* with rectangles (may include background)  
- **Semantic Segmentation**: Answers *"Which pixel belongs to what?"* → **exact masks**  
- **Critical for Self-Driving Cars**:  
  - Avoids collisions with pixel-level precision  
  - Enables safe lane changes and pedestrian detection  
  - Powers real-time environment understanding in dynamic scenes  

> _Every pixel counts when lives are on the line._

---

## Dataset: CARLA Simulator

The data comes from the **CARLA self-driving car simulator**:

- **RGB Images**: `./data/CameraRGB/` → Real-world-like driving scenes  
- **Segmentation Masks**: `./data/CameraMask/` → Pixel-perfect ground truth  
- **Classes Highlighted**:  
  - `Car` → Dark blue  
  - `Person` → Red  
- **Preprocessing**: Images and masks loaded, paired, and visualized for validation  

> *Note: The `data/` folder is excluded via `.gitignore` — download separately if needed.*

---

## U-Net Architecture

U-Net is an **encoder-decoder CNN** designed for precise segmentation:

- **Encoder (Downsampling Path)**:  
  - Captures context using `Conv2D` + `MaxPooling2D`  
  - Reduces spatial size, increases feature depth  
- **Decoder (Upsampling Path)**:  
  - Uses `Conv2DTranspose` to recover resolution  
  - Restores fine-grained details  
- **Skip Connections**:  
  - Concatenate encoder features to decoder  
  - Prevent loss of border pixels and reduce overfitting  
- **Final Layer**: 1×1 convolution → class logits per pixel  

![U-Net Architecture](images/unet.png)

> _"U" shape = Down, bottom, up — with highways (skip connections) for information flow._

---

## Key Takeaways

- U-Net balances **context** and **localization**  
- Skip connections = secret to **sharp boundaries**  
- Ideal for **medical imaging**, **satellite analysis**, and **autonomous driving**  

---

## The Final Frame: A Story in Pixels

Imagine a quiet evening drive. A child chases a ball into the street.  
Your car doesn’t see a *box* around the child — it sees **every pixel** of danger.  
In 40 epochs, this U-Net learns to paint the world in labels:  
> *"Red for person. Blue for car. Green for safe."*  

And in that split second, **a mask becomes a lifeline.**  

This isn’t just code.  
It’s the future of perception — **one pixel at a time.**

---

*Built with passion. Trained for precision. Deployed for safety.*  
**Elon might not knock… but the future just did.**
