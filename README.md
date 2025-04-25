# Image Anonymization with YOLOv8

This Colab notebook demonstrates segmenting people in images and detecting their faces using YOLOv8 models. To then apply various blurring techniques to anonymise the subjects.

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
        (Or you can modify the code to pick one of the 3 options to suit your project).
    * Runs person segmentation.
    * Applies Gaussian, mosaic, and solid color blurring to the segmented people.
        (Or you can modify the code to pick one of the 3 options to suit your project).
6.  **Saves the resulting images** 
    * Saves images with different blur effects applied.

## Dependencies

You need the following Python libraries installed:

* `ultralytics`: For YOLOv8 models.
* `huggingface_hub`: To download the face detection model.
* `Pillow (PIL)`: For image handling.
* `opencv-python`: For image processing tasks (in this case: reading, writing, blurring, resizing, color conversion).
* `numpy`: For handling the numerical data that makes up images.

You can install the primary dependencies using pip:

```bash
pip install ultralytics huggingface_hub opencv-python numpy Pillow
``` 

## How to run
Set up Environment: Use a Python environment (like Google Colab) with the dependencies listed above installed.

Upload image: Upload the image(s) you want to process to your environment.

Update image path: Modify the image_path variable in the code to point to your uploaded image:

Update this line with the path to your image: image_path = "/content/your_image_name.jpg"

Optional: If you only want to apply one specific blur method, instead of all three, you need to modify the code before running it. Comment out or delete the lines corresponding to the blur methods you don't want.

Run the Code: If you use notebook, execute the cells in the notebook sequentially.

Check Outputs: The processed images with different blur effects will be saved in your environment's content directory. You can view or download them from there.

## Blurring Methods

This code implements three blurring methods for both faces (bounding boxes) and segmented people (masks):

Gaussian Blur: Applies a standard Gaussian blur filter. The intensity is controlled by kernel_size. The size of the kernel needs to be an odd number. 

Mosaic Blur: Downscales the region and then upscales it using nearest-neighbor interpolation to create a pixelated effect. The level of pixelation is controlled by mosaic_size.

Solid Color Blur: Replaces the region with a solid color, calculated as the average color of the pixels within that region.

Kernel size should be changed depending on the level of anonymization needed for your project. 
Solid blur offers the highest level of anonymization out of the three methods. 
