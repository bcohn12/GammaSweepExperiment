Block Diagram for R01 Project
=============================


```sequence
participant NeuralFPGA
participant LoadCell
participant DAQ
participant CPU
participant FPGA
participant ANADIGI
participant Driver
participant Motor
participant Timing
participant Encoder



participant String

Note left of FPGA: Force Feedback Loop (PID Control)
Encoder-->CPU: Encoded Length Pulses (Rotational Angle or RPM)
CPU-->NeuralFPGA: Digital Length and Velocity Values
Note over NeuralFPGA: Small delay
NeuralFPGA-->CPU: Digital Voltage (Desired Force)
LoadCell-->DAQ: Analog Voltage (Current Force)
Note over DAQ: Small delay
Title: Sets of steps which occur simultaneously are painted as dotted lines
CPU-->FPGA: Digital Voltage (Desired Force)
DAQ-->FPGA: Digital Voltage (Current Force)
FPGA->ANADIGI: Digital Voltage (Correction Command)
ANADIGI->Driver: Analog Voltage (Correction Command)
Driver->Motor: High Current Drive (Correction Command)
Motor-->String: Torque applied
String-->LoadCell: Linear force applied

```

