# Segmented_anonymizer

In this Colab notebook I demonstrate segmenting people in images and detecting their faces using YOLOv8 models. To then apply various blurring techniques to anonymise the subjects.

## Overview

The code performs the following steps:
1.  **Installs necessary libraries.**
2.  **Downloads a pre-trained YOLOv8 face detection model** from Hugging Face Hub.
3.  **Loads the face detection model and a YOLOv8 segmentation model.**
4.  **Defines functions** for:
    * Detecting faces (`detect_faces`).
    * Segmenting people (`segment_people`).
    * Applying blur to detected face bounding boxes (`blur_patches`).
    * Applying blur to segmented people masks (`blur_segmented_people`).
5.  **Processes input images:**
    * Loads the image.
    * Runs face detection.
    * Applies Gaussian, mosaic, and solid color blurring to the detected faces.
        (Or you can pick one of the 3 options to suit your project).
    * Runs person segmentation.
    * Applies Gaussian, mosaic, and solid color blurring to the segmented people.
        (Or you can pick one of the 3 options to suit your project).
6.  **Saves the resulting images** with different blur effects applied.