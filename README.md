# plc-motor-control-simulation
Small collection of PLC logic examples and Python scripts created during my Mechatronics &amp; Automation diploma
# PLC Motor Control Logic – Siemens S7-1200 (Simulation)

This repository contains a simple PLC control logic example created as part of my Mechatronics & Automation diploma at Kingston College. The project demonstrates core PLC concepts, including:

- Start/Stop motor control using ladder logic  
- Emergency stop behaviour  
- Basic I/O mapping  
- Logic testing workflow  
- Understanding of PLC scan cycles

Tools used:
- Siemens TIA Portal
- S7-1200 simulator

This project reflects my early hands-on experience with PLC programming and industrial automation.
# I/O List – Simple Start/Stop Motor Control

**Digital Inputs**
- I0.0 – Start pushbutton (NO)
- I0.1 – Stop pushbutton (NC)
- I0.2 – Emergency stop (NC)

**Digital Outputs**
- Q0.0 – Motor contactor coil / Lamp
- Q0.1 – Status indicator (On when motor is running)
# Ladder Logic Description

**Network 1 – Motor Latching Circuit**

|--[ I0.0 Start ]----+----[ Q0.0 Motor ]----( Q0.0 Motor ) 
                     |
                     +----[ I0.2 E-Stop ]

- Pressing **Start (I0.0)** energises **Q0.0**, which then seals itself in through its own contact.
- **Stop (I0.1)** and **Emergency Stop (I0.2)** are wired in series in the real circuit and open the path when pressed.
- When Q0.0 is ON, the motor or lamp remains energised until Stop or E-Stop is pressed.

**Network 2 – Status Indicator**

|--[ Q0.0 Motor ]-----------------( Q0.1 Status Lamp )

- When the motor coil is energized, a status lamp is turned ON.
