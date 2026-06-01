# MOSFET Characterization & Analog Verification Suite

An automated analog IC verification suite using LTspice to analyze 180nm MOSFET characteristics across Process, Voltage, and Temperature (PVT) corners and statistical Monte Carlo variations.

## 🚀 Features & Verification Coverage
* **DC Characterization:** Extracts $I_D$ vs $V_{DS}$ (Drain) and $I_D$ vs $V_{GS}$ (Transfer) curves.
* **PVT Corner Analysis:** Validates device degradation across standard process corners (TT, FF, SS) paired with temperature (-40°C to 125°C) and voltage supply drops ($\pm$10%).
* **Monte Carlo Mismatch:** Evaluates local threshold voltage ($V_{th}$) and physical geometric variations over 100+ statistical runs.

## 📁 Repository Structure
* `/testbenches` : Houses all the primary `.asc` schematic files.
* `/models` : Contains the open-source 180nm SPICE card parameter files used for simulation.

## 🛠️ How to Run the Simulations
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com
   ```
2. Open **LTspice**.
3. Navigate to `testbenches/pvt_corners/` and open the desired `.asc` file.
4. Click the **Run** button (Running Man icon).
5. Right-click on the schematic graph to trace target signals like `I(M1)`.

## 📊 Verification Results (Examples)
### 1. PVT Corner Sweep
*Place an image or brief explanation here showing your current drop at the SS, high-temp corner.*

### 2. Monte Carlo Distribution
*Place an image here showing the Gaussian histogram of your threshold variation or current mismatch.*

## 📚 Academic & Industrial References
This verification framework is designed based on industry-standard methodologies outlined in:

* **Baker, R. Jacob.** *CMOS: Circuit Design, Layout, and Simulation, Fourth Edition*, Wiley-IEEE Press, 2019.
  * **Chapter 5 & 6:** Applied for establishing the base SPICE parameters and generating the $I_D$ characterization curves.
  * **Chapter 6 (Process Variations):** Referenced to map out the Fast/Slow (FS) transistor corner matrix and handle environmental PVT boundaries.
  * **Analog Chapters (Mismatch Analysis):** Utilized to construct the statistical tolerance metrics evaluated in the Monte Carlo suite.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
