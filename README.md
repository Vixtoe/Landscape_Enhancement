# Landscape Image Enhancement Using HSV Space & Spatial Filtering

> A MATLAB-based image processing pipeline designed to improve shadow visibility, compress overexposed highlights, and enhance visual sharpness in high-dynamic-range landscape photographs.

---

## Project Overview

High-contrast landscape photographs—such as sunset scenes—often suffer from underexposed foreground shadows alongside clipped, overexposed regions near the sun[cite: 3]. Direct global enhancements often result in blown-out highlights or unnatural color shifts[cite: 3]. 

This project implements a targeted image enhancement pipeline in MATLAB using HSV color space transformations, local gamma adjustments, highlight compression, and unsharp masking to enhance dark regions while preserving natural colors and highlight details[cite: 3].

---

## Core Objectives & Problem Statement

* **Foreground Shadow Recovery:** Lift underexposed foreground details (e.g., people and decks) without introducing noise or unnatural color shifts[cite: 3].
* **Highlight Compression:** Mitigate extreme solar overexposure and sun glare[cite: 3].
* **Color Preservation & Sharpening:** Maintain natural hue characteristics while improving edge contrast and fine structural details[cite: 3].

---

## Technical Pipeline & Implementation

1. **HSV Color Space Transformation:** Converts the normalized RGB image (`im2double`) into HSV to isolate illumination ($V$) from chromaticity ($H, S$)[cite: 3].
2. **Shadow Recovery (Power-Law / Gamma Correction):** Applies a power-law transformation ($V^{\gamma}$ with $\gamma = 0.45$) specifically to masked dark regions ($V < 0.50$) to lift shadows[cite: 3].
3. **Selective Saturation Boost:** Increases saturation ($S + 0.18$) within shadow masks to prevent washed-out tones[cite: 3].
4. **Highlight & Sun Compression:** Detects overexposed regions ($V > 0.92$) and applies a compressive gamma ($V^{1.8}$) with slight saturation reduction to tone down sun glare[cite: 3].
5. **Spatial Filtering & Unsharp Masking:** Converts the processed image to grayscale luminance ($Y$), extracts a detail layer using Gaussian filtering ($Y - Y_{\text{blurred}}$), and adds scaled high-frequency details back to RGB channels for edge sharpening[cite: 3].

---

## Tech Stack & Tools

* **Language & Environment:** MATLAB
* **Functions & Methods:** `rgb2hsv`, `hsv2rgb`, `imgaussfilt`, Mask-Based Gamma Transformations, Histogram Analysis[cite: 3]
* **Primary Script:** `sunset_shadow_visible_balanced_sun.m`[cite: 3]

---

## Documentation & Artifacts

* **Source Script:** Available in [`scripts/sunset_shadow_visible_balanced_sun.m`](scripts/sunset_shadow_visible_balanced_sun.m)[cite: 3]
* **Presentation Deck:** [View Presentation Slides (PDF)](Image%20Enhancement%20Project.pdf?raw=true)[cite: 3]

---

## Team & Individual Contributions

* **Author:** Chanoudom Tann (Victor)[cite: 3]
* **Individual Contributions:**
  * Designed and tuned the HSV-based selective shadow and highlight masking logic[cite: 3].
  * Developed the spatial Gaussian detail extraction and unsharp masking workflow in MATLAB[cite: 3].
  * Performed histogram comparisons and created project documentation[cite: 3].

---

## Project Structure

```text
landscape-image-enhancement/
├── data/
│   └── sunset.JPG
├── docs/
│   └── Image Enhancement Project.pdf
├── scripts/
│   └── sunset_shadow_visible_balanced_sun.m
└── README.md
