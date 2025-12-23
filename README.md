# KF-TSER: Kalman Filtered Temporal Speech Emotion Recognition

## Authors
- **Marouane EL HIZABRI**
- **Ismail HAYOUKANE**
- **Abdelfattah BEZZAZ**

---

## Overview

**KF-TSER** (Kalman Filtered Temporal Speech Emotion Recognition) is a speech emotion recognition framework designed to improve the robustness of frame-level neural predictions by explicitly modeling temporal dynamics in speech.

The system combines:
- A **frame-level neural classifier (MLP)** trained on short-term acoustic features
- **Kalman filtering** to smooth noisy frame-level emotion probabilities
- **Score fusion and utterance-level aggregation** to produce stable final predictions

KF-TSER significantly outperforms standalone frame-level classification by exploiting the temporal inertia inherent in human speech.

---

## Motivation

Frame-level speech emotion recognition suffers from:
- High variability across adjacent frames
- Sensitivity to transient acoustic artifacts
- Emotion “flickering” in short-term predictions

KF-TSER addresses these issues by treating frame-level predictions as **noisy measurements** and applying **Kalman-based temporal stabilization**, resulting in more reliable utterance-level emotion decisions.

---

## System Pipeline

1. **Feature Extraction**
   - Short-term acoustic features are extracted from speech signals.
   - Each frame is treated as an independent observation.

2. **Frame-Level Classification (MLP)**
   - A Multi-Layer Perceptron is trained using cross-entropy loss.
   - Outputs per-frame emotion probability vectors.

3. **Kalman Temporal Filtering**
   - Frame-level probabilities are smoothed using a Kalman filter.
   - Temporal continuity constraints suppress spurious predictions.

4. **Score Fusion & Utterance-Level Decision**
   - Smoothed frame scores are fused and averaged.
   - A single emotion label is assigned per utterance.

---

## Performance Summary

| System | Accuracy |
|------|----------|
| Frame-level MLP | 60.6% |
| **KF-TSER (Proposed)** | **82.3%** |

**Absolute gain:** +21.7 percentage points

These results demonstrate the effectiveness of Kalman-based temporal modeling for speech emotion recognition.

---

## Repository Structure

