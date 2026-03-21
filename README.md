# ⚙️ 4-Speed Modular Dual-Clutch Transmission (DCT)

![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen) ![Platform: 3D Printed](https://img.shields.io/badge/Platform-3D_Printed-blue) ![License: MIT](https://img.shields.io/badge/License-MIT-orange)

> <img width="1323" height="964" alt="full assembly image 3" src="https://github.com/user-attachments/assets/c9c0feb5-8154-47f2-b94f-4c615809c1ff" />
> <img width="887" height="633" alt="image" src="https://github.com/user-attachments/assets/9a6f8eae-ad6b-4374-9d6d-27ff35138c11" />



## 📖 Description & Background
This repository contains the CAD files and assembly documentation for a **fully modular, 3D-printable 4-speed Dual-Clutch Transmission (DCT)**. It is powered by a 6V DC motor and designed to demonstrate high-efficiency kinetic energy transfer without the need for complex friction plates.

### 🚗 The Engineering: DCT vs. Manual Transmission
A traditional manual transmission interrupts power flow during a shift (the "neutral" gap). A Dual-Clutch Transmission solves this by splitting the gears across two independent shafts:
* **The Pros:** Near-seamless torque delivery, faster shift times, and higher mechanical efficiency since the "next" gear is pre-selected while the current one is driving.
* **The Cons:** Higher mechanical complexity, increased weight, and in real-world applications, complex thermal and fluid management. 

This model recreates that continuous power flow using a unique mechanical linkage, making the complex logic of a DCT visible and accessible.

---

## 🌟 Key Features & Innovations

### 1. The "Linked-Shift" Mechanical Logic
Real DCTs use electronic actuators (TCUs) to independently engage clutches. To make this model accessible and purely mechanical, we implemented a **slider-rod linkage system**. 
When you manually shift one set of gears, the connecting rod automatically pushes the slider on the opposite shaft into the "pre-selected" engagement position. This perfectly simulates the electronic hand-off of an actual DCT without needing a single line of code.

><img width="828" height="628" alt="image" src="https://github.com/user-attachments/assets/6f6aa915-af71-445e-9fdf-9e2cc0da81f2" />


### 2. 100% Modular "Zero-Rigid-Fix" Design
The entire assembly follows a zero-rigid-fix philosophy:
* **No permanent adhesives:** Every gear, shaft, and bearing can be disassembled.
* **Tolerances:** Parts are engineered with optimized tolerances for 3D printing, ensuring a snug fit for bearings and minimized backlash between gear meshes. 

---

## 📐 Mechanical Architecture

### ⚙️ Gear Ratios Matrix
The transmission features four distinct speeds, alternating between the independent Odd and Even shafts:

| Gear | Ratio | Tooth Count (Drive:Driven) | Active Shaft |
| :--- | :--- | :--- | :--- |
| **1st** | 1:2.5 | 10T : 25T | Odd |
| **2nd** | 1:1.33 | 15T : 20T | Even |
| **3rd** | 1.33:1 | 20T : 15T | Odd |
| **4th** | 2.5:1 | 25T : 10T | Even |

### 🔩 Helical Gears vs. Spur Gears
To mimic high-performance automotive transmissions, this model utilizes **Helical Gears**.
* **Why Helical?** They offer smoother, progressive tooth engagement, operate much quieter than spur gears, and have a higher load-carrying capacity.
* **The Engineering Challenge:** Helical gears generate **axial thrust** (forces pushing the gear sideways along the shaft). 
* **Our Implementation:** We currently utilize circlips to lock the gears against this axial load as this small setup for demosntration of the mechanism has no load on the output shaft and the gears are small and 3D printed models. However, because circlips are not a solid, long-term solution for continuous thrust and loaded big useful models, upgrading to **shaft collars with thrust bearings** is recommended for higher loads.

### 🔺 Triangular Shaft Layout
Rather than a traditional straight-line sequential layout, this model uses a **Triangular Shaft Arrangement**. 
* **The Benefit:** It creates a much more compact gearbox. 
* **Load Distribution:** Torque is shared and distributed more evenly across the shafts. Bearings carry multi-directional loads, which reduces the bending moments on a single plane compared to a straight-line setup.

> <img width="674" height="477" alt="image" src="https://github.com/user-attachments/assets/61aeef88-ec20-4e41-89cb-3cf088451221" />


---

## 📦 Bill of Materials (BOM)

All housing, gears, and shafts are fully 3D printable. The following hardware components are sourced from the market to complete the build:

| Item | Qty | Specification & Source Link | Use Case |
| :--- | :---: | :--- | :--- |
| **Miniature Ball Bearings** | 15 | [6800-ZZ (10x19x5mm)](https://omrook.com/6800-zz-id-10mm-od-19mm-h-5mm-miniature-ball-bearing/?srsltid=AfmBOooN28es7BWXCtrsCIt4WeAYt7OW58Kqg4sm4qBmBNrfNRqw3Lf4) | Main shaft rotation |
| **DC Geared Motor** | 1 | [6V Arduino Geared Motor](https://www.amazon.in/INVENTO-1pcs-6V-Geared-Arduino/dp/B07R5FPR4D) *(or [Yellow Metal Variant](https://www.amazon.in/Geared-Motor-Original-Metal-Yellow/dp/B0B9KBJWW8))* | Main power drive |
| **E-Type Circlips** | 40 | [10mm Mild Steel (Black Coated)](https://onlyscrews.in/products/10mm-e-type-circlip-mild-steel-black-coated) | Internal gear locking |
| **External Circlips** | 10 | [10mm Shaft Diameter](https://omrook.com/external-circlip-for-10mm-shaft-diameter-100pcs/) | Shaft securing |
| **Thrust Bearings** | 10 | [AXK-1024 Needle Roller (10x24mm)](https://omrook.com/axk-1024-thrust-needle-roller-bearing-id-10mm-od-24mm/) | Axial load management |
| **Shaft Coupling** | 1 | [10mm x 6mm Aluminum Flexible](https://www.flyrobo.in/10mm-x-6mm-aluminum-flexible-shaft-coupling) | Motor-to-shaft connect |
| **Power Source** | 1 | [Lithium-ion Rechargeable Battery](https://www.amazon.in/Electronics-Lithium-ion-Rechargeable-Blutooth-Speakers/dp/B0G63YDBLR/) | Motor power |

*(Note: Standard M3/M4 machine screws are also required for mounting the motor and external housing).*

---

## 🛠️ Installation & Assembly Setup
1. **Print Tolerances:** Ensure your printer is well-calibrated. The gears require minimal stringing to prevent backlash.
2. **Post-Processing:** Sand the 3D-printed shafts lightly if the 6800-ZZ bearings do not slide on smoothly. **Do not force them**, as this breaks the zero-rigid-fix modularity.
3. **Linkage Alignment:** When installing the slider clutches, ensure the connecting rod is perfectly horizontal so shifting from 1st (Odd) smoothly engages 2nd (Even).

---

## 🚀 Roadmap & Future Upgrades
- [ ] **Thrust Upgrade:** Replace all load-bearing circlips with solid shaft collars to fully support the thrust bearings against the helical gear axial loads.
- [ ] **Electronic Actuation:** Design a mount for a servo motor to push the linkage rod, allowing for automated shifting via an Arduino.

## 🤝 Contributing
Suggestions and improvements are welcome! If you have ideas for better bearing mounts or modified gear ratios, please open an issue.
