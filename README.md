# DESIGN OF BANDGAP REFERENCE WITH NONLINEAR TEMPERATURE COMPENSATION USING GPDK 90NM TECHNOLOGY
**Authors:** Nguyen Quoc Huy    

**Organization:** Hanoi University of Industry  

**Tool:** Cadence Virtuoso 

![Logo](Figures/ICD_LAB.jpg)

**Technology/Process:** 90nm  

**Project Duration:** February, 2026 to March, 2026  

## Abstract  
This project presents the design and vertification of high-performance CMOS Bandgap Reference (BGR) aimed at providing a stable 1.2V output. By intergrating advanced higher-order curvature correction, the architecture achieves a superior temperature coefficient, ensuring high precision across varying thermal conditions.
## 1. Introduction  
Bandgap Reference (BGR) circuits are critical modules in most integrated circuit systems and are widely used in analog circuits, digital circuits, and mixed-signal circuits such as memory circuits, A/D converters, and low dropout linear regulators. BGR circuits provide temperature-independent voltage or currents for the system-on-a-chip (SoC), and their performance determines the quality of the entire SoC. With the development of the CMOS process, the feature size of integrated circuits continues to decrease, and the operation voltage of the electronic system is becoming increasingly lower. Low-voltage and high-precision BGR circuit have received widespread attention.  
The operational framework of a BGR is based on merging two distinct voltage characterized by contrasting thermal behaviors. A voltage linked to the base-emitter voltage (VBE) of a bipolar junction transistor (BJT), which displays a Complementary to Absolute Temperature (CTAT) coefficient, and a derived from the VBE variance (∆VBE) between two BJTs running at different current densities, exhibiting a Proportional to Absolute Temperature (PTAT) coefficient. By mathematically balancing these two components, a Zero-Temperature-Coefficient (ZTC) voltage can be established at a targeted temperature point. Furthermore, this work proposes an optimized BGR architecture specifically aimed at suppressing high order nonlinear temperature components to achieve superior precision.
## 2. Design Specification  
The target pergormance metrics for the Bandgap Reference are ourlined in Table 1. The design was required to operate reliably across the Process, Voltage and Temperature (PVT) corners detailed in Table 2.
### Specification  
| Parameter   | Min    | Typ   | Max    | Unit   | Notes                                                                               |
|:------------|:-------|:------|:-------|:-------|:------------------------------------------------------------------------------------|
| VDD         | 1.8    | 2     | 2.2    | V      |                                                                                     |
| Temp        | -40    | 25    | 125    | C      |                                                                                     |
| VBG         | 1.188  | 1.2   | 1.212  | V      |                                                                                     |
| Temp Co.    |        |       | 20     | ppm/°C |                                                                                     |
| Iq          |        | 50u   | 100u   | A      |                                                                                     |
| PSR (DC)    |        |       | -60    | dB     |                                                                                     |
| PSR (10k)   |        |       | -40    | dB     |                                                                                     |
| Function    |        |       |        |        | Startup, Curvature compensation, Trimming for process variation                     |  

**Table 1: Design Specification for the Bandgap Reference.**    

### Corner Setting  
|               | P             | V              | T         |
|---------------|---------------|----------------|-----------|
| **MOS**       | SS SF FS FF   |                |           |
| **BJT**       | SS FF         | 2V +/-10%      | -40 125   |
| **RES**       | SS FF         | 2V +/-10%      | -40 125   |
| **CAP**       | SS FF         |                |           |
| **MONTE CARLO** | Process + Mismatch |         |           |  

**Table 2: Corner Setting across Process, Voltage and Temperature (PVT).**

## 3. Circuit Architecture and Implementation
An optimized architecture, integrating multiple high-performance techniques, was chosen to fulfill the demanding technical requirements. Figure 1(a) depicts the fundamental block diagram of this proposed BGR.  
![Block Diagram](Figures/BlockDiagram.png)  
**Figure 1(a): Overall BGR Block Diagram showing key functional blocks.**  

To further eliminate high-order temperature terms, a BGR circuit incorporating curvature compensation is designed, as illustrated in Figure 1(b). The primary elements and methodologies are explored in the following sections.
![General Schematic](Figures/General_Schematic.png)
**Figure 1(b): Overall BGR Block Diagram showing key functional blocks.**  

### 3.1. Error Amplifier  
Since the base-emitter voltage (VBE) typically operates around 0.7V, a PMOS-input differential pair is preferred to accommodate this low common-mode input level. The primary role of this amplifier is to equalize the currents in the two core branches containing Q0 and Q2, there by ensuring precision. Consequently, a PMOS-input folded-cascode amplifier was selected, as depicted in Figure 2.  

![Error Amplifier](Figures/Error_Amplifier.png)  
**Figure 2: Error Amplifier schematic: PMOS-input Folded Cascode Amplifier**  

The folded-cascode topology provides high gain and good PSRR in a single stage, as summarized in the comparison table (Figure 3).  












