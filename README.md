# ⚽ Dribble.AI – Ball Action Tracking in Soccer Videos

Dribble.AI is a deep learning-based system developed for automated ball action spotting in soccer matches. The project leverages the SoccerNet Ball Action Spotting dataset to detect and classify key actions like passes, shots, and goals with high temporal precision. This hybrid architecture combines the spatial strength of CNNs and the temporal modeling capabilities of Transformers to provide real-time, scalable analysis of soccer footage.

---

## 📌 Project Overview

- **Goal:** Accurately localize and classify ball-related actions in soccer videos.
- **Dataset:** [SoccerNet Ball Action Spotting Dataset](https://www.soccer-net.org/tasks/ball-action-spotting)
- **Model:** CNN + Transformer Hybrid Architecture
- **Evaluation Metric:** Mean Average Precision (mAP) at various tolerance levels (as per SoccerNet standards)

---

## 🧠 Architecture 
![System Architecture](Images/system_architecture.jpeg)

- **CNN Backbone:** Extracts spatial features from frames (e.g., ResNet, EfficientNet).
- **Temporal Encoder:** Transformer layers capture sequential context for frame-level predictions.
- **Pooling Layer:** Global Average or GeM pooling for feature condensation.
- **Classifier:** Fully connected layers to predict action class probabilities.

---

## 📈 Results

We evaluated two models trained at different resolutions on the held-out test match *Middlesbrough vs Preston North End*.

- The **224p model** achieved:  
  - **Macro F1 Score:** `0.2947`  
  - **Mean Average Precision (mAP):** `0.4115`  

- The **720p model** significantly improved performance with:  
  - **Macro F1 Score:** `0.5661`  
  - **Mean Average Precision (mAP):** `0.6618`  

### 🔬 Per-Class Metrics Comparison

| Class      | AP (224p) | BA (224p) | MCC (224p) | AP (720p) | BA (720p) | MCC (720p) |
|------------|-----------|-----------|------------|-----------|-----------|------------|
| Cross      | 0.3971    | 0.7784    | 0.3821     | 0.4428    | 0.8007    | 0.4245     |
| Drive      | 0.5750    | 0.6204    | 0.2563     | 0.8246    | 0.7987    | 0.5931     |
| Header     | 0.3210    | 0.6179    | 0.2792     | 0.6251    | 0.6430    | 0.4716     |
| High-Pass  | 0.3481    | 0.5434    | 0.1876     | 0.6104    | 0.7088    | 0.5162     |
| Pass       | 0.5456    | 0.5256    | 0.1264     | 0.8184    | 0.7657    | 0.5303     |
| Throw-in   | 0.2823    | 0.7183    | 0.2773     | 0.6493    | 0.7689    | 0.5330     |

![Prediction Demo](Images/prediction_demo.gif)

The transition to 720p resolution substantially improved the model's ability to detect and localize ball actions across all categories. This was especially evident in high-frequency actions such as `Pass` and `Drive`, which showed notable gains in both Average Precision (AP) and Matthews Correlation Coefficient (MCC). Model performance is expected to improve further with extended 720p video training, which was not completed due to compute constraints.

--- 

## 👥 Authors
- Shagufta Anjum – MCS, University of Illinois Urbana-Champaign
- Nidhi Baheti – MS Statistics, University of Illinois Urbana-Champaign
- Jyot Buch – MS Statistics, University of Illinois Urbana-Champaign
- Varsha Chikkamagaluru – MCS, University of Illinois Urbana-Champaign
