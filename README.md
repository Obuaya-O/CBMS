# Surrogate Endpoint Detection in Nervous‑System Clinical Trial Protocols

This repository contains code and scripts to reproduce the experiments from our CBMS 2025 paper:  
“Automated Detection of Surrogate‑Endpoint Use via Active Learning”

> **Note:** The NS‑HRA dataset is **not** included due to data‑protection restrictions. You must obtain access from the University College London and NHS Health Research Authority. If access granted, the code to extract features from the XML files into a separate datsaset will be provided.

## Features

- **Baseline Calculations: LOOCV, Training the classifier and Active learning**
 > **Note:** Each baseline calculation was created using the Megahed et al. interactive simulator (http://rstudio.fsb.miamioh.edu:3838/megahefm/metric_interpretation/)
  - LOOCV: We computed a “do‐nothing” weighted accuracy baseline by inputting the EUCT‑NS manual‐label class counts (0:72, 1:26, 2:43) into the simulator, yielding a baseline of 0.36 under random labeling.
  - Training the classifier: We computed a “do‐nothing” weighted recall baseline by inputting the EUCT‑NS manual‐label class counts into the simulator, yielding a baseline of 0.49 under random sampling
  - Active learning: We computed a retrospective "do-nothing" weighted accuracy and recall using the class counts (0: 72, 1:31, 2:37) from the predicted labels of the active learning procedure into the simulator, yielding a baseline of 0.36 and 0.38, respectively.

- **Leave-One-Out-Cross-Validation**
  - TF‑IDF (1–3 grams) + Complement Naïve Bayes  
  - Leave‑One‑Out Cross‑Validation on EUCT‑NS (n = 190)  
  - Metrics: balanced accuracy (0.58), weighted F₁ (0.61)
  
- **Active Learning**  
  - Uncertainty sampling on NS‑HRA (n = 694)  
  - 20 iterations, batch size = 7 (total 140 labels)  
  - Tracks balanced accuracy & per‑class F₁

> **Note:** Included code for PR-CURVE thresholding but did not have space to include in the 2-page abstracts

- **PR‑Curve Thresholding**  
  - One‑vs‑rest precision–recall curves  
  - Class‑specific thresholds for ≥ 0.70 recall  

