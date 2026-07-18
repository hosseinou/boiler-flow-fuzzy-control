# Boiler Flow Control: PID vs. Fuzzy Logic

This repository contains a MATLAB/Simulink simulation comparing the performance of a conventional Proportional-Integral-Derivative (PID) controller against an intelligent Fuzzy Logic Controller (FLC). 

This project was developed for the "Computer Applications in Control" coursework to control the temperature and steam flow parameters of a chemical plant boiler.

## Project Overview
Industrial boiler systems are highly sensitive to environmental changes and nonlinearities. While classical PID controllers are standard in the industry, they often struggle with large overshoots and long settling times in complex systems. 

This project mathematically models a boiler plant and simulates two parallel control loops to demonstrate the superiority of Fuzzy Logic in suppressing overshoot and improving transient response.

## System Architecture

### 1. The Plant Model
The boiler system is modeled using experimental data, resulting in the following third-order continuous-time transfer function:
$G(s) = \frac{5(s+1)}{s(s+1)(s+6)}$

### 2. Conventional PID Controller
A classical feedback loop was established and tuned using Ziegler-Nichols frequency response criteria. The resulting parameters are:
*   **Proportional (P):** 30
*   **Integral (I):** 21.2
*   **Derivative (D):** 9

### 3. Fuzzy Logic Controller (FLC)
To optimize the system, a Mamdani-type Fuzzy Inference System was designed to replace the linear PID calculation:
*   **Inputs (2):** `Error` ($e$) and `Change in Error` ($\Delta e$).
*   **Output (1):** Controller Output ($u$).
*   **Membership Functions:** 7 linguistic variables (NB, NM, NS, ZO, PS, PM, PB) utilizing triangular and trapezoidal shapes.
*   **Rule Base:** A comprehensive 49-rule IF-THEN matrix processes the heuristic logic.
*   **Defuzzification:** Centroid method.

## Performance Comparison
The simulation proves that the Fuzzy Logic Controller significantly outperforms the conventional PID controller in handling the plant's nonlinearities:
*   **Maximum Overshoot:** Reduced from 47.3% (PID) to 9.35% (Fuzzy).
*   **Settling Time:** Improved from 10.14 seconds (PID) to 7.18 seconds (Fuzzy).

## Repository Structure
*   `fuzzy_hw3.slx`: The primary Simulink model containing both the PID and Fuzzy control loops for direct step-response comparison.
*   `fuzzy_hw1.fis`: The Fuzzy Inference System defining the membership functions and the 49-rule base.
*   `HW3_Report.pdf`: Comprehensive project report detailing the stability analysis, Bode plots, and Simulink scope outputs.

## How to Run
1. Clone this repository.
2. Open MATLAB and ensure the Fuzzy Logic Toolbox is installed.
3. Open `fuzzy_hw3.slx` in Simulink.
4. Ensure the Fuzzy Logic Controller block is linked to `fuzzy_hw1.fis`.
5. Run the simulation and open the Scope blocks to view the comparative step responses.
