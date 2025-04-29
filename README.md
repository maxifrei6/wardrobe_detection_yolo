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

- Labeling was performed using **Label Studio**, with bounding boxes tightly drawn around clothing items, minimizing background noise.
- Training is currently in progress: the dataset preparation phase is complete, and fine-tuning has begun on a **YOLOv8n (Nano)** model.
- Deployment is planned for a **Raspberry Pi 5**, targeting efficient inference on CPU-only hardware.


## Dataset Creation Process

This dataset was created entirely manually for the purpose of fine-tuning a custom YOLOv8 object detection model to recognize wardrobe items (e.g. shirts, t-shirts, pants, shoes).

---

### 1. Image Collection

- All clothing items were **photographed individually** using a phone camera.
- Each item was placed on a neutral background (floor, door, or dark surface) for contrast.
- The camera was held steady in top-down or front-facing angle.
- Natural or room lighting was used (no flash).
- Images were exported to `.jpg` format and organized into folders by item type.
- No data augmentation was used at this stage.

**Example:**

![Dataset Overview](assets/dataset_overview.png)

---

### 2. File Cleaning and Organization

- All images were renamed using a clear pattern, e.g.:
  ```
  tshirt_white01.jpg, pants_dark12.jpg
  ```
- `.HEIC` and `.MOV` files were removed or ignored.
- Images were sorted into class folders for easier inspection before being merged into the final dataset.

**Example layout:**

```
/unprocessed/
├── tshirt_white01.jpg
├── tshirt_white02.jpg
├── pants_dark03.jpg
```

---

### 3. Train/Val Split

- Images were split randomly by their index into 80% training / 20% validation.
- Each split preserved class balance.
- Images were then placed in YOLO-compatible folders:

```
data/images/train/
data/images/val/
```

---

### 4. Annotation / Bounding Box Labeling

- Labeling was performed using **Label Studio**.
- Classes were predefined and consistent across all images.
- Boxes were drawn tightly around clothing items including all visual parts (e.g. sleeves, collars, soles).
- Exported format: YOLOv8 (text files per image with class and normalized coordinates).

**Example:**

![Bounding Box Example](assets/bounding_box.png)

---

### 5. YOLO Format Output Example

Each image has a `.txt` file with YOLO annotations in the format:

```
class_index x_center y_center width height
```

Example label file:

```
0 0.5049 0.5582 0.7654 0.8571
```

Where:
- `0` → Class index (e.g. `tshirt_white`)
- `0.5049 0.5582` → Center of the box (normalized)
- `0.7654 0.8571` → Width and height (normalized)

These are stored as:

```
data/labels/train/tshirt_white02.txt
```

---

## Next Steps

- Fine-tune a YOLOv8n model on the labeled dataset.
- Validate model performance and optimize it for Raspberry Pi inference.
- Prepare export formats (ONNX, CoreML) for deployment if needed.

---

*This project is actively under development.*
