# IntelliQuilt
**It is my undergraduate thesis project at Renmin University of China, which I completed with the help of my Tutor @JingZhou.**

## Project Introduction

After rapid growth, China’s e‑commerce platforms have entered a phase of fierce competition in operational optimization and resource integration. Merchants must stand out on highly homogeneous platforms, and accurate sales forecasting enables better inventory allocation and marketing strategies—reducing costs and improving margins.

In this study, we focus on down‑jacket products. We collected data for 4,608 items from a major e‑commerce marketplace, covering three modalities: text descriptions, structured attributes, and product images. After feature engineering and filling missing fields, we applied targeted data augmentation to address label imbalance, enhancing model generalization and preventing overfitting.

For each modality, we built a baseline model using classic architectures and optimized for accuracy. To aid convergence and avoid overfitting, we employed early stopping, adaptive learning rates, and transfer learning. The image‑based SqueezeNet model achieved 72.58% accuracy; the text‑based LSTM reached 64.72%; and the structured‑data MLP reached 66.28%.

Next, we explored multimodal fusion. We experimented with various fusion stages (early vs. late), modality combinations, and fusion rules—including feature concatenation, majority voting, and an attention mechanism. We also incorporated two specialized image models for detailed product shots. Our best late‑fusion model with attention, named **IntelliQuiltAI**, accepts images, text, and structured data and attained a maximum accuracy of **80.62%**. IntelliQuiltAI has been packaged as an interactive app for end users.

---

## Results

### Baseline Models

| Modality    | Model       | Accuracy |
|-------------|-------------|---------:|
| Image       | SqueezeNet  |   72.58% |
| Text        | LSTM        |   64.72% |
| Structured  | MLP         |   66.28% |

### Multimodal Fusion Models

| ID | Modalities                   | Fusion Stage | Fusion Rule             | Max Accuracy |
|----|------------------------------|--------------|-------------------------|-------------:|
| 1  | Text, Image, Structured      | Early        | Feature Concatenation   |      72.84% |
| 2  | Text, Image                  | Early        | Feature Concatenation   |      71.44% |
| 3  | Structured, Image            | Early        | Feature Concatenation   |      72.75% |
| 4  | Text, Image, Structured      | Late         | Majority Voting         |      77.43% |
| 5  | Text, Image                  | Late         | Majority Voting         |      77.28% |
| 6  | Structured, Image            | Late         | Majority Voting         |      75.63% |
| 7  | Text, Image, Structured      | Late         | Attention Mechanism     |      80.62% |
| 8  | Text, Image                  | Late         | Attention Mechanism     |      78.62% |
| 9  | Structured, Image            | Late         | Attention Mechanism     |      79.88% |



## Time Line 
+ 2024.06 Accepted by the school and then nominated for an outstanding thesis.
+ 2024.04.10 Submitted the paper
+ 2024.02.21 Complete the training of multiple-modal data fusion model and submit the draft
+ 2024.01.14 Update the unimodal modeling code section and the data processing documents
+ 2024.01.08 Detailed data and pics
+ 2023.12.10 Exploring unimodal benchmark models based on NLP data
+ 2023.11.23 Raw data collected: using crawler to extract 4608 product infomation from an online platform and uploaded to github project.
+ 2023.11.17 Thesis Topic Finalized——prediction to sales of clothes on online shopping plate form.
