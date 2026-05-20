# Image-classification-using-deep-learning
gastrointestinal (GI) tract Endoscope image classification project with pretrained models

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red.svg)
![Dataset](https://img.shields.io/badge/Dataset-Kvasir--v2-success.svg)

## 📌 Project Motivation & Overview
Gastric endoscopy is a critical medical procedure used to inspect the gastrointestinal (GI) tract and detect life-threatening conditions such as ulcers, polyps, and infections. Traditionally, medical professionals manually examine these endoscopic images—a time-consuming process that can be prone to human error due to fatigue. 

**This project bridges the gap between healthcare and artificial intelligence.** By leveraging state-of-the-art Deep Learning and Convolutional Neural Networks (CNNs), we have developed an automated system capable of recognizing complex patterns in endoscopic images. Our goal is to assist doctors in making faster, more accurate diagnoses, ultimately improving patient care and saving lives.

---

## 📊 The Dataset (Kvasir-v2)
We utilized the highly regarded **Kvasir-v2 Dataset**, which provides a comprehensive collection of gastrointestinal tract images.
- **Total Images:** 8,000 high-quality endoscopic images.
- **Data Balance:** Perfectly balanced dataset with exactly **1,000 images per class**, ensuring the model doesn't become biased towards any specific category.
- **8 Distinct Categories:**
  1. `dyed-lifted-polyps`
  2. `dyed-resection-margins`
  3. `esophagitis`
  4. `normal-cecum`
  5. `normal-pylorus`
  6. `normal-z-line`
  7. `polyps`
  8. `ulcerative-colitis`

---

## ⚙️ Data Preprocessing Pipeline
Medical images often suffer from varying lighting conditions and noise. We implemented a robust preprocessing pipeline to highlight critical features for our models:
1. **Resizing:** Standardized all images to `224x224` pixels for model compatibility.
2. **Normalization:** Scaled pixel values to a `[0, 1]` range to speed up convergence.
3. **Contrast Enhancement (CLAHE):** Converted images to the LAB color space and applied Contrast Limited Adaptive Histogram Equalization to make lesions and polyps more visible.
4. **Noise Reduction:** Applied a `3x3` Gaussian Blur to smooth out medical artifacts and camera noise.

---

## 🧠 Model Architectures & Comparison
During our research, we experimented with different transfer learning architectures to find the optimal balance between accuracy and computational efficiency. Here is a comparison between our two main approaches:

| Feature | 🏆 EfficientNetB3 (Primary Model) | 🔄 ResNet50V2 (Alternative Model) |
| :--- | :--- | :--- |
| **Architecture Profile** | Highly optimized, fewer parameters | Deep residual network |
| **Preprocessing Tolerance** | Works flawlessly with lightweight preprocessing | Sensitive to aggressive filtering (CLAHE/Blur caused issues) |
| **Fine-Tuning Strategy** | Standard fine-tuning approach | Required freezing all but the last **15 layers** |
| **Training Stability** | **Highly Stable** from the very first epoch | Initially unstable; required pipeline modifications |
| **Overall Performance** | Excellent accuracy & fast convergence | Good, but required significant parameter tuning |

### 💡 Why EfficientNetB3 Won:
After rigorous testing, **EfficientNetB3** was chosen as our final and primary model. It provided a superior balance of high accuracy and computational efficiency. It adapted beautifully to our dataset without requiring the heavy modifications that ResNet50V2 needed, resulting in smooth loss/accuracy curves and excellent predictive performance.

---

## 👥 the Team
This project was brought to life by a dedicated team of engineering students, under the supervision of esteemed faculty members:

**Team Members:**
* 👩‍💻 **Wafaa Hassan Ramadan**
* 👩‍💻 **Sohaila Elsayed Ibrahem**
* 👩‍💻 **Mennatallah Mohamed Elsayed**

**Academic Supervision:**
* 🎓 **Dr. Lamees Naser** * 🎓 **Eng. Merna Mansour** ---
*If you find this project helpful, please consider giving it a ⭐ on GitHub!*
