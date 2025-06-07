#  Buck-Boost Converter.

## 1. Introduction

A **buck-boost converter** is a type of DC-DC converter that can either step up (boost) or step down (buck) a given input voltage, depending on the system's requirements. Unlike a simple **linear voltage regulator** (like 7805), which just dissipates excess voltage as heat, a buck-boost converter **stores and transfers energy using inductors and switches** to maintain a stable voltage — with **much higher efficiency**.

### How Is It Different from a Normal Voltage Regulator?

| Feature                      | Linear Voltage Regulator        | Buck-Boost Converter                  |
|-----------------------------|----------------------------------|---------------------------------------|
| Efficiency                  | Low (drops excess voltage as heat) | High (80–95% typical)               |
| Output Voltage Range        | Only lower than input            | Can be higher, lower, or equal to input |
| Main Components             | Regulator IC, capacitors, resistor | Inductor, capacitor, diode/switch, PWM controller |
| Heat Dissipation            | High                             | Low                                    |
| Suitable for battery use?   | Not ideal                        | Perfect for varying battery voltages  |

### Example:
- If you use a **12V battery** to power a **5V circuit**, a **linear regulator like 7805** will drop 7V across itself and waste it as heat. A **buck converter** will step it down efficiently using switching action.
- If the battery drops below 5V (say 3.7V), a **boost converter** would be required.
- Instead of switching between buck and boost manually, a **buck-boost converter** handles it automatically.

---

## 2. Basic Block Diagram & Circuit Comparison

### Linear Regulator Example:

![Linear Voltage Regulator](https://www.circuitbasics.com/wp-content/uploads/2020/07/regulator6-1.png)
<br> </br>

### Buck Boost converters
<div align="center">
  <img src="https://github.com/user-attachments/assets/bbbce4d0-08c7-42c3-a171-269a84da55c3" alt="buck boost converters" />
</div>


- The **inductor** stores and releases energy depending on the switching control.
- A **timing controller (PWM or IC)** determines how long to turn the switch on/off.
- The **capacitor** smooths the output voltage.

---

## 3. Why Use a Buck-Boost Converter?

- ✅ Can operate even when input is **below or above** the desired output.
- ✅ **High efficiency** (80–95%) – less heat, longer battery life.
- ✅ Supports wide input ranges — ideal for battery-powered systems.
- ✅ No need to switch between buck and boost manually.

---

## 4. Working of a Buck-Boost Converter

The working is based on two phases — **charging and discharging the inductor**:

1. **Switch ON** (Transistor closed):  
   - Current flows from Vin → inductor → ground.  
   - Energy is stored in the inductor's magnetic field.

2. **Switch OFF** (Transistor open):  
   - Inductor reverses polarity and pushes energy to the output capacitor and load.
   - Diode ensures current flows in correct direction.

This process is repeated many times per second (~100kHz to 1MHz) using a **PWM control circuit**.

### Good Videos for Visual Understanding:
- [Buck-Boost Converter Working Animation](https://youtu.be/PgTR7226sHU?si=k1gsW_XjhkRGvlHq)
- [Practical Buck Converter Explanation](https://youtu.be/IyiCHMHE5Qg?si=YHHveMQKFkdFUsB2)
- [Boost Converter Explained Simply](https://youtu.be/rfChSvb8FX0?si=FDPxVHZtR7t_r60C)

---

## 5. Buck Converter – Basic Circuit and Explanation

A **buck converter** is used to step down voltage (e.g., 12V to 5V). It works by rapidly switching a transistor on and off and smoothing the output using an LC filter.

### Basic Circuit:

- When the switch is ON, current builds in the inductor.
- When OFF, inductor continues current flow through diode to output.

---

## 6. Boost Converter – Basic Circuit and Explanation

A **boost converter** is used to step up voltage (e.g., 3.3V to 5V). It also relies on the inductor’s energy storage.



- Switch ON: inductor stores energy.
- Switch OFF: inductor pushes energy through diode to the output.

---


## 2. About the TPS63070 IC

The TPS63070 is a high-efficiency buck-boost converter IC from Texas Instruments. It is designed to provide a regulated output from an input that may be higher or lower than the output. It integrates power switches and uses a synchronous switching topology.

**Key Features:**
- Input voltage range: 2V to 16V
- Output current: Up to 2A
- High efficiency: Up to 96%
- Adjustable output voltage
- Internal soft start and power-save mode

## 3. Why I Replicated SparkFun's Module

To learn and understand how real-world power circuits are designed, I replicated the SparkFun Buck-Boost Converter module that uses the TPS63070. This was also my **first fully SMD PCB design** done in **Altium Designer**. Replicating this helped me understand layout practices, SMD footprint management, and how real-life buck-boost designs work.

## 4. My Design Highlights

- Schematic and PCB layout done in **Altium Designer**
- Used similar components to the SparkFun board
- Focused on replicating routing, capacitor placements, and inductor layout
- Learned component selection, DRC rules, and layout planning
- Practiced exporting Gerbers and 3D visualization

## 5. Buck, Boost & Buck-Boost Theory (Simulated in LTspice)

To support my learning, I also designed and simulated:
- A basic **Buck Converter** to step down 12V to 5V
- A **Boost Converter** to step up 3.3V to 5V
- A **Buck-Boost Converter** to maintain 5V from varying input

These simulations were done in **LTspice** and helped visualize:
- Switching waveforms
- Inductor current
- Voltage ripple
- Efficiency trade-offs

## 6. Components Used

| Component          | Value / Part No.     | Description                     |
|-------------------|----------------------|---------------------------------|
| IC                | TPS63070             | Buck-Boost Regulator IC         |
| Inductor          | 2.2µH                | Power inductor for switching    |
| Input Capacitor   | 10µF (x2)            | Decoupling and noise reduction  |
| Output Capacitor  | 22µF (x2)            | Output voltage stabilization    |
| Resistors         | Various              | For feedback and configuration  |
| Diode             | N/A                  | (Internal to IC)                |

## 7. Schematic & PCB Screenshots

_Schematic and PCB layout screenshots will be added here soon._

## 8. Design Files

- [Schematic and PCB (Altium Designer)](./altium_project/)
- [Gerber Files](./gerbers/)
- [BOM File](./BOM.csv)
- [LTspice Simulations](./ltspice_sims/)

## 9. Learnings and Next Steps

This project taught me a lot about real-world PCB design, switching regulator theory, and how to manage a full SMD workflow in Altium. My next step is to design my **own buck converter** circuit from scratch and test it in hardware.

## 10. How to Use / Build This

- **Input Voltage:** 3.3V to 12V
- **Output Voltage:** Settable (default: 5V)
- **Max Output Current:** 2A (depends on cooling & layout)

**Assembly Tip:** Since this is an SMD-only design, hot air soldering or a reflow oven is recommended for best results.

---

### 📌 Note:
This project is for educational purposes and was inspired by SparkFun’s open hardware approach. The goal was to learn by doing and understand the inner workings of a reliable buck-boost converter.

---

### 📷 Project Images & GitHub Page Coming Soon!



