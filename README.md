# Concrete Mix Design and Sieve Analysis

## Overview
[cite_start]This repository contains a MATLAB implementation and accompanying documentation for Concrete Mix Design, primarily utilizing the American Concrete Institute (ACI) 211.1 method[cite: 100, 101]. The script automates the calculation of mix proportions and includes additional modules for the British Method, cost estimation, and sieve analysis of coarse and fine aggregates.

## Features
* [cite_start]**ACI Method Implementation:** Automates the 9-step ACI mix design process, calculating slump, maximum aggregate size, water and air content, w/c ratio, cement content, and aggregate proportions[cite: 111, 112, 113, 114, 115, 116, 117, 118, 119, 120].
* **Sieve Analysis:** Computes the fineness modulus and cumulative retained percentages for aggregate gradation.
* **Visualizations:** Generates semilog gradation curves and plots for water content estimation, air percentage requirements, and water-cement ratio relationships.
* **Unit Flexibility:** Supports inputs in both metric (mm, MPa) and imperial (inches, psi) units.

## Repository Structure
* `src/Group_3.m`: The primary MATLAB script requiring user inputs to compute mix designs and plot relationships.
* [cite_start]`docs/ACI_Mix_Design_Report.pdf`: Theoretical background, tabular data references (such as dry-rodded volumes and mixing water estimations), and example problem calculations[cite: 42, 122, 195].

## Usage
1. Open MATLAB and navigate to the `src` directory.
2. Run the `Group_3.m` script.
3. Follow the command window prompts to define the required variables. 
4. [cite_start]The script will request design parameters, including construction type and target slump[cite: 142, 146].
5. [cite_start]You will need to provide the maximum aggregate size[cite: 185].
6. The script requires the concrete type (air-entrained vs. non-air-entrained) and exposure conditions (mild, moderate, or severe).
7. Finally, input the target mean strength.

## Theoretical Basis
[cite_start]The calculations are grounded in standard ACI 211.1 practices[cite: 101]. Linear interpolation is utilized within the script to determine precise mixing water requirements and air percentages based on standard tabular data for various aggregate sizes and slump conditions.
