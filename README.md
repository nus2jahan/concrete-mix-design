# 🏗️ Concrete Mix Design & Aggregate Analysis GUI Application on MATLAB

[![MATLAB](https://img.shields.io/badge/MATLAB-Base_Functionality-orange)](https://www.mathworks.com/products/matlab.html)
[![Engineering](https://img.shields.io/badge/Industry-Civil_Engineering-blue)](https://www.asce.org/)
[![Documentation](https://img.shields.io/badge/Status-Complete-green)](https://github.com/nus2jahan/concrete-mix-design)

A comprehensive, modular MATLAB application designed for the calculation, estimation, and visualization of concrete mix proportions and aggregate properties. This repository provides a complete analytics dashboard for civil and structural engineering researchers, automating complex computational pipelines from laboratory data to publication-ready results.

---

## 📖 Overview

This repository contains a modular, script-based analytics dashboard engineered to bridge the gap between raw laboratory data and structural design requirements. Built on base MATLAB, the suite integrates standard mix design methodologies (ACI & British), physical property visualization, and advanced economic estimation.

The application automates:
*   **Absolute Volume Determination** for precise batching.
*   **Moisture Content Adjustment** for real-world field conditions.
*   **Fineness Modulus (FM) Calculation** via standardized sieve analysis.
*   **Multi-standard Mix Proportioning** (ACI 211.1 and British Standard).
*   **Semilogarithmic Gradation Plotting** for quality control.

---

## ✨ Comprehensive Features

### 1. Advanced Mix Design Methodologies
* **Dual-Standard Implementation:** Toggle between **ACI 211.1 (American)** and **British Standard** approaches to compare international design philosophies.
* **Smart Interpolation Engine:** Uses **linear interpolation algorithms** to determine precise mixing water and entrapped/entrained air content, eliminating manual lookup table errors.
* **Dynamic Unit Management:** Full-scale switching between the **Metric System** (mm, MPa, kg) and the **Imperial System** (inches, psi, lb) to maintain mathematical consistency.

### 2. Automated Aggregate Analysis
* **Sieve Analysis Module:** Converts raw laboratory mass data into individual and cumulative mass retained, as well as percent finer.
* **Fineness Modulus (FM) Engine:** Mathematically processes standardized sieve fractions to calculate the FM, a primary indicator for particle size distribution.
* **Dynamic Moisture Adjustment:** Automatically adjusts batch water requirements based on measured **Absorption Capacity** and **Field Moisture Content**.

### 3. Advanced Visualization & Data Output
* **Semilog Gradation Engine:** Generates publication-ready semilogarithmic plots (Sieve Opening vs. Percent Finer) to identify "gap-graded" vs. "well-graded" aggregates.
* **Visual Grading Confirmation:** High-fidelity plotting to allow engineers to visually inspect distribution against standard grading envelopes.
* **Structured CLI Reporting:** Outputs highly formatted, matrix-style tables in the Command Window for easy data entry.

### 4. Economic & Volumetric Estimation
* **Absolute Volume Translation:** Converts all ingredients into exact absolute volumes using specific gravities, ensuring the final yield matches the design volume.
* **Batch Costing:** Integrates localized material unit pricing to provide real-time cost estimation per unit volume.
* **Trial Mix Calculation:** Automates the calculation of required volumes for experimental specimens (Cylinders, Rectangular, or Square blocks).

---

## 🧪 Methodology: ACI 211.1 & Mathematical Formulations

The suite operates on the **Absolute Volume Method**, which is more precise than the bulk volume method as it accounts for the interstitial voids between particles.

### 1. Mass-Volume Conservation
The core of the mix design is the principle that the sum of the volumes of all constituent parts must equal the total volume of the concrete batch:

$$V_{total} = V_{water} + V_{cement} + V_{coarse\_agg} + V_{fine\_agg} + V_{air}$$

To ensure accuracy, the absolute volume of each solid ingredient is derived from its mass and specific gravity:
$$\text{Volume}_{i} = \frac{\text{Mass}_{i}}{\text{Specific Gravity}_{i} \times \rho_{w}}$$
*(Where $\rho_{w}$ is the density of water)*

### 2. Sieve Analysis & Grading
The **Fineness Modulus (FM)** is calculated via the exact linear sum of the cumulative percentages retained on a standardized set of sieves:
$$\text{FM} = \frac{\sum \text{Cumulative Percentage Retained}}{\text{Number of Sieves}}$$

### 3. Iterative Remainder Logic
To eliminate truncation errors (rounding errors that accumulate in manual calculations), the script uses a **Mathematical Remainder Approach**. It calculates the volumes of water, cement, coarse aggregate, and air first, then assigns the remaining volume to the fine aggregate:
$$V_{fine\_agg} = V_{total} - (V_{water} + V_{cement} + V_{coarse\_agg} + V_{air})$$

---

## 🚀 Getting Started

### Prerequisites
* **Software:** MATLAB (R2018a or newer is highly recommended for optimal graphical rendering).
* **Dependencies:** This suite relies on **Base MATLAB** functionality. No additional Toolboxes (like Optimization or Statistics) are required.

### 🛠 Installation & Environment Setup
1.  **Download/Clone:** Download the repository as a ZIP file or use Git:
    ```bash
    git clone https://github.com/nus2jahan/concrete-mix-design.git
    ```
2.  **Set Working Directory:** Open MATLAB and navigate to the `concrete-mix-design` folder. 
    * *Crucial:* Ensure the folder name appears in the MATLAB path bar at the top of the screen.
    * *Verification:* Type `pwd` in the Command Window to confirm you are inside the project directory.
3.  **Verify Pathing:** To ensure MATLAB can see the script, you can optionally type `addpath(genpath(pwd))` in the Command Window.

### 💻 Operational Workflow (How to Use)
1.  **Launch the Suite:** In the Command Window, simply type the master script name and press Enter:
    ```matlab
    Group_3
    ```
2.  **Sequential Data Entry:** The program will initiate a **Command Line Interface (CLI)**. Follow the on-screen prompts. You will be asked for:
    * **Project Scope:** Metric or Imperial units.
    * **Structural Requirements:** Target compressive strength (f'c) and Slump.
    * **Exposure Conditions:** Environmental severity (e.g., sulfate or freeze-thaw).
    * **Material Properties:** Specific gravities and moisture content of aggregates.
3.  **Review Outputs:** Once the calculations are complete, the software will generate:
    * A tabular breakdown of the mix proportions (Mass and Volume).
    * Cost estimates per unit volume.
    * A semilogarithmic gradation plot.

---

## ⚠️ Troubleshooting

| Issue | Description & Resolution |
| :--- | :--- |
| **Unrecognized Function** | **Pathing Error:** MATLAB cannot find `Group_3.m`. Ensure you are in the correct folder and that the file is not named differently (case-sensitive). |
| **Graphics/Plot Failures** | **Display Issue:** Ensure MATLAB figure windows are not minimized or docked behind the main editor. Check your OS graphics driver if plots do not appear. |
| **Unit Instability** | ⚠️ **CRITICAL:** Do not attempt to "switch" units halfway through a session. If you start in Metric, you must complete the session in Metric. Mixing units will result in mathematically impossible volumes. |

## 📂 Project Structure

```text
concrete-mix-design/
├── Group_3.m                    # Primary computational engine (ACI/British logic, CLI, & Plots)
├── aci_trial_cost_sieve.pdf      # Comprehensive methodology documentation & reference tables
└── README.md                    # Project documentation
