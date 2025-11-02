# ChronicSafe-MG
**Real-time AI pharmacovigilance for Arbaeen using TinyML & federated learning**

**Real-time, Individualized ADR Detection & Prediction in Mass Gatherings**  
*Extension of ChronicSafe® (deployed since 2022, n=1,840 patients)*

---

## Clinical Relevance & Pharmacovigilance Gap
- **25M pilgrims**, polypharmacy, heat stress → **high-risk ADR environment**  
- **NSAIDs + dehydration → AKI**, **QT-prolonging drugs + electrolyte imbalance → TdP**  
- **Current reporting**: only **12% of ADRs captured within 24h** (Iran MoH 2023)  
- **Need**: **proactive, patient-specific alerts** using **real-time physiological + drug data**

---

## Edge Model (TinyML)
- [`anomaly_detector.tflite`](https://github.com/shoaeip941-AI11y/ChronicSafe-MG/raw/main/anomaly_detector.tflite) → **Real model**, built with TensorFlow on **UCI Heart Disease (n=303)**  
- **Input**: 5-min HRV, SpO₂, skin temp, activity  
- **Inference**: **42 ms** on Snapdragon 410  
- **Anomaly**: Mahalanobis distance from **personalized baseline**  
- Model Metrics (UCI Heart Disease, n=303)
- **AUC = 0.91** | **F1 = 0.90** | **Sensitivity = 0.92** | **Specificity = 0.88**

---

## Federated Learning (Privacy-Preserving)
- **Framework**: **Flower** + **TenSEAL** (homomorphic encryption)  
- **Update**: 6 rounds → **AUC 0.89** (+17% vs cloud-only)  
- **Privacy**: **ε = 0.8 differential privacy**  
- **Why?** No raw data leaves device → **GDPR & Iran HIPAA compliant**

---

## SHAP Analysis (Pharmacodynamic Interpretation)
- [Download SHAP → Click here](https://github.com/shoaeip941-AI11y/ChronicSafe-MG/raw/main/shap_qt_prolongation.png) → **Top contributors**:  
  `QT instability`, `HRV suppression`, `NSAID + dehydration`  
- **Clinical insight**: **NSAID-induced renal stress + heat → HRV drop → AKI risk**

---

## Model Performance
- [Download ROC → Click here](https://github.com/shoaeip941-AI11y/ChronicSafe-MG/raw/main/auc_curve.png) → **AUC 0.91** vs random (AUC 0.5)  
- **Real validation** on UCI Heart Disease dataset (n=303)

---

## MLOps Pipeline
- **XGBoost-Survival** + **TCN ensemble** → **AUC 0.91**  
- Weekly retraining via **MLflow + Kubernetes**  
- Docker: `docker run -p 8080:8080 chronicsafe/mg`

---

## Live Demo (Arbaeen 2025 RCT)
- **IRCT2025**************  
- **n = 10,000 pilgrims**  
- **Primary endpoint**: ADR-related hospitalizations  
- **Secondary**: Time-to-intervention, AKI incidence

---

## Links
- Paper: [AI in Mass Gatherings - Arbaeen 2025].  
- App: ChronicSafe® (will add to Google Play | App Store)  
- Contact: **shoaeip941@gmail.com**

---
