# DESIGN OF A HIGH-PRECISION VOLTAGE-MODE BANDGAP REFERENCE IMPLEMENTED IN 90NM CMOS TECHNOLOGY
**Authors:** Nguyen Quoc Huy    

**Organization:** Hanoi University of Industry  

**Tool:** Cadence Virtuoso 

![Logo](Figures/ICD_LAB.jpg)

**Technology/Process:** 90nm  

**Project Duration:** February, 2026 to March, 2026  

## Abstract  
This project presents the design and vertification of high-performance CMOS Bandgap Reference (BGR) aimed at providing a stable 1.2V output. By intergrating advanced higher-order curvature correction, the architecture achieves a superior temperature coefficient, ensuring high precision across varying thermal conditions.
## 1. Introduction  
Bandgap Reference (BGR) circuits are critical modules in most integrated circuit systems and are widely used in anaalog circuits, digital circuits, and mixed-signal circuits such as memory circuits, A/D converters, and low dropout linear regulator. BGR circuits provide temperature-independent voltage or currents for the system-on-a-chip (SoC), and their performance determines the quality of the entire SoC. With the development of the CMOS process, the feature size of integrated circuits continues to decrease, and the operation voltage of the electronic system is becoming increasingly lower. Low-voltage and high-presicion BGR circuit have received widespread attention. 

## 2. Design Specification  

### Specification  
| Parameter   | Min    | Typ   | Max    | Unit   | Notes                                                                               |
|:------------|:-------|:------|:-------|:-------|:------------------------------------------------------------------------------------|
| VDD         | 1.8    | 2     | 2.2    | V      |                                                                                     |
| Temp        | -40    | 25    | 125    | C      |                                                                                     |
| VBG         | 1.188  | 1.2   | 1.212  | V      |                                                                                     |
| Temp Co.    |        |       | 10     | ppm    |                                                                                     |
| Iq          |        | 100u  | 150u   | A      |                                                                                     |
| PSR (DC)    |        |       | -60    | dB     |                                                                                     |
| PSR (10k)   |        |       | -40    | dB     |                                                                                     |
| Function    |        |       |        |        | Startup, Curvature compensation, Trimming for process variation                     |
### Corner Setting  
|               | P             | V              | T         |
|---------------|---------------|----------------|-----------|
| **MOS**       | SS SF FS FF   |                |           |
| **BJT**       | SS FF         | 2V +/-10%      | -20 125   |
| **RES**       | SS FF         | 2V +/-10%      | -20 125   |
| **CAP**       | SS FF         |                |           |
| **MONTE CARLO** | Process + Mismatch |         |           |
## 3. Circuit Architecture and Implementation  


