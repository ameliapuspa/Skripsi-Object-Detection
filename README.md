# Palm Oil Leaf Bagworm Detection using Faster R-CNN and YOLOv8
This repository contains my bachelor degree's final project, where I compare the performance of **Faster R-CNN** and **YOLOv8** for detecting bagworms on palm oil leaves. The objective of this project is to determine which model performs better in detecting bagworms based on accuracy, precision, and recall. The entire project was developed using Google Colaboratory.
## Introduction
Indonesia has become the world's largest palm oil producer since 2006, and the health of palm oil leaves, which play a key role in photosynthesis, is crucial for producing high-quality fruit. Bagworms (Metisa plana) are one of the main pests that can damage these leaves, negatively impacting crop productivity.
Currently, pest detection is done manually through visual observation, which is not always effective. This project aims to automate the detection of bagworms using deep learning models, comparing Faster R-CNN and YOLOv8, and exploring the impact of various tiling techniques to improve detection on small objects like bagworms.
## Dataset
The dataset consists of **104 images** of palm oil leaves with and without bagworm infestations, provided by **PT SMART Tbk, Riau**. The images are annotated and augmented using **Roboflow**.
- **Image dimensions**: 360 x 640 px
- **Train/Validation/Test split**: 73/21/10
- **Annotation tool**: Roboflow
- **Augmentation techniques**: Random rotations, flips, and crops
## Tiling Scenarios
Due to the small size of the bagworms in the images, we experimented with tiling techniques to improve detection performance. Four different scenarios were tested:
1. **No Tiling**: Images used in their original dimensions (360 x 640 px)
2. **Tiling 2x2**: Each image is split into 4 tiles
3. **Tiling 3x3**: Each image is split into 9 tiles
4. **Tiling 3x4**: Each image is split into 12 tiles
These tiling methods were applied to both Faster R-CNN and YOLOv8 models to evaluate their impact on detection performance.
## Results
The performance of both **Faster R-CNN** and **YOLOv8** was evaluated using the validation dataset across different tiling scenarios. The table below summarizes the results for each tiling scenario based on accuracy, precision, and recall:
| Model        | Tiling  | Accuracy | Precision | Recall |
|--------------|---------|----------|-----------|--------|
| Faster R-CNN | No Tiling | 70.8%     | 84.3%       | 81.5%    |
| Faster R-CNN | 2x2     | 72.9%      | 85.3%       | 83.3%    |
| Faster R-CNN | 3x3     | 83.1%      | 90.6%       | 90.9%    |
| Faster R-CNN | 3x4     | 80.5%      | 89.3%       | 89%    |
| YOLOv8       | No Tiling | 77.3%     | 88%       | 86.4%    |
| YOLOv8       | 2x2     | 79.2%      | 88.9%       | 91.3%    |
| YOLOv8       | 3x3     | 84.7%      | 91%       | 92.4%    |
| YOLOv8       | 3x4     | 82.4%      | 90.5%       | 90.1%    |

Based on the validation data, the **YOLOv8 model with 3x3 tiling** achieved the highest performance, with an accuracy of 95.0%, precision of 93.2%, and recall of 91.0%. This model was then used to test the model on the test dataset.
### Test Results
The **YOLOv8 3x3** model was evaluated on the test dataset, resulting in the following confusion matrix:
- **True Positive (TP)**: 50
- **False Positive (FP)**: 7
- **False Negative (FN)**: 6
- **True Negative (TN)**: 0

From this confusion matrix, I calculated the following metrics:
- **Accuracy**: 80.6%
- **Precision**: 87.7%
- **Recall**: 90.9%
## Conclusion
This study compared the performance of **Faster R-CNN** and **YOLOv8** for detecting bagworms on palm oil leaves, with tiling techniques applied to enhance detection of small objects. The results showed that **YOLOv8** with 3x3 tiling achieved the best overall performance on the validation data, with the highest accuracy, precision, and recall.

When tested on unseen data, the **YOLOv8 3x3** model maintained strong performance, achieving an accuracy of 80.6%, a precision of 87.7%, and a recall of 90.9%. These results demonstrate the model's potential for automating pest detection in palm oil plantations, contributing to the digitalization of pest surveillance systems. This approach can help mitigate the economic impact caused by bagworm infestations.
