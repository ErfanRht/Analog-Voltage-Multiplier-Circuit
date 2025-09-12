# Analog Voltage Multiplier Circuit

### Final Project for the Electrical Circuits I Lab at Sharif University of Technology

This repository documents the design, simulation, and physical implementation of an analog voltage multiplier circuit. The project was completed as the final project for the Electrical Circuits I (EC1) course, under the supervision of Dr. Mostafa Zarghani. The circuit takes two analog voltage signals as input and produces an output voltage proportional to their product, using fundamental electronic components.

## Goals
The primary goal of this project is to build a functional analog multiplier using op-amps, diodes, and resistors. The design leverages the non-linear current-voltage characteristic of diodes to perform mathematical operations purely in the analog domain. The entire process, from theoretical design and software simulation to PCB layout and final assembly, is documented here.

### Key Specifications
* **Functionality**: Multiplies two analog input signals.
* **Input Voltage Range**: 1V to 2V.
* **Operating Frequency**: 0 to 200 Hz.
* **Power Supply**: Symmetrical ±12V DC.
* **Core Technology**: Op-Amp based logarithmic, summing, and anti-logarithmic amplifiers.
* **Implementation**: Simulated in **LTspice**, designed in **Altium Designer**, and fabricated as a physical PCB.

## Principle of Operation

The circuit's operation is based on a fundamental mathematical principle: **multiplication can be achieved by adding logarithms**.

$$ V_{out} \propto V_{in1} \times V_{in2} $$

This relationship can be transformed into the logarithmic domain:

$$ \ln(V_{out}) = \ln(V_{in1}) + \ln(V_{in2}) + C $$

The circuit implements this principle in three main stages:

1.  **Logarithmic Amplifiers**: The first stage consists of two logarithmic amplifiers, one for each input signal ($V_{in1}$ and $V_{in2}$). An op-amp with a diode in its negative feedback loop is used. The diode's exponential I-V relationship ($I_D \approx I_S e^{V_D / (n V_T)}$) results in an output voltage that is proportional to the natural logarithm of the input voltage.

2.  **Summing Amplifier**: The outputs from the two logarithmic amplifiers are fed into a summing (or adder) circuit. This op-amp configuration adds the two logarithmic signals together, effectively performing the `$\ln(V_{in1}) + \ln(V_{in2})$` operation.

3.  **Exponential (Anti-Log) Amplifier**: The final stage performs the inverse operation. An anti-logarithmic amplifier, which has a diode at its input and a resistor in the feedback loop, takes the summed logarithmic signal and produces an output that is proportional to the exponential of its input. This converts the sum of logarithms back into a product, yielding the final multiplied output signal.

---

## Component Selection

The components were chosen based on the project requirements, availability, and suitability for the specified voltage and frequency ranges.

| Component | Model/Type | Rationale |
| :--- | :--- | :--- |
| **Operational Amplifier** | LM741 | General-purpose, stable performance, and compatible with ±12V supply. |
| **Diode** | 1N4148 | Fast-switching signal diode with a suitable forward voltage for the input range. |
| **Resistors** | 10kΩ, 410kΩ, 470Ω | Through-hole, carbon film resistors selected for defining amplifier gains. |

---

## Implementation Workflow

### 1. Simulation in LTspice
The circuit was first designed and simulated in LTspice to verify its theoretical operation. The simulation confirmed that the circuit correctly multiplies the two sinusoidal input signals.

<img width="100%" src="https://github.com/ErfanRht/Analog-Multiplier-Circuit/blob/main/images/LtSpice_schematic.png" align="center" alt="screenshot" />

### 2. PCB Design in Altium Designer
After successful simulation, the schematic was transferred to Altium Designer to create a professional printed circuit board (PCB). The layout was optimized for signal integrity and component placement within the required 6x10 cm board size.

<img width="100%" src="https://github.com/ErfanRht/Analog-Multiplier-Circuit/blob/main/images/PCB_design_2d.png" align="center" alt="screenshot" />
<img width="100%" src="https://github.com/ErfanRht/Analog-Multiplier-Circuit/blob/main/images/PCB_design_3d.png" align="center" alt="screenshot" />

### 3. Fabrication and Assembly
The designed PCB was fabricated and assembled by hand-soldering all the through-hole components.

<img width="100%" src="https://github.com/ErfanRht/Analog-Multiplier-Circuit/blob/main/images/photo_2025-09-12_16-41-47.jpg" align="center" alt="screenshot" />
<img width="100%" src="https://github.com/ErfanRht/Analog-Multiplier-Circuit/blob/main/images/photo_2025-09-12_16-41-55.jpg" align="center" alt="screenshot" />


---

## Repository Contents

* `Project.asc`: The LTspice simulation file for the multiplier circuit.
* `EC1_ProjectReport_G05.pdf`: The complete project report submitted for the course (in Persian), containing detailed analysis, simulation results, and images.
* `EC_Project_Phase2_Helps.pdf`: The official project guidelines and help document from the university (in Persian).
* `README.md`: This file.
