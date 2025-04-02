

# **Comparing LSGAN, WGAN, and WGAN-GP on MedMNIST**  

This repository contains the code and results for comparing **LSGAN, WGAN, and WGAN-GP** on three datasets from **MedMNIST**: **PathMNIST, OCTMNIST, and BreastMNIST**. The goal is to analyze their performance in generating medical images by evaluating **FID (Fréchet Inception Distance), IS (Inception Score), training stability, and efficiency**.  

## **Datasets Used**  
| Dataset    | Description | Size | Characteristics |  
|------------|------------|------|----------------|  
| **PathMNIST** | Histopathology images of colorectal cancer tissue | 107,180 images | **Colored, high variation** |  
| **OCTMNIST**  | Optical coherence tomography scans of the retina | (Subset) 15,000 images | **Grayscale, moderate variation** |  
| **BreastMNIST** | Breast ultrasound images for tumor classification | 780 images | **Grayscale, very small dataset** |  

## **Experiment Setup**  
- **LSGAN, WGAN, and WGAN-GP** were trained on all three datasets.  
- Models were evaluated using **FID (lower is better) and IS (higher is better)**.  
- Training time and stability were also analyzed.  

## **Results**  

### **PathMNIST**  
| Model      | Epochs | Training Time | FID ↓ | IS ↑ | Last Epoch D Loss | Last Epoch G Loss |  
|------------|--------|--------------|-------|------|------------------|------------------|  
| **LSGAN**  | 50     | 46 min       | 348.28 | 1.51 | 0.1361 | 1.3743 |  
| **WGAN**   | 16     | 1.86 hrs     | 123.78 | 1.24 | 0.1771 | -1.1623 |  
| **WGAN-GP**| 31     | 3.43 hrs     | 140.43 | 1.31 | 6.6229 | -4.8858 |  

### **OCTMNIST**  
| Model      | Epochs | Training Time | FID ↓ | IS ↑ | Last Epoch D Loss | Last Epoch G Loss |  
|------------|--------|--------------|-------|------|------------------|------------------|  
| **LSGAN**  | 50     | 57.75 min    | 322.79 | 2.03 | 0.0242 | 0.9741 |  
| **WGAN**   | 50     | 53.39 min    | 231.15 | 1.91 | -0.1928 | -0.0561 |  
| **WGAN-GP**| 50     | 56.54 min    | 227.27 | 1.98 | 9.7521 | -64.3092 |  

### **BreastMNIST** (50 Epochs)  
| Model      | Epochs | Training Time | FID ↓ | IS ↑ | Last Epoch D Loss | Last Epoch G Loss |  
|------------|--------|--------------|-------|------|------------------|------------------|  
| **LSGAN**  | 50     | 4.5 min      | 430.62 | 1.82 | 0.0048 | 0.9712 |  
| **WGAN**   | 50     | 4.3 min      | 370.56 | 1.41 | -0.0912 | 0.3327 |  
| **WGAN-GP**| 50     | 2.65 min     | 379.41 | 1.58 | 11.4073 | 1.6067 |  

### **BreastMNIST** (100 Epochs)  
| Model      | Epochs | Training Time | FID ↓ | IS ↑ | Last Epoch D Loss | Last Epoch G Loss |  
|------------|--------|--------------|-------|------|------------------|------------------|  
| **LSGAN**  | 100    | 9 min        | 398.63 | 1.84 | 0.0030 | 1.0886 |  
| **WGAN**   | 100    | 5 min        | 274.89 | 1.77 | -0.5630 | 0.9131 |  
| **WGAN-GP**| 100    | 5 min        | 303.49 | 1.73 | 8.7280 | 0.5244 |  

## **Key Takeaways**  
- **PathMNIST (Colored, large dataset):**  
  - **WGAN performed the best** in terms of FID (123.78) but required **significant training time**.  
  - **LSGAN had the highest IS**, though it struggled with image fidelity.  
  - **WGAN-GP took the longest** and didn’t significantly outperform WGAN.  

- **OCTMNIST (Grayscale, moderate dataset):**  
  - **WGAN-GP had the best FID (227.27)** but required **longer training** than WGAN.  
  - **LSGAN had the highest IS (2.03),** indicating more diverse image generation.  

- **BreastMNIST (Grayscale, small dataset):**  
  - **LSGAN performed the worst across metrics** with an FID of 430.62.  
  - **WGAN improved significantly with more epochs**, suggesting that extended training helped stabilize performance on this smaller dataset.
  - **WGAN-GP struggled with stability**, leading to inconsistent gains.  

---  
📖 **Read the full blog post:** [Medium Link]  

