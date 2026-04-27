\# MOSFET (NMOS \& PMOS) Characteristics using LTspice



\## 📌 Objective



To analyze and compare the electrical characteristics of NMOS and PMOS transistors using LTspice simulation.



\---



\## 🧠 Theory



MOSFET operates in three regions:



\* Cutoff Region



\* Triode (Linear) Region



\* Saturation Region



\* NMOS turns ON when \*\*Vgs > Vth\*\*



\* PMOS turns ON when \*\*Vgs < Vth (negative)\*\*



\---



\## ⚙️ Simulation Setup



\### 🔹 NMOS



\* DC Sweep: Vgs from 0 → VDD

\* Vds fixed at 1V



\### 🔹 PMOS



\* DC Sweep: Vgs from 0 → -VDD

\* Vds fixed



\---



\## 📊 Results



\### NMOS Characteristics



\* Id vs Vgs

\* Id vs Vds



\### PMOS Characteristics



\* Id vs Vgs

\* Id vs Vds



\---



\## 📐 Key Measurements



\### Threshold Voltage (Vth)



Extracted using constant current method:

.meas Vth\_NMOS FIND V(Vgs) WHEN I(M1)=1u



\### Transconductance (gm)



.meas gm\_NMOS DERIV I(M1)



\---



\## 🔍 Observations



\* NMOS has higher current due to higher electron mobility

\* PMOS requires larger width (W) for symmetry

\* Saturation region begins when Vds ≥ (Vgs - Vth)



\---



\## 📁 Project Structure



\* models/ → Device models

\* NMOS/ → NMOS simulations

\* PMOS/ → PMOS simulations

\* results/ → Output plots



\---



\## 🚀 Tools Used



\* LTspice

\* PTM / BSIM models



\---



\## 👨‍💻 Author



Md. Masudun Nabi Siam

EEE, BSMRSTU

Aspiring VLSI Engineer



