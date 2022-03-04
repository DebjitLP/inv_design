# Inverter Design
Inverter design for given rise/fall Delay, rise/fall time and load conditions

## Contents
* [Tools Used](https://github.com/DebjitLP/inv_design#tools-used)
* [Abstract1](https://github.com/DebjitLP/inv_design#abstract1)
* [Schematics_1 in Virtuoso](https://github.com/DebjitLP/inv_design#schematics_1-in-virtuoso)
* [Pre-Layout Simulation Results1](https://github.com/DebjitLP/inv_design#pre-layout-simulation-results1)
* [Layout of the Inverter in Virtuoso (indicating different layers)](https://github.com/DebjitLP/inv_design#layout-of-the-inverter-in-virtuoso-indicating-different-layers)
* [Post-layout Simulation Results1](https://github.com/DebjitLP/inv_design#post-layout-simulation-results1)
* [Pre-Layout vs Post-layout Simulations Results1](https://github.com/DebjitLP/inv_design#pre-layout-vs-post-layout-simulations-results1)
* [Changes in Post-Layout1](https://github.com/DebjitLP/inv_design#changes-in-post-layout1)
* [Abstract2](https://github.com/DebjitLP/inv_design#abstract2)
* [Schematics_2 in Virtuoso](https://github.com/DebjitLP/inv_design#schematics_2-in-virtuoso)
* [Pre-Layout Simulation Results2](https://github.com/DebjitLP/inv_design/blob/main/README.md#pre-layout-simulation-results2)
* [Layout of the Inverter in Virtuoso (indicating different layers)](https://github.com/DebjitLP/inv_design/blob/main/README.md#layout-of-the-inverter-in-virtuoso-indicating-different-layers-1)
* [Post-layout Simulation Results2](https://github.com/DebjitLP/inv_design/blob/main/README.md#post-layout-simulation-results2)
* [Pre-Layout vs Post-layout Simulations Results2](https://github.com/DebjitLP/inv_design/blob/main/README.md#pre-layout-vs-post-layout-simulations-results2)
* [Changes in Post-Layout2](https://github.com/DebjitLP/inv_design/blob/main/README.md#changes-in-post-layout2)
* [Author](https://github.com/DebjitLP/inv_design/blob/main/README.md#author)
* [Acknowledgements](https://github.com/DebjitLP/inv_design/blob/main/README.md#acknowledgements)



## Tools Used

- Cadence Virtuoso
- Cadence Spectre
- STMicroelectronics 65nm
- Mentor Graphics Eldo
- Ezwave

## Abstract1

Design a minimum-sized inverter such that the following specification is met.
For a load of 20fF, (Rise-delay) = (Fall-delay) < 50ps at SS, 1.08V, 125C


## Schematics_1 in Virtuoso:

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/layout_schem/shchematic1.png?raw=true)

For achieving the equal rise and fall delays here only the width of the PMOS and 
NMOS is varied. Length of the devices are kept constant.
For the Required Specification:
The PMOS W/L is 2.095/0.06. 
The NMOS W/L is 1.005/0.06.


## Pre-Layout Simulation Results1

* **Input and Output Waveform of the Inverter**

The simulations were run for 100ns with Input signal of time period of 10ns (Duty Cycle = 0.5).

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/pre_wave.png?raw=true)



* **Timing Specifications1**

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/dlpt/pre_time1.png?raw=true)



* **Waveforms of Rise and Fall Delay**

Rise Delay
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/pre_rised.png?raw=true)

Fall Delay
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/pre_falld.png?raw=true)



* **Width of NMOS fixed at 1.005 and Width of PMOS swept to Obtain the Sizing:**

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/sweep_size1.png?raw=true)

* **Input and Output Waveform of the Inverter:**

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/pre_wave.png?raw=true)

## Layout of the Inverter in Virtuoso (indicating different layers)

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/layout_schem/lay_1.png?raw=true)


## Post-layout Simulation Results1





* **Timing Specifications1**

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/dlpt/post_time1.png?raw=true)



* **Waveforms of Rise and Fall Delay**

Rise Delay
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/post_rised.png?raw=true)

Fall Delay
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/post_falld.png?raw=true)


## Pre-Layout vs Post-layout Simulations Results1

| Parameters |  Pre-Layout                |  Post-Layout                |
| :-------- |  :------------------------- |   :------------------------- |
| `Wn` |  1.005 um | 1.005 um |
| `Wp ` | 2.095 um |  2.095 um |
| `Temperature ` | 125 C | 125 C |
| `Vdd` |  1.08 V |     1.08 V |
| `Rise Delay (TPLH)` |  45.65 ps |     47.39 ps |
| `Fall Dlay (TPHL)` |  45.66 ps |     47.40 ps |
| `Avg. Delay` |  45.65 ps |    47.39 ps |

## Changes in Post-Layout1

- Due to the introduction of Parasitic Capacitances and Resistances in the Post-Layout in various nodes of the design the Delays increases and thus performance degrades by a small margin.
- Increase in contact resistance, contact to Poly Capacitance and total output capacitance leads to increase in the delay in post layout.

* **What can be done to avoid mismatch in pre-layout and post-layout results:**

- If we are able to model the parasitic capacitance in the pre layout itself, do the sizing based on total load capacitance and modelled parasitic then the mis-match could be avoided to some extent.
- Reducing the number of contacts in the post-layouts would reduce the capacitance of Contact-Poly, thus would help in reducing the delay and mismatch.
- Over qualifying the specifications by a small margin by taking the sizes of the devices a little bit larger would help in reducing the delays and mismatch as well.


## Abstract2

 For a load of 20fF, Rise-time = Fall-time (20%-80% transition thresholds) = 20ps 
(approx) at Slow NMOS-Slow PMOS (SS), 1.08V, 125C


## Schematics_2 in Virtuoso:

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/layout_schem/shchematic2.png?raw=true)

For achieving the equal rise and fall time here only the width of the PMOS and 
NMOS is varied. Length of the devices are kept constant.
For the Required Specification:
The PMOS W/L is 7.875/0.06. 
The NMOS W/L is 3.235/0.06.

## Pre-Layout Simulation Results2

* **Timing Specifications2**

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/dlpt/pre_time2.png?raw=true)

* **Waveforms of Rise and Fall Time**

Rise Time
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/pre_riset.png?raw=true)

Fall Time
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/pre_fallt.png?raw=true)

## Layout of the Inverter in Virtuoso (indicating different layers)

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/layout_schem/lay_2.png?raw=true)


## Post-layout Simulation Results2

* **Timing Specifications2**

![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/dlpt/post_time2.png?raw=true)

* **Waveforms of Rise and Fall Time**

Rise Time
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/post_riset.png?raw=true)

