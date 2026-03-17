# 🧠 Human Vision vs. Machine Creation: A Realism Classification Approach

> A machine learning study investigating what makes images look "real" to humans — combining psychophysics experiments with SVM, MLP, and CNN models to classify photographs vs. computer-generated images.

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Domain](https://img.shields.io/badge/Domain-Machine%20Learning-blue)
![Type](https://img.shields.io/badge/Type-University%20Project-orange)
![Models](https://img.shields.io/badge/Models-SVM%20%7C%20MLP%20%7C%20CNN-purple)

---

## 📌 Overview

Can machines learn what makes an image look *real* to the human eye? This project explores the intersection of **human perception** and **machine learning** by first conducting psychophysics experiments with 130 participants to identify the visual attributes that influence realism perception, then building three ML models to automatically classify images as **real photographs** or **computer-generated (CG)**.

We identified **10 key factors** (color naturalness, object familiarity, texture detail, etc.) that drive human realism judgment, engineered features based on these findings, and trained EF-SVM, EF-MLP, and VR-CNN classifiers on benchmark datasets — bridging the gap between human visual cognition and computational image analysis.

---

## 🎯 Objectives

- Identify the visual attributes that influence human perception of image realism through psychophysics experiments
- Engineer empirically grounded features encoding color, texture, familiarity, and aesthetics
- Develop and compare three ML models (SVM, MLP, CNN) for realism prediction and photo vs. CG classification
- Evaluate models on benchmark datasets including the Washington 3D Scene Dataset

---

## 🔬 Psychophysics Experiments

### Study I — Binary Realism Classification
- **30 participants** categorized images as either photographs or computer-generated
- Generated binary ground truth labels for model training

### Study II — Realism Rating Scale
- **100 participants** rated images on a 5-point scale (1 = fully CG → 5 = highly realistic)
- Revealed nuanced perceptions and strong consistency with Study I results

---

## 🔍 Key Realism Factors Discovered

The 10 attributes most influencing human realism perception, ranked by inter-rater agreement:

| # | Factor | Agreement (ρ) | Correlation |
|---|--------|:---:|:---:|
| 1 | Colors go well together | 0.88 | 0.20* |
| 2 | Color appearance natural | 0.82 | 0.45* |
| 3 | Familiarity with objects | 0.77 | 0.17* |
| 4 | Objects appear natural | 0.76 | 0.34* |
| 5 | Object combinations appear natural | 0.76 | 0.22* |
| 6 | Appears to be a photograph | 0.73 | 0.78* |
| 7 | Familiarity with the scene | 0.65 | 0.29* |
| 8 | Contains fine details | 0.58 | -0.02 |
| 9 | Mysterious quality | 0.34 | -0.26* |
| 10 | Unusual or strange elements | 0.30 | -0.28* |

> **Key insight:** Color naturalness (ρ=0.82) and color harmony (ρ=0.88) had the strongest influence — humans judge realism primarily through color before texture or content.

---

## 🏗️ Model Architecture

Three models were developed using different approaches:

```
                    ┌─────────────────────────────────┐
                    │        INPUT IMAGE              │
                    └───────────┬─────────────────────┘
                                │
                ┌───────────────┼───────────────┐
                ▼               ▼               ▼
    ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
    │   EF-SVM      │  │   EF-MLP      │  │   VR-CNN      │
    │               │  │               │  │               │
    │ Handcrafted   │  │ Handcrafted   │  │ End-to-End    │
    │ Features +    │  │ Features +    │  │ Raw Pixels →  │
    │ SVM Classifier│  │ Neural Network│  │ Conv Layers   │
    └───────┬───────┘  └───────┬───────┘  └───────┬───────┘
            │                  │                  │
            └──────────────────┼──────────────────┘
                               ▼
                    ┌─────────────────────┐
                    │  Photo or CG?       │
                    │  + Realism Score     │
                    └─────────────────────┘
```

| Model | Approach | Input | Strength |
|-------|----------|-------|----------|
| **EF-SVM** | Feature-based + SVM | Engineered features | Fast, interpretable |
| **EF-MLP** | Feature-based + Neural Net | Engineered features | Captures non-linear patterns |
| **VR-CNN** | Deep Learning | Raw image pixels | Automatic feature extraction |

---

## ⚙️ Feature Engineering

Features designed from psychophysics findings:

```
┌─────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│    COLOR         │     │    AESTHETICS     │     │   OBJECT         │
├─────────────────┤     ├──────────────────┤     ├──────────────────┤
│ Color histogram  │     │ Brightness       │     │ Object count     │
│ similarity       │     │ Contrast         │     │ Scene arrangement│
│ Color balance    │     │ Color harmony    │     │ Familiarity cues │
│ Naturalness      │     │ Visual appeal    │     │                  │
└─────────────────┘     └──────────────────┘     └──────────────────┘
```

---

## 📊 Experimental Design

Two tasks were evaluated:

| Task | Type | Ground Truth | Metric |
|------|------|-------------|--------|
| **Realism Prediction** | Regression | 5-point realism scores (Study II) | Correlation coefficient |
| **Image Classification** | Binary | Photo vs. CG labels (Study I) | Accuracy |

**Datasets used:**
- Visual Realism Dataset (human-rated images)
- Washington 3D Scene Dataset (generalization testing)

---

## 🧰 Tech Stack

| Category | Tools & Technologies |
|----------|---------------------|
| **Language** | Python |
| **ML Models** | SVM, MLP (scikit-learn), CNN (TensorFlow/Keras) |
| **Feature Extraction** | OpenCV, color histograms |
| **Data Analysis** | NumPy, Pandas, Matplotlib |
| **Experiments** | Psychophysics surveys (30 + 100 participants) |

---

## 📁 Repository Structure

```
├── README.md                    # Project documentation
├── ML_CEP_final.pdf             # Full project report
```

---

## 📄 Documentation

| Document | Link |
|----------|------|
| 📘 Full Report (PDF) | [View Report](./ML_CEP_final.pdf) |

---

## 📸 Screenshots

<details>
<summary><b>Click to view examples</b></summary>

<br>

### Real vs. Computer-Generated Image Samples
Example images from the dataset showing real photographs alongside computer-generated images used in the psychophysics experiments and model training.

![Real vs CG Samples](./screenshots/real_vs_cg_samples.png)

</details>

---

## 👥 Team

| Name | Roll Number |
|------|-------------|
| Anousha Malik | NIM-BSEE-2021-29 |
| Ahtisham Saleem | NIM-BSEE-2021-19 |
| Saad Zahid | NIM-BSEE-2021-26 |
| Jaleed Ahmed | NIM-BSEE-2021-02 |

---

## 🏫 Academic Info

| Detail | Info |
|--------|------|
| **Course** | EE-475: Introduction to Machine Learning |
| **Instructor** | Dr. Farrukh Qureshi |
| **University** | Namal University, Mianwali |
| **Program** | BS Electrical Engineering |

---

## 📬 Contact

- **Email:** engr.ahtishamsaleem@gmail.com
- **LinkedIn:** [Ahtisham Saleem](https://www.linkedin.com/in/ahtisham-salim)
- **GitHub:** [@codebyahtisham](https://github.com/codebyahtisham)

---

<p align="center">
  ⭐ If you found this project interesting, consider giving it a star!
</p>
