# Concrete Mix Design and Analysis GUI Application

A comprehensive, modular MATLAB application designed for the calculation, estimation, and visualization of concrete mix proportions and aggregate properties.

## 📖 Overview

This repository contains a modular, script-based analytics dashboard engineered for civil and structural engineering researchers. Built entirely on base MATLAB, it seamlessly integrates standard mix design methodologies, laboratory data processing, and physical property visualization. 

The suite automates complex computational pipelines including absolute volume determination, moisture content adjustment, Fineness Modulus (FM) calculation, multi-standard mix proportioning, and semilogarithmic aggregate gradation plotting.

---

## ✨ Comprehensive Features

### 1. Advanced Mix Design Methodologies
* **Dual-Standard Implementation:** Users can toggle between the **ACI 211.1 (American)** and **British Standard** approaches. This allows for comparative studies between different international design philosophies within a single environment.
* **Smart Interpolation Engine:** Instead of relying on manual lookups from physical tables, the software utilizes **linear interpolation algorithms**. This calculates precise mixing water requirements and entrapped/entrained air content by calculating values between standard data points, ensuring high precision in non-standard environmental conditions.
* **Dynamic Unit Management:** The suite supports full-scale switching between the **Metric System** (mm, MPa, kg) and the **Imperial System** (inches, psi, lb). This prevents the common manual error of "unit mixing" by enforcing consistency throughout the entire computational pipeline.

### 2. Aggregate & Signal Processing
* **Automated Sieve Analysis:** Automates the conversion of raw laboratory mass data into meaningful metrics. It computes:
    * Individual and cumulative mass retained per sieve.
    * Cumulative percent retained and percent finer.
    * Grading curves necessary for quality control.
* **Fineness Modulus (FM) Engine:** A dedicated module that mathematically processes standardized sieve fractions to compute the FM. This serves as a primary indicator for the particle size distribution of fine aggregates, influencing the workability and water demand of the mix.
* **Dynamic Moisture Adjustment:** The software accounts for real-world laboratory conditions by adjusting batch water requirements based on the measured **Absorption Capacity** and **Field Moisture Content** of the aggregates, ensuring the water-to-cement ratio remains constant in the final mix.

### 3. Advanced Visualization & Data Output
* **Semilog Gradation Engine:** Generates publication-ready semilogarithmic plots (Sieve Opening vs. Percent Finer). These graphs are essential for identifying "gap-graded" vs. "well-graded" aggregates.
* **Visual Grading Confirmation:** Utilizes MATLAB's high-fidelity plotting engine to allow engineers to visually inspect particle size distribution against standard grading envelopes.
* **Structured CLI Reporting:** Rather than simple text dumps, the software outputs highly formatted, matrix-style tables in the Command Window, facilitating easy data entry into laboratory notebooks or Excel.

### 4. Cost & Volume Estimation
* **Absolute Volume Translation:** Moves beyond simple mass-based mixing by converting all ingredients into their exact **Absolute Volumes** using specific gravities. This ensures that the final yield matches the design volume exactly.
* **Economic Analysis (Batch Costing):** Integrates localized material unit pricing to provide a real-time cost estimation per unit volume of concrete, factoring in the cost of cement, aggregates, water, and admixtures.

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
├── image_004b64.png              # Sample output: Semilogarithmic gradation visualization
└── README.md                    # Project documentation
