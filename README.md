# GridSense

**A Self-Calibrating, Map-Aware Computer Vision System for Automated Traffic Violation Detection and Evidence Generation**

> Submission for **Problem Statement 3 — Automated Photo Identification and Classification for Traffic Violations Using Computer Vision**, Gridlock Hackathon 2.0.
> This problem statement requires only an **idea / concept submission** — no working model, implementation, or dataset is mandated. This repository contains the concept materials, not a deployed system.

---

## The problem

Today's traffic camera enforcement systems are limited by three structural gaps, beyond the core detection task itself:

- **Doesn't scale** — every new camera needs manual, on-site calibration of stop-lines, lane direction, and restricted zones in pixel coordinates.
- **Rigid logic** — a separate hardcoded model/rule per violation type makes new violation categories expensive to add.
- **Weak evidence** — a single still photo is often insufficient or contestable as legal evidence for judgment-based violations (signal timing, stop-line crossing).

## The idea

GridSense reframes automated violation detection as a **calibration and reasoning problem**, not just a detection problem, through three core pillars:

| Pillar | What it does |
|---|---|
| **Map-Aware Auto-Calibration** | Uses geo-referenced road network data (lane geometry, stop-lines, one-way zones) to automatically calibrate any new camera — no manual zone-drawing. |
| **Scene-Graph Violation Reasoning** | Represents each frame as a graph of vehicles, riders, pedestrians, signal state, and lane zones; violations are inferred from relationship patterns rather than hardcoded per-violation classifiers. |
| **Junction Memory** | A feedback loop where human-reviewer rejections locally adapt each camera's confidence thresholds, letting one global model adjust to site-specific false-positive patterns without full retraining. |

A **multi-frame, tamper-evident evidence chain** (rather than a single static photo) further strengthens legal defensibility.

Full methodology, assumptions, and evaluation strategy are in the [concept note](./GridSense_Concept_Note.pdf).

## Live concept demo

🔗 **[View the concept demo](https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/)** *(replace with your GitHub Pages URL after enabling Pages in repo Settings)*

The demo site walks through the problem, the three pillars, the system architecture, and an illustrative evidence-review dashboard mockup.

## Repository contents

| File | Description |
|---|---|
| `index.html` | Concept demo site (also serves as the Demo Link via GitHub Pages) |
| `assets/architecture.png` | System architecture diagram |
| `assets/dashboard.png` | Evidence review dashboard UI mockup |
| `GridSense_Concept_Note.pdf` | Full concept note — approach, methodology, assumptions, evaluation strategy |
| `README.md` | This file |

## System overview

```
Preprocessing → Detection & Tracking → Map-Calibration → Violation Reasoning
      → Plate Recognition → Evidence Generation → Review & Analytics
                     ↑___________ Junction Memory feedback ___________|
```

| Stage | Key techniques |
|---|---|
| Preprocessing | CLAHE, low-light enhancement, de-rain/dehaze, deblurring |
| Detection & Tracking | Shared-backbone detector (YOLO/RT-DETR) + ByteTrack |
| Map-Calibration | Homography estimation from GPS/orientation + road network data |
| Violation Reasoning | Scene-graph construction + pattern evaluation |
| Plate Recognition | Small-object plate detector + OCR (PaddleOCR/CRNN) |
| Evidence Generation | Annotated overlays, structured metadata, hash-chained log |
| Review & Analytics | Confidence-gated human review, trend dashboards |

## Evaluation strategy (proposed)

Since no proprietary dataset is mandated for this problem statement, evaluation is proposed against public datasets — e.g. the India Driving Dataset (IDD) for detection, public helmet-detection datasets for classification, and public Indian license-plate datasets for OCR — using mAP, Precision/Recall/F1, calibration accuracy vs. a manual baseline, and end-to-end latency/throughput. Full detail in the concept note.

## Note on scope

This is an idea/concept submission as explicitly permitted for Problem Statement 3. The demo site and dashboard mockup are illustrative concept visuals, not outputs of a live or trained model.

---

*Gridlock Hackathon 2.0 — Problem Statement 3*
