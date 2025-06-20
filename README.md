# 🎨 Context-Aware Image Colorization with Semantic Segmentation

This project performs **context-aware grayscale image colorization** using a deep learning pipeline that combines semantic segmentation (via DeepLabV3) and an encoder-decoder architecture (EfficientUNet). It enhances color realism by using object-aware cues.

---

## 📌 Features

- Accepts grayscale (`.jpg`, `.png`, `.webp`, etc.) images as input.
- Automatically segments the image using DeepLabV3.
- Applies **colorization conditioned on segment masks** using a custom EfficientUNet model.
- Supports a **Gradio interface** for easy user interaction.
- Calculates **SSIM** and **PSNR** scores to evaluate output quality.
- Final outputs can be downloaded in multiple formats (JPEG, PNG, WEBP, TIFF).

---

## 🧠 Model Architecture

- **Encoder**: EfficientNet-B0 pretrained on ImageNet.
- **Decoder**: U-Net style upsampling blocks.
- **Segmentation**: Precomputed using `deeplabv3_resnet101`.
- **Fusion**: Segment mask is embedded and concatenated with grayscale input before feeding to encoder.

---

## 📁 Dataset Structure

The dataset combines multiple sources and is preprocessed into `L` and `ab` channels from LAB color space.

'''
landscape_data/
├── train/
│ ├── grayscale/
│ ├── color/
│ ├── lab_L/
│ └── lab_ab/
├── valid/
└── test/
'''

