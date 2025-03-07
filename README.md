# Solar PV + Optional Battery Subsystem

This repository contains a **Simscape** subsystem that models a **solar photovoltaic (PV) system** with an **optional battery**. You can either use the subsystem as-is, with the battery included, or remove/bypass the battery components for a *pure* solar PV module. In either configuration, it integrates seamlessly into any larger Simulink/Simscape Electrical model.

---

## Table of Contents

1. [Overview](#overview)  
2. [Key Features](#key-features)  
3. [Block Diagram & Inputs/Outputs](#block-diagram--inputsoutputs)  
4. [Usage Instructions](#usage-instructions)  
5. [Removing the Battery](#removing-the-battery)  
6. [Parameterization & Masking](#parameterization--masking)  
7. [Testing & Validation](#testing--validation)  
8. [License & Disclaimer](#license--disclaimer)  
9. [Contact & Contributing](#contact--contributing)

---

## Overview

- **File**: `solarpvmodel.slx`  
- **Toolboxes Required**:  
  - MATLAB  
  - Simulink  
  - Simscape  
  - Simscape Electrical  

This subsystem is ready to be dragged into any Simulink/Simscape model. It provides a *photovoltaic power source* whose voltage and current respond to changing irradiance and temperature, and optionally charges or discharges a battery if you choose to keep that component inside.

---

## Key Features

1. **Variable Inputs**  
   - Solar irradiance \([W/m^2]\)  
   - Cell/module temperature \([°C]\)  

2. **Built-In or Optional Battery**  
   - A battery model (with user-definable capacity, SOC, etc.) can be used to store or supply energy.  
   - You can remove/bypass the battery for a *pure* PV source.

3. **Outputs**  
   - PV array voltage 
   - PV array current 
   - Battery current  
   - Battery SOC  
   - Output bus voltage

4. **Compatibility**  
   - Connects to other Simscape Electrical components (inverters, loads, controllers) via electrical ports or signal lines (depending on your setup).

---


### Inputs

1. **Irradiance**: \([W/m^2]\) – Time-varying or constant.  
2. **Temperature**: \([°C]\) – Typically cell temperature.  
3. **(Optional) V_pv**: \([V]\) – External control or measurement for the PV array voltage.  
4. **(Optional) I_pv**: \([A]\) – External control or measurement for the PV array current.

### Outputs

1. **V_PV**: \([V]\) – Voltage at the PV terminals.  
2. **I_PV**: \([A]\) – Current delivered by the PV array.  
3. **Current (A)** – Net current from the subsystem output (includes PV + battery).  
4. **SOC (%)** – Battery’s State of Charge (if battery is active).  
5. **Voltage (V)** – Output or bus voltage.

---

## Usage Instructions

1. **Open/Install**  
   - Copy `solarpvmodel.slx` into your working directory or add it to your MATLAB path.

2. **Drag & Drop**  
   - Open your main Simulink model.  
   - Drag the subsystem from the Simulink Library Browser (or from the file) into your model.

3. **Connect Inputs**  
   - Connect **Irradiance** and **Temperature** signals/blocks.  
   - If desired, connect external voltage/current references or measurements for advanced control (e.g., MPPT).

4. **Parameter Setup**  
   - Double-click the subsystem to edit:  
     - **PV model parameters** (panel specs, diode, etc.)  
     - **Battery parameters** (capacity, nominal voltage, initial SOC)

5. **Simulate**  
   - Press “Run.”  
   - Monitor the outputs (V_PV, I_PV, battery SOC, etc.).

---

## Removing the Battery

To use this subsystem strictly as a solar PV module:

1. **Open the Subsystem** (Look Under Mask or open directly).  
2. **Delete/Bypass the Battery Block** so the PV output directly feeds your external circuit.  
3. **Reconnect or remove** any converter/load logic as needed.  
4. **Save** the modified version if you want to keep both variants.

---

## Parameterization & Masking

If desired, create a **mask** to expose all key parameters in a single dialog box. Common parameters include:

- **PV**: Nominal power, open-circuit voltage, short-circuit current, series/shunt resistance, etc.  
- **Battery**: Rated capacity (Ah or Wh), nominal voltage, internal resistance, initial SOC.

---

## Testing & Validation

1. **Constant Irradiance**  
   - Compare the simulated \(V_{\mathrm{PV}}, I_{\mathrm{PV}}\) to the PV datasheet values at STC (1000 W/m², 25 °C).

2. **Dynamic Irradiance**  
   - Feed time-varying or step changes in irradiance; observe how the model responds.

3. **Battery SOC**  
   - If the battery is present, verify correct charging/discharging under different load or PV power conditions.

4. **Integration**  
   - Connect the subsystem to an MPPT controller or power converter in a larger Simulink model. Confirm stable operation.

---

## License & Disclaimer

- **License**: (MIT)
- **Disclaimer**: This model is provided “as is” without warranty. Verify results with actual datasheet data or empirical measurements before critical deployments.

---

## Contact & Contributing

- **Contact**: For questions or issues, please reach out via your chosen support channel (https://www.linkedin.com/in/tanveer-hussain-277119196/).  
- **Contributions**: Pull requests for improvements—such as advanced battery chemistry or improved PV equations—are welcome.

---

**Enjoy simulating your Solar PV system!**



## Upwork Job Requirements
Simscape Library
Can you create  a  solar  pv  model  for  simscape  electrical   library?  I  want  to  have  a  solar  pv  model  with  input  parameters  variable  which  
I  can  decide  and  add  that  model  to  an  existing  simscape  library  where  other  components  are  present  and  it  should  be  compatible.

