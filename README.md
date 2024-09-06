**Fire Alert System Using AT89C51 and LCD**

This project is a fire alert system based on the **AT89C51 microcontroller**, a **buzzer**, an **LCD**, and a **switch** used to simulate fire detection. When the switch is pressed, the system triggers the buzzer and displays a "FIRE DETECTED" message on the LCD screen.
![trest](https://github.com/user-attachments/assets/00e257d6-651b-47c2-b0fe-068ea5ba0248)

**Table of Contents**

- [Introduction](#introduction)
- [Components Used](#components-used)
- [Circuit Diagram](#circuit-diagram)
- [Pin Configuration and Connections](#pin-configuration-and-connections)
- [Code Explanation](#code-explanation)
- [Working](#working)
- [Proteus Simulation](#proteus-simulation)
- [How to Run](#how-to-run)
- [License](#license)

**Introduction**

The fire alert system is designed to simulate fire detection using a **switch**. When the switch is pressed, the system displays "FIRE DETECTED" on the **LCD** and sounds an alarm via a **buzzer**. The microcontroller used in this project is the **AT89C51**, a popular 8051 family microcontroller.

**Components Used**

1. **AT89C51 Microcontroller**
2. **16x2 LCD** (Liquid Crystal Display)
3. **Buzzer**
4. **Push Button** (for simulating fire detection)


**Circuit Diagram**

**Pin Configuration and Connections**

**AT89C51 Microcontroller:**
![8051 TREST](https://github.com/user-attachments/assets/0a559c24-2650-460d-b43a-68887505ff88)


| **Pin No.** | **Pin Name** | **Function** | **Connection** |
| --- | --- | --- | --- |
| 1   | P1.0 | General Purpose I/O Pin | Connected to the Switch (for fire detection) |
| 2   | P1.1 | General Purpose I/O Pin | Connected to RS pin of the LCD |
| 3   | P1.2 | General Purpose I/O Pin | Connected to RW pin of the LCD |
| 4   | P1.3 | General Purpose I/O Pin | Connected to EN pin of the LCD |
| 21-28 | P2.0-P2.7 | General Purpose I/O Pins | Connected to D0-D7 of the LCD |
| 10  | P3.0 | General Purpose I/O Pin | Connected to the Buzzer |
| 18, 19 | XTAL1, XTAL2 | Clock Oscillator Pins | Connected to 11.0592 MHz Crystal Oscillator |
| 9   | RST | Reset Pin | Connected to reset circuit (capacitor & resistor) |

**LCD (16x2):**

| **Pin No.** | **Pin Name** | **Function** | **Connection** |
| --- | --- | --- | --- |
| 1   | VSS | Ground | Connected to Ground |
| 2   | VDD | Power Supply | Connected to +5V |
| 3   | VEE | Contrast Control | Connected to Potentiometer |
| 4   | RS  | Register Select | Connected to P1.1 of the AT89C51 |
| 5   | RW  | Read/Write | Connected to P1.2 of the AT89C51 |
| 6   | EN  | Enable | Connected to P1.3 of the AT89C51 |
| 7-14 | D0-D7 | Data Pins | Connected to P2.0-P2.7 of AT89C51 |

**Buzzer:**

| **Pin No.** | **Function** | **Connection** |
| --- | --- | --- |
| 1   | Positive (+) | Connected to P3.0 |
| 2   | Negative (-) | Connected to Ground |

**Switch:**

| **Pin No.** | **Function** | **Connection** |
| --- | --- | --- |
| 1   | Input (for fire detection) | Connected to P1.0 |
| 2   | Ground | Connected to Ground |

**Code Explanation**

The microcontroller continuously monitors the **switch** connected to pin **P1.0**. When the switch is pressed (indicating fire detection), the microcontroller:

- Displays "FIRE OCCURED" on the **LCD**.
- Activates the **buzzer** connected to **P3.0**.

When the switch is not pressed, it displays "FIRE ALERT SYSTEM" and turns off the buzzer.

**Key Code Components:**

- **lcdinit()**: Initializes the LCD in 8-bit mode, 2-line display.
- **lcddis()**: Displays a string of characters on the LCD.
- **lcdcmd()**: Sends command instructions to the LCD.
- **lcddat()**: Sends data (characters) to the LCD.


```c
void lcdinit() {
    lcdcmd(0x38);  // Initialize LCD in 8-bit mode, 2-line display
    lcdcmd(0x01);  // Clear display
    lcdcmd(0x0C);  // Display ON, cursor OFF
    lcdcmd(0x80);  // Move cursor to beginning
}
```
**Working**

1. **Normal Condition**:
    - The LCD displays "FIRE ALERT SYSTEM" and the buzzer remains off.
2. **Fire occured**:
    - If the switch is pressed (indicating fire detection), the LCD displays "FIRE OCCURED" and the buzzer turns on.
3. **Reset**:
    - The microcontroller will continuously monitor the switch and update the display/buzzer accordingly.

**Proteus Simulation**

You can simulate the circuit using Proteus. Ensure that you have connected the LCD, microcontroller, switch, and buzzer correctly as described above. After running the simulation, the display should show "FIRE ALERT SYSTEM" initially, and if you press the switch to simulate fire detection, it should display "FIRE DETECTED" and activate the buzzer.

**How to Run**

1. **Proteus Simulation**:
    - Use the attached Proteus circuit diagram to simulate the fire alert system.
    - Ensure all components are connected properly.
    - Load the compiled .hex file into the AT89C51 in Proteus and run the simulation.

**License**

This project is open-source under the MIT License.
