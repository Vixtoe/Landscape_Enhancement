# Landscape Image Enhancement Using HSV Space & Spatial Filtering

> A MATLAB-based image processing pipeline designed to improve shadow visibility, compress overexposed highlights, and enhance visual sharpness in high-dynamic-range landscape photographs.

---

## Project Overview

High-contrast landscape photographs—such as sunset scenes—often suffer from underexposed foreground shadows alongside clipped, overexposed regions near the sun. Direct global enhancements often result in blown-out highlights or unnatural color shifts. 

This project implements a targeted image enhancement pipeline in MATLAB using HSV color space transformations, local gamma adjustments, highlight compression, and unsharp masking to enhance dark regions while preserving natural colors and highlight details.

---

## Core Objectives & Problem Statement

* **Foreground Shadow Recovery:** Lift underexposed foreground details (e.g., people and decks) without introducing noise or unnatural color shifts.
* **Highlight Compression:** Mitigate extreme solar overexposure and sun glare.
* **Color Preservation & Sharpening:** Maintain natural hue characteristics while improving edge contrast and fine structural details.

---

## Technical Pipeline & Implementation

1. **HSV Color Space Transformation:** Converts the normalized RGB image (`im2double`) into HSV to isolate illumination ($V$) from chromaticity ($H, S$).
2. **Shadow Recovery (Power-Law / Gamma Correction):** Applies a power-law transformation ($V^{\gamma}$ with $\gamma = 0.45$) specifically to masked dark regions ($V < 0.50$) to lift shadows.
3. **Selective Saturation Boost:** Increases saturation ($S + 0.18$) within shadow masks to prevent washed-out tones.
4. **Highlight & Sun Compression:** Detects overexposed regions ($V > 0.92$) and applies a compressive gamma ($V^{1.8}$) with slight saturation reduction to tone down sun glare.
5. **Spatial Filtering & Unsharp Masking:** Converts the processed image to grayscale luminance ($Y$), extracts a detail layer using Gaussian filtering ($Y - Y_{\text{blurred}}$), and adds scaled high-frequency details back to RGB channels for edge sharpening.

---

## Tech Stack & Tools

* **Language & Environment:** MATLAB
* **Functions & Methods:** `rgb2hsv`, `hsv2rgb`, `imgaussfilt`, Mask-Based Gamma Transformations, Histogram Analysis
* **Primary Script:** `sunset_shadow_visible_balanced_sun.m`

---

## Documentation & Artifacts

* **Source Script:** Available in [`scripts/sunset_shadow_visible_balanced_sun.m`](scripts/sunset_shadow_visible_balanced_sun.m)
* **Presentation Deck:** [View Presentation Slides (PDF)](Image_Enhancement_Project.pdf)

---

## Team & Individual Contributions

* **Author:** Chanoudom Tann (Victor)
* **Individual Contributions:**
  * Designed and tuned the HSV-based selective shadow and highlight masking logic.
  * Developed the spatial Gaussian detail extraction and unsharp masking workflow in MATLAB.
  * Performed histogram comparisons and created project documentation.

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
