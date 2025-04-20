# ⚙️ Verilog-A Opamp Model (Ideal, Linear Output) for Cadence Spectre

This repository provides a simple **ideal operational amplifier** (opamp) modeled in Verilog-A for use with **Cadence Virtuoso** and **Spectre** simulator. The model includes open-loop gain and allows rail-to-rail output without limiting or bandwidth shaping.

---

## 🧠 Model Description

This opamp model implements:

- A high open-loop gain (`A0`)
- A differential input: `vinp`, `vinn`
- A single-ended output: `vout`
- Supply pins: `vdd` and `vss` (not internally modeled)
- **No** output voltage limiting
- **No** gain-bandwidth limitation

### Equation:

V(vout) = A0 × (Vin+ - Vin−)


---

## 🧪 How to Use in Cadence Virtuoso

### 1. Add the Verilog-A Model

1. Open **Library Manager**
2. Create or choose a library
3. Go to:  
   **File → New → Cell View**
   - View Name: `veriloga`
   - Tool: `Verilog-A`
4. Paste the content of `veriloga.va`
5. Click `Check and Save`

### 2. Create a Symbol

- In the Verilog-A editor, go to:  
  **Launch → Create Symbol**
- Wire pins in the following order: `vout`, `vinp`, `vinn`, `vdd`, `vss`
- Save the symbol

### 3. Build a Testbench

- Instantiate the opamp symbol in a schematic
- Connect it in a basic configuration (e.g., voltage follower or inverting amp)
- Apply `vpulse`, `vsin`, or `vdc` to the inputs
- Add power supplies for `vdd` and `vss`

![opamp](https://github.com/user-attachments/assets/de77dc08-b573-42de-a917-fa75b053162a)


### 4. Run Simulations in ADE

- Open ADE and select a simulation type (Transient or DC)
- Add output variables (e.g., `V(vout)`)
- Click **Run** to simulate

![opamp_veriloga](https://github.com/user-attachments/assets/cd507ff0-884c-42f8-ba04-72848414b86b)

---

## ⚠️ Limitations

- No rail-to-rail output limiting (`Vhi`, `Vlo` are unused)
- No frequency-dependent behavior (GBW is not implemented)
- Supply pins are symbolic and not modeled in behavior

---

## 📬 Feedback

Feel free to open issues or submit pull requests if you want to extend this model with GBW limitation, output clamping, or realistic offset.

---
