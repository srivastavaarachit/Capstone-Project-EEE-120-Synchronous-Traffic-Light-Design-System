# Capstone-Project-EEE-120-Synchronous-Traffic-Light-Design-System
EEE 120 Capstone: Design and simulation of a synchronous 6-state traffic light controller using D-flip-flops. Features standard cycling, 4-way flash, and dynamic toggling modes. Includes full engineering lifecycle documentation: stakeholder reqs, state diagrams, minimized logic, and Digital software simulations.
# 🚦 Synchronous Traffic Light Controller | EEE 120 Capstone

![Project Status](https://img.shields.io/badge/Status-Complete-success)
![Tool](https://img.shields.io/badge/Simulation-Digital-blue)
![Course](https://img.shields.io/badge/Course-EEE%20120-maroon)

## 📖 Project Overview
**Author:** Rachit Srivastava  
**Instructor:** Steven Millman  
**Date:** May 1, 2025  

This repository hosts the **Capstone Design Project** for EEE 120: a fully functional **Synchronous Sequential Traffic Light Controller**. Designed to replace manual timing with robust digital logic, this system manages traffic flow, ensures pedestrian safety, and includes dynamic operational modes.

The project documents the full engineering lifecycle—from stakeholder interviews and value proposition analysis to logic minimization, circuit simulation, and final validation.

---

## 🧠 Design Philosophy & Value
We didn't just build a circuit; we solved a problem.
* **Technological:** Replaced analog timers with a precision digital logic system.
* **Societal:** Enhanced road safety with clear, rule-based transitions.
* **Financial:** Reduced the need for human traffic personnel.
* **Environmental:** Optimized flow to reduce engine idling and emissions.

---

## 👥 Stakeholder Feedback & Requirements
The design was shaped by real-world input from three key stakeholders:

1.  **Kavya (Roommate):**
    * *Need:* Pedestrian safety & clear light patterns.
    * *Feature:* **Emergency Override Mode**.
2.  **Prince (CSE Major):**
    * *Need:* Debugging simplicity & startup safety.
    * *Feature:* **All-Red State** & **Asynchronous Reset**.
3.  **Daksh (CSE Major):**
    * *Need:* Gate efficiency & dynamic toggling.
    * *Feature:* **"Surprise Mode"** & logic minimization.

---

## ⚙️ Technical Specifications

### System States
The controller operates on a 6-state machine utilizing **D-Flip-Flops**:
* **S0 (000):** All Red (Stop)
* **S1 (001):** Main Green
* **S2 (010):** Main Yellow
* **S3 (011):** Side Green
* **S4 (100):** Side Yellow
* **S5 (101):** *Reserved/Intermediate*


### Operational Modes (Input C[1:0])
| Mode | Input (C) | Behavior |
| :--- | :---: | :--- |
| **Normal Cycle** | `00` | Standard traffic flow: All Red → Main Green → Yellow → Side Green → Yellow → All Red. |
| **4-Way Flash** | `01` | **Main Red** and **Side Red** toggle alternately (simulating a 4-way stop). |
| **Priority Flash** | `10` | **Side Red** toggles, while **Main Yellow** stays permanently ON. |
| **Surprise Mode** | `11` | Both **Main Green** and **Side Green** toggle every cycle for rapid crossing. |

### Minimized Logic Equations (Design #1)
The final circuit was optimized for gate efficiency using the following Boolean equations:

```math
MG = A'BC'
MY = AB'C
MR = A + B'C'
SG = A'B'C
SY = AB'C'
SR = A + BC
