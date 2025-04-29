# YOLO Wardrobe Detection

This is an ongoing personal project focused on building a custom YOLOv8 object detection model to identify various wardrobe items (shirts, t-shirts, pants, and shoes) from images.

The goal is to create a lightweight, deployable model (target: Raspberry Pi 5) capable of recognizing different categories of clothing based on manually collected and labeled image data.

---

## Current Status

| Stage | Status |
|:---|:---|
| Dataset images collected | Completed |
| Image formatting and cleaning | Completed |
| Image labeling with bounding boxes (Label Studio) | Completed |
| Dataset structure organized for YOLOv8 | Completed |
| Model training and fine-tuning | Ongoing |
| Deployment preparation | Pending |

- All wardrobe item images have been manually photographed.
- All images are now labeled with tight bounding boxes.
- Class labels have been consistently assigned.
- Dataset is formatted and ready for YOLOv8 training.


## Project Folder Structure

```
yolo_wardrobe_detection/
├── data/
│   ├── images/
│   │   ├── train/        # Training images
│   │   └── val/          # Validation images
│   ├── labels/
│   │   ├── train/        # YOLO format label files for train images
│   │   └── val/          # YOLO format label files for val images
│   ├── classes.txt       # List of all class names (for labeling tools)
│   └── data.yaml         # YOLO dataset configuration file
├── notebooks/            # (Empty for now — will contain Jupyter experiments)
├── src/                  # (Empty for now — will contain training scripts)
├── outputs/
│   ├── models/           # (Will store trained model checkpoints)
│   ├── predictions/      # (Will store model prediction outputs)
│   └── logs/             # (Training and evaluation logs)
├── README.md             # This project readme
├── requirements.txt      # (Empty or partial — will be filled post-training)
```

---

## Notes

- Labeling was performed using **Label Studio**, with bounding boxes tightly drawn around clothing items, avoiding background noise where possible.
- The project is currently **pre-training**: labeling and dataset preparation are finished, but no model training or fine-tuning has started yet.
- The model will be based on **YOLOv8n (Nano)** to optimize performance for CPU-bound devices like the Raspberry Pi 5.

---

## Next Steps

- Fine-tune a YOLOv8n model on the labeled dataset.
- Validate model performance and optimize it for Raspberry Pi inference.
- Prepare export formats (ONNX, CoreML) for deployment if needed.

---

*This project is actively under development.*