Fall Time
![Reference Circuit Diagram](https://github.com/DebjitLP/inv_design/blob/main/waveforms/post_fallt.png?raw=true)


## Pre-Layout vs Post-layout Simulations Results2

| Parameters |  Pre-Layout                |  Post-Layout                |
| :-------- |  :------------------------- |   :------------------------- |
| `Wn` |  3.235 um | 3.235 um |
| `Wp ` | 7.875 um |  7.875 um |
| `Temperature ` | 125 C | 125 C |
| `Vdd` |  1.08 V |     1.08 V |
| `Rise TIME` |  19.61 ps |     20.44 ps |
| `Fall TIME` |  19.61 ps |     19.58 ps |

## Changes in Post-Layout2

- Due to the introduction of Parasitic Capacitances and Resistances in the Post-Layout in various nodes of the design the Delays increases and thus performance degrades by a small margin.
- Increase in contact resistance, contact to Poly Capacitance and total output capacitance leads to increase in the delay in post layout.

* **What can be done to avoid mismatch in pre-layout and post-layout results:**

- If we are able to model the parasitic capacitance in the pre layout itself, do the sizing based on total load capacitance and modelled parasitic then the mis-match could be avoided to some extent.
- Reducing the number of contacts in the post-layouts would reduce the capacitance of Contact-Poly, thus would help in reducing the delay and mismatch.
- Over qualifying the specifications by a small margin by taking the sizes of the devices a little bit larger would help in reducing the delays and mismatch as well.
- Such larger sizes of PMOS and NMOS should be broken into fingers and output should be taken out from the point of less capacitance. With efficient source, drain sharing the mismatch can be further avoided.


## Author

```bash
Debjit Batabyal , Indraprastha Institute of Information Technoology Delhi
```

## Acknowledgements

 - Indraprastha Institute of Information Technoology Delhi
 - STMicroelectronics

