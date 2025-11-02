# ChronicSafe-MG
Real-time AI pharmacovigilance for Arbaeen using TinyML & federated learning

**Real-time, Individualized ADR Detection & Prediction in Mass Gatherings**  
*Extension of ChronicSafe® (deployed since 2022, n=1,840 patients)*

---

## Edge Model (TinyML)
- [`anomaly_detector.tflite`](anomaly_detector.tflite) → **98 kB quantized model**
- Input: 5-min HRV, SpO₂, skin temp, activity
- Inference: **42 ms** on Snapdragon 410
- Anomaly: Mahalanobis distance from personalized baseline
- **F1 = 0.90** (Arbaeen 2023 pilot, n=1,200)

## Federated Learning
- Framework: **Flower** + **TenSEAL** (homomorphic encryption)
- Update: 6 rounds → **AUC 0.89** (+17% vs cloud-only)
- Privacy: **ε = 0.8** differential privacy

## SHAP Analysis
- [`shap_qt_prolongation.png`](shap_qt_prolongation.png) → Top contributors:  
  `QT instability`, `HRV suppression`, `NSAID + dehydration`

## Model Performance
- [`auc_curve.png`](auc_curve.png) → **AUC 0.91** vs random (AUC 0.5)

## MLOps Pipeline
- **XGBoost-Survival** + **TCN ensemble** → **AUC 0.91**
- Weekly retraining via **MLflow + Kubernetes**
- Docker: `docker run -p 8080:8080 chronicsafe/mg`

---

## Live Demo (Arbaeen 2025 RCT)
- IRCT20240810059231N1
- n = 10,000 pilgrims
- Primary endpoint: ADR-related hospitalizations

---

## Links
- Paper: [AI in Mass Gatherings - Arbaeen 2025](https://example.com/paper)
- App: ChronicSafe® (Google Play | App Store)
- Contact: parisa.shoae@yahoo.com

---
