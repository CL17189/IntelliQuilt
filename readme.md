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

## Model Structure
```mermaid
flowchart TD
    subgraph Input[Model Input]
        A1[Main Product Image]
        A2[Detail Image 1]
        A3[Detail Image 2]
        A4[Structured Data<br/>(e.g. Price=999, Origin=Ningbo)]
        A5[Text Description<br/>e.g. "Winter Down Jacket 2023..."]
    end

    subgraph Models
        B1[SqueezeNet<br/>(Main Image)]
        B2[MobileNet_V2<br/>(Detail Image 1)]
        B3[MobileNet_V2<br/>(Detail Image 2)]
        B4[MLP<br/>(Structured Data)]
        B5[LSTM<br/>(Text Data)]
    end

    subgraph Decision Vectors
        C1[Decision 1]
        C2[Decision 2]
        C3[Decision 3]
        C4[Decision 4]
        C5[Decision 5]
    end

    D[Attention Mechanism]
    E[Final Decision<br/>(Model Output)]

    %% Connections from input to models
    A1 --> B1
    A2 --> B2
    A3 --> B3
    A4 --> B4
    A5 --> B5

    %% Model to decision vector
    B1 --> C1
    B2 --> C2
    B3 --> C3
    B4 --> C4
    B5 --> C5

    %% Decision vectors to attention
    C1 --> D
    C2 --> D
    C3 --> D
    C4 --> D
    C5 --> D

    %% Final output
    D --> E
```



## Time Line 
+ 2024.06 Accepted by the school and then nominated for an outstanding thesis.
+ 2024.04.10 Submitted the paper
+ 2024.02.21 Complete the training of multiple-modal data fusion model and submit the draft
+ 2024.01.14 Update the unimodal modeling code section and the data processing documents
+ 2024.01.08 Detailed data and pics
+ 2023.12.10 Exploring unimodal benchmark models based on NLP data
+ 2023.11.23 Raw data collected: using crawler to extract 4608 product infomation from an online platform and uploaded to github project.
+ 2023.11.17 Thesis Topic Finalized——prediction to sales of clothes on online shopping plate form.
