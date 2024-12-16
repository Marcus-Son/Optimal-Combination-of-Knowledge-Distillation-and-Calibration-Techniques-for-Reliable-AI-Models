# **Optimal Combination of Knowledge Distillation and Calibration Techniques for Reliable AI Models**

---

## 📌 **Overview**

This project presents an in-depth study on the combination of **Knowledge Distillation (KD)** and **Calibration Techniques** to optimize accuracy and reliability in deep learning models, especially in **Class Imbalance** environments. The research identifies the most effective pairings of KD methods and Calibration strategies to maintain high prediction performance while ensuring reliable confidence scores.

The key objectives of this research are:
1. Mitigate the negative effects of **class imbalance** using effective calibration techniques.
2. Develop lightweight student models through **Knowledge Distillation** without compromising accuracy.
3. Evaluate and identify optimal combinations of KD and calibration techniques through comprehensive experiments.

The experimental results demonstrate that the combination of **Contrastive Representation Distillation (CRD)** and **Balanced Softmax (BS)** outperforms other methods under different imbalance ratios on CIFAR-10 and CIFAR-100 datasets.

---

## 🛠 **Key Features**

### **Knowledge Distillation Methods**
1. **Vanilla Knowledge Distillation (Vanilla KD):** 
   - The basic KD method that transfers soft logits from the teacher model to the student model.
2. **Contrastive Representation Distillation (CRD):**
   - A contrastive learning-based approach that ensures the student model mimics the teacher's feature space.
3. **Relational Knowledge Distillation (RKD):**
   - Focuses on preserving relative distances and angles between samples in the feature space.
4. **Attention Transfer (AT):**
   - Transfers the attention maps of the teacher model to the student model to align focus regions.

### **Calibration Techniques**
1. **Adaptive Label Smoothing (ALS):**
   - Dynamically adjusts the smoothing factor based on class imbalance to improve confidence calibration.
2. **Confidence Penalty (CP):**
   - Adds a penalty term to the loss to prevent overconfident predictions.
3. **Balanced Softmax (BS):**
   - Modifies the Softmax function to account for class imbalance.
4. **Mixup Augmentation:**
   - Enhances generalization by interpolating inputs and labels during training.

---

## 📊 **Experimental Setup**

### **Datasets**
The experiments are conducted on two standard benchmark datasets:
- **CIFAR-10**: 10-class image dataset with 50,000 training and 10,000 test images.
- **CIFAR-100**: 100-class image dataset with 50,000 training and 10,000 test images.

### **Class Imbalance Simulation**
Class imbalance is introduced by simulating two levels of imbalance:
- **Imbalance Factor (IF) = 50**: The most frequent class contains 50 times more samples than the least frequent class.
- **Imbalance Factor (IF) = 100**: The imbalance ratio is increased to 100:1.

### **Models**
- **Teacher Model**: ResNet-50
- **Student Model**: ResNet-18

### **Evaluation Metrics**
1. **Accuracy (ACC):** Measures overall classification performance.
2. **Expected Calibration Error (ECE):** Evaluates the alignment between predicted confidence and actual accuracy.
3. **Harmonic Score:** Combines ACC and 1-ECE to balance performance and reliability.
   
---

## 📊 **Results and Analysis**

### **1. Overall Performance**
- A total of **128 combinations** of KD and Calibration techniques were evaluated.
- **Top-performing combinations** are identified based on Harmonic Score.

#### **CIFAR-10 Results**
| KD Method | Teacher Calibration | Student Calibration | Mixup | ACC (%) | ECE | Harmonic Score |
|-----------|---------------------|----------------------|-------|---------|-----|----------------|
| CRD       | Balanced Softmax    | Balanced Softmax     | True  | 79.60   | 0.0819 | 1.0000         |
| CRD       | CP                  | CP                   | True  | 79.46   | 0.0823 | 0.9914         |

- **Key Observation**: CRD combined with **Balanced Softmax** achieves the highest performance, balancing accuracy and calibration effectively.

#### **CIFAR-100 Results**
| KD Method | Teacher Calibration | Student Calibration | Mixup | ACC (%) | ECE | Harmonic Score |
|-----------|---------------------|----------------------|-------|---------|-----|----------------|
| CRD       | Balanced Softmax    | Balanced Softmax     | True  | 43.75   | 0.1488 | 0.8561         |
| CRD       | None                | Balanced Softmax     | True  | 43.18   | 0.1526 | 0.8084         |

- **Key Observation**: Balanced Softmax proves robust even with a high imbalance factor and complex dataset.

### **2. Impact of Calibration Techniques**
- **Balanced Softmax** consistently outperforms other calibration techniques in reducing the impact of class imbalance.
- **ALS** improves model generalization but underperforms in calibration for extreme imbalance scenarios.

### **3. Influence of Knowledge Distillation Methods**
- **Contrastive Representation Distillation (CRD)** achieves the best balance between performance and reliability.
- **Vanilla KD** underperforms compared to advanced KD techniques like CRD and RKD.

---

## 📈 **Visualizations**

### **1. ACC vs ECE Plots**
ACC vs. ECE plots clearly demonstrate the trade-off between accuracy and calibration for each combination.

![output_10_50](https://github.com/user-attachments/assets/d5cd2270-24d0-4ee1-9f11-91f45bc221d3)
![output_10_100](https://github.com/user-attachments/assets/df2d9a7a-d57e-47e4-9606-ead830d78c67)
![output_100_50](https://github.com/user-attachments/assets/5fccdca2-548b-49a6-bd3a-588a60f16e92)
![output_100_100](https://github.com/user-attachments/assets/23dac0e2-eb0d-4c0e-a6d7-97aae4d1026f)

### **2. Harmonic Score Analysis**
Harmonic Score graphs highlight the best-performing combinations in terms of balancing accuracy and reliability.
![cal_10_50](https://github.com/user-attachments/assets/85b6c6a7-8a5a-476a-a9af-0c1ffb146c7a)
![cal_10_100](https://github.com/user-attachments/assets/22a6cab2-8aa8-4faf-ac1d-ce3411086775)
![cal_100_50](https://github.com/user-attachments/assets/40a1401c-f73a-403b-b685-7e4f655d3e07)
![cal_100_100](https://github.com/user-attachments/assets/4bb031be-9db7-4033-9b94-d31cd1544394)

## 🤝 **Contributors**
- **Son Minhyeok**
- **Lee Chaerin**
- Supervisor: **Prof. Shim Jaewoong**
