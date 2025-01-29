# **ML Explainability Using LIME**
## Overview

This repository demonstrates how to use <b>LIME (Local Interpretable Model-Agnostic Explanations)</b> to generate local explanations for predictions made by the <b>ResNet34</b> model which can be called as a black-box model because it predicts without giving any explanation why certain features contribute to a particular decision.



## Why LIME?

LIME is well-suited for this task because:
1. **Model-Agnostic** - It can explain any model whcih includes deep learning models such as ResNet, Inception, YOLO etc
2. **Local Interpretability** - it is a local explanation, focused on one prediction at a time; assisting in debugging decisions independently.
3. **Intuitive Visualization** - It highlights the image regions that were that were most influential for classification.
   
## Strengths
1. <b>Helps Understand Misclassification</b> - We saw that" the car was mistaken for a "minivan", "beach wagon", "pickup", and "parking meter". LIME showed that the model relied more on the roof shape, wheel, and windows rather than the full car body or its structure.
2. <b>Visualises Feature Importance</b> - We saw that the roofline and doors were critical for the "minivan" prediction. The wheels played a major role in the "car wheel" prediction. Background elements such as windows and bushes misled a few incorrect predictions.
3. <b>Works on any Model</b> - As LIME is Model-Agnostic, it can be used on any Machine Learning or Deep Learning Model including transformers.

## Limitations
1. <b>Image Segmentation can be Inaccurate</b> - LIME relies on superpixel segmentation, which, at times, may include the background in explanations. This happened in the "parking meter" misclassification, where the model was focusing on the windows and wall textures rather than the car.
2. <b>Results can be Inconsistent</b> - Since LIME works by perturbing the image randomly, if we run it multiple times, it may give different feature highlights. This may lead to unstable explanations, especially for low-confidence predictions such as "pickup" (1%).
3. <b>Computationally Expensive</b> - Since LIME makes multiple predictions on pertubed data points to highlight feature importance, it is considered to be computationally expensive.

## Potential Improvements
1. **Expand Training Data** - We can add more car images from different angles, lighting conditions, and backgrounds to improve model recognition and feature approximation.
2. **Increasing the Number of Perturbations** - We can increase `num_samples` (probably 5000 in place of 1000) for more stable explanations.
3. **Reduce Background Influence** - We can try preprocessing images by masking non-object areas using edge detection or cropping around the object.

## Final Thoughts
1. LIME gave us very good insights as to how the ResNet34 model made its predictions, revealing that the model sometimes focused on the wrong features ( e.g the elements in the background and bits and pieces of car features )
2. While LIME is a powerful tool for explaining deep learning models, we can try it out by combining it with other techniques like SHAP and Anchors to improve reliability, feature approximation and reduce inconsistencies.

## Installation and Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/johnjoel2001/ML_Explainability_I.git
   cd ML_Explainability_I
   ```
2. Run the main.ipynb
3. The requirements are listed in the first cell.


## References

1)  **Unsplash Image URL ( I have selected this particular image for this Assignemnt )** - https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D

2) **ImageNet Class Labels** - https://storage.googleapis.com/download.tensorflow.org/data/imagenet_class_index.json"
