# Predicting Patient No-Shows in MRI Appointments with Interpretable Machine Learning

In radiology, MRI machines are vital but expensive to run, so they should not sit idle. A single missed appointment wastes costly resources, loses revenue, and delays treatment for other patients.

This repository provides a framework to predict these no-shows using interpretable machine learning. While our study focuses on MRI, the methodology can be adapted to other diagnostic services (such as Computed Tomography (CT) or ultrasound) to improve efficiency and scheduling across different healthcare departments.

### Our Approach

Rather than chasing abstract "black-box" accuracy, by using real-world data from a brazilian diagnostic imaging clinic (*n* = 28,991) we built a system focused on operational utility through three core pillars:

* **Time-Split Cross-Validation:** To mirror a real-world deployment, we tuned our models using a temporal split—ensuring the system always predicts the "future" based only on "past" data.

* **Operational Calibration ($F_{\beta=1.5}$):** In clinical practice, the cost of an empty MRI slot (a False Negative) is often higher than the cost of a "false alarm" (a False Positive). Through discussions with clinic managers, we prioritized Sensitivity by using an $F_{\beta}$-score with $\beta=1.5$ to calibrate our decision thresholds.

* **Interpretable AI with SHAP:** To move beyond "black-box" predictions, we utilized the SHAP framework to identify exactly which factors were driving each individual prediction.

### Results & Key Drivers

The LightGBM model emerged as the best performing tool. On held-out 2023 test data, it achieved:

* **Sensitivity:** 39.63% 

* **AUC-PR:** 0.2203 

* **Overall Accuracy:** 82.37% 

SHAP analysis revealed the top drivers of non-attendance in this clinical context were distance to the clinic, healthcare plan, patient sex and age, and procedure.

### Repository Structure

The code is organized as follows:

* `data_exploration/`: Comprehensive plots for data exploration.

* `models_hyperparameter_tuning/`: Comprehensive tuning logs and scripts for LR, MLP, XGBoost, CatBoost, and LightGBM.

* `threshold_tuning/`: Optimization of the $F_{\beta}$ score to align model sensitivity with clinic goals.

* `evaluation_on_test_data/`: Final performance metrics and individual prediction "waterfall" plots for clinical interpretability.

### Full Paper

You can read the full article here:
**[https://doi.org/10.1080/01605682.2026.2636598](https://www.tandfonline.com/doi/full/10.1080/01605682.2026.2636598)**

### Citation

```bibtex
@article{oliveira2026predicting,
  title={Predicting patient no-shows in magnetic resonance imaging appointments using interpretable machine learning},
  author={de Oliveira, Carlos Eduardo Gonçalves and Teixeira, Ana Beatriz Marinho de Jesus and Oliveira, Mateus Simão and Itikawa, Emerson Nobuyuki},
  journal={Journal of the Operational Research Society},
  year={2026},
  publisher={Taylor & Francis},
  doi={10.1080/01605682.2026.2636598}
}

```

---

Ethical approval provided by the Ethical Committee of the Universidade Federal de Goiás (CAAE: 81394924.0.0000.5083). Financed in part by CAPES - Finance Code 001.
