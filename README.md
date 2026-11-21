# Benchmarking YOLOv7 to YOLO26 for Multi-Class Brain Tumor Detection in MRI

Accuracy and parameter efficiency of six lightweight YOLO variants under limited training epochs (15 and 30).

## Dataset
Roboflow Universe, "brain-tumor-mri" by eksperiment, version 2 (CC BY 4.0).
https://universe.roboflow.com/eksperiment/brain-tumor-mri-ycidy/dataset/2

- 3,903 MRI images, 4 classes: Glioma, Meningioma, No Tumor, Pituitary
- Split: 2,444 train / 1,074 valid / 385 test
- Preprocessing: auto-orient, resize to 640x640. No augmentation in the dataset version.

## Models
YOLOv7-tiny, YOLOv8n, YOLOv9t, YOLOv10n, YOLO11n, YOLO26n. YOLOv8 to YOLO26 were trained with Ultralytics (image size 640, batch 16, seed 0). YOLOv7-tiny was trained with the original WongKinYiu/yolov7 repository using its default settings.

## Results (test set, 385 images)

| Model | Epochs | Params (M) | Precision | Recall | F1 | mAP@0.5 | mAP@0.5:0.95 |
|---|---|---|---|---|---|---|---|
| YOLOv7-tiny | 15 | 6.02 | 0.8930 | 0.7470 | 0.8135 | 0.8660 | 0.6130 |
| YOLOv7-tiny | 30 | 6.02 | 0.9170 | 0.8340 | 0.8735 | 0.9110 | 0.6600 |
| YOLOv8n | 15 | 3.01 | 0.9280 | 0.9098 | 0.9188 | 0.9522 | 0.7556 |
| YOLOv8n | 30 | 3.01 | 0.9478 | 0.9011 | 0.9239 | 0.9617 | 0.7642 |
| YOLOv9t | 15 | 2.01 | 0.9311 | 0.9081 | 0.9194 | 0.9549 | 0.7558 |
| YOLOv9t | 30 | 2.01 | 0.9203 | 0.9171 | 0.9187 | 0.9499 | 0.7589 |
| YOLOv10n | 15 | 2.71 | 0.9517 | 0.8901 | 0.9199 | 0.9542 | 0.7488 |
| YOLOv10n | 30 | 2.71 | 0.9419 | 0.9129 | 0.9272 | 0.9573 | 0.7652 |
| YOLO11n | 15 | 2.59 | 0.9364 | 0.8888 | 0.9120 | 0.9471 | 0.7505 |
| YOLO11n | 30 | 2.59 | 0.9346 | 0.8855 | 0.9094 | 0.9465 | 0.7618 |
| YOLO26n | 15 | 2.51 | 0.9328 | 0.9062 | 0.9193 | 0.9609 | 0.7608 |
| YOLO26n | 30 | 2.51 | 0.9434 | 0.8978 | 0.9200 | 0.9600 | 0.7675 |

Full table: `results_final.csv`. Figures are in `figures/`.

## Notes and limitations
- Single run per setting (seed 0) on a small test set; differences among the Ultralytics models are small.
- YOLOv7-tiny uses a different codebase and default hyperparameters, so it is not a perfectly matched comparison. Its inference time is not comparable with the others.

## How to run
Open the notebook in Google Colab (T4 GPU), place the dataset zip in Google Drive, and run the cells in order.
