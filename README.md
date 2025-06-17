# 🌍 An Ensemble Earthquake Prediction System Using Machine Learning

# Authors:  
 A. Harsha Vardhan
 
U.G. Student CSBS Branch SRKR Engineering College, Bhimavaram, Andhra Pradesh, India  


## 🚀Abstract

Frequent natural disasters create huge social and economic losses.  
This project presents a **machine‑learning ensemble** that forecasts earthquakes **7 days ahead**, returning probable location (lat/long), date, and occurrence probability. Early alerts from such a system can save lives and reduce infrastructure damage.

**Keywords:** Random Forest, Decision Tree, XGBoost, Machine Learning, Earthquake Dataset

---

## I. Introduction

Predicting earthquakes is difficult because of complex tectonic processes, limited data, and high spatial/temporal uncertainty. Ethical issues arise from false alarms or missed events.  
Our solution leverages recent ML advances and a continually updated USGS dataset (refreshed every 15 min) to tackle these challenges.

---

<p align="center">
  <img src="images/earth_layers.png" alt="Earth Layers" width="420">
</p>

## II. Literature Survey

1. **Kulkarni et al. (2021)** – demoed XGBoost for 7‑day quake prediction; data quality is critical.  
2. **Al Banna et al. (2022)** – reviewed AI techniques, noted difficulty forecasting high‑magnitude events.  
3. **Goswami et al. (2018)** – surveyed data‑mining for disaster management, highlighted data‑source gaps.  
4. **Jia & Ye (2023)** – deep‑learning in assessment; training data & interpretability still hurdles.  
5. **Abdul Salam et al. (2021)** – hybrid FPA‑LS‑SVM outperformed FPA‑ELM in S‑California; needs wider testing.  

---

## III. Dataset

- **Source:** USGS earthquake feed – `https://earthquake.usgs.gov/earthquakes/feed/`  
- **Samples:** 10 561 events, 22 attributes  
- **Core features kept:** `time`, `latitude`, `longitude`, `depth`, `magnitude`, `place` (others dropped if >50 % null)  

---

## IV. Problem Statement & Approach

- **Task:** Binary‐classify whether an earthquake occurs in the next 7 days.  
- **Rolling‑window labeling:** Past days → averages; window shifted +7 days to create labels.  
- **Algorithms tested:** Decision Tree, Random Forest, SVM, XGBoost (AdaBoost‑style ensemble).  
- **Metrics:** AUC‑ROC & Recall — prioritise **low false negatives** (missed quakes).

---

## V. Metrics

- **Confusion Matrix** – TP, TN, FP, FN insight  
- **AUC‑ROC** – overall discriminative power  
- **Recall** – share of actual quakes correctly flagged

---

## VI. Proposed System

*(workflow diagram below)*

<p align="center">
  <img src="images/proposed_system_flow.png" alt="Proposed System Flowchart" width="720">
</p>

### Key pipeline steps

1. **Pre‑processing** – null handling, type casting  
2. **Feature Engineering** – rolling stats (`depth7`, `mag15`, etc.)  
3. **Feature Selection**  
4. **Train/Test Split** (70 / 30)  
5. **Hyper‑tune** with `GridSearchCV`  
6. **Model comparison** via AUC & Recall  
7. **Save best model** (XGBoost) for inference  
8. **Forecast next 7 days** on live feed

---

## VII. Algorithms

| Algorithm                | Notes                                       |
|--------------------------|---------------------------------------------|
| **Decision Tree**        | Simple interpretable splits                |
| **Random Forest**        | Bagging of trees, handles variance         |
| **XGBoost**              | Gradient‑boosted trees, regularised, fast  |
| (AdaBoost variants)      | Weak‑learner ensemble                       |
| **SVM**                  | Baseline kernel classifier (for contrast)  |

---

## VIII. Results

| Classifier      | AUC‑ROC | Recall |
|-----------------|:-------:|:------:|
| Decision Tree   | 0.9165  | 0.833  |
| Random Forest   | 0.9167  | 0.833  |
| **XGBoost**     | **0.9848** | **0.833** |

- XGBoost (5 000 trees, lr = 0.003) achieved highest AUC and kept FN low (9 only).

---

<p align="center">
  <img src="images/xgboost_features.png" alt="Why XGBoost" width="600">
</p>

## IX. Conclusion

- **XGBoost** chosen for deployment – best AUC (0.98) & balanced recall.  
- Safety focus: missing an actual quake (FN) is riskier than extra alerts (FP).  
- A Google Maps‑based web app visualises 7‑day forecasts for rapid response.

---

## X. Future Work

1. **15‑day horizon** – requires richer data & deeper models (CNN/RNN, GNN, HMM).  
2. **Global generalisation** – train on multi‑region datasets.  
3. **Explainability** – SHAP/attention to build public trust.  
4. **Edge deployment** – low‑latency warnings via IoT seismographs.

---

## XI. How to Reproduce / Run Locally

```bash
# 1. Clone this repo
git clone https://github.com/harsha915/Earthaquake-Prediction-sytem.git
cd Earthaquake-Prediction-sytem

# 2. (Optional) create & activate venv
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 3. Install requirements
pip install -r requirements.txt

# 4. Train or skip (model/earthquake_model.pkl provided)
python src/train_model.py   # optional

# 5. Launch Flask app
python src/app.py
# visit http://127.0.0.1:5000
````

---

## XII. Directory Layout

```
Earthaquake-Prediction-sytem/
├─ images/
│  ├─ earth_layers.png
│  ├─ proposed_system_flow.png
│  └─ xgboost_features.png
├─ model/
│  └─ earthquake_model.pkl
├─ src/
│  ├─ app.py
│  └─ train_model.py
├─ templates/  (Flask HTML)
├─ static/     (CSS/JS)
├─ requirements.txt
└─ README.md   (this file)
```

---

## XIII. References

1. Kulkarni M., Mulay C., Marathe S., Itankar P. *Earthquake Prediction using ML* (IJARIIT, 2021)
2. Al Banna M.H. et al. *AI in Predicting Earthquakes* (2022)
3. Goswami S. et al. *Data‑Mining Techniques for Natural Disasters* (Ain Shams Eng. J., 2018)

---

## License

Released for academic and demonstration purposes. See `LICENSE` for details.
