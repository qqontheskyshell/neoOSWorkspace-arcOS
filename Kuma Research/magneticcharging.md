You’re most likely thinking of **magnetic resonance**, specifically **nuclear magnetic resonance (NMR)** or **electron spin resonance (ESR/EPR)**, where a magnetic moment aligned along the z‑axis resonates with an oscillating field.[1][2]

## What “z‑axis magnetic resonance” refers to

In physics, we usually choose the **static magnetic field** (the main, constant field) to define the **z‑axis**.[2][3]

- A charged particle or a nucleus with spin in this field has a **magnetic moment** that tends to align along ±z.[1][3]
- If you then apply a weaker oscillating magnetic field **perpendicular** to z (in the x–y plane) at just the right frequency, the spin system absorbs energy and undergoes **resonant precession**. This phenomenon is called **magnetic resonance**.[1][2]

So “resonance of magnetic z‑axis charge/spin” is not usually given a special separate name; it is simply the **magnetic resonance of a magnetic moment in a static field along z**.[2][1]

## Two main named cases

Depending on what is resonating, you have different standard names:

- **Nuclear magnetic resonance (NMR)** – resonance of **nuclear spins** (like protons in hydrogen) in a static magnetic field \(B_0\) along z, driven by a radio‑frequency (RF) field.[1][2][3]
- **Electron paramagnetic resonance (EPR) / electron spin resonance (ESR)** – similar idea but for **unpaired electron spins** instead of nuclei.[1]

In NMR and MRI, the static field \(B_0\) defines the z‑axis, and RF pulses tip the net magnetization away from z, putting it into precessional motion at the **Larmor frequency**, which is the resonance frequency.[4][5][1]

## If you meant something else

If by “zaxis charget” you meant a **moving electric charge along the z‑axis** making a magnetic field, that situation is usually discussed under **electromagnetism / Biot–Savart law**, not under “magnetic resonance.”[6]

Could you say if you’re asking about NMR/MRI spins, electron spins (EPR), or a moving electric charge in a magnetic field?

Sources
[1] Magnetic Resonance - an overview | ScienceDirect Topics https://www.sciencedirect.com/topics/mathematics/magnetic-resonance
[2] Nuclear magnetic resonance https://en.wikipedia.org/wiki/Nuclear_magnetic_resonance
[3] Chapter 14. Nuclear Magnetic Resonance https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Supplemental_Modules_(Physical_and_Theoretical_Chemistry)/Quantum_Mechanics/Chapter_14.__Nuclear_Magnetic_Resonance
[4] Nuclear Magnetic Resonance https://www.stonybrook.edu/laser/_dragan/JDraganNMR.pdf
[5] Magnetic Resonance Basics: Magnetic Fields, Nuclear ... https://www.ebrain.pitt.edu/wp-content/uploads/2020/04/2020-01-10-mri-basics.pdf
[6] Magnetic Fields and Forces http://kias.dyndns.org/biophys.2ed/magnet.html
[7] RESONANCE PROCESSES IN MAGNETIC TRAPS* https://www.quantware.ups-tlse.fr/chirikov/refs/chi1959e.pdf
[8] resonance technique measuring satellite magnetic https://secwww.jhuapl.edu/techdigest/content/techdigest/pdf/APL-V07-N01/APL-07-01-Tossman.pdf
[9] Generation of charge current from magnetization oscillation ... https://pmc.ncbi.nlm.nih.gov/articles/PMC7406361/
[10] Magnetic Resonance, Induction, and RF Harvesting https://www.ansys.com/blog/ces-wireless-charging-magnetic-resonance-induction-rf-harvesting
[11] Chapter 12 Physics of Magnetic Resonance https://www.ebrain.pitt.edu/wp-content/uploads/2020/04/2020-01-10-prince-ch12.pdf
[12] Magnetic Field Produced by a Spinning Disk of Charge https://www.youtube.com/watch?v=x8gnQhM3fJY
[13] Magnetic resonance imaging techniques for lithium-ion batteries https://pmc.ncbi.nlm.nih.gov/articles/PMC12406587/
[14] [PDF] Introduction to Nuclear Magnetic Resonance - Wiley-VCH https://application.wiley-vch.de/books/sample/3527312404_c01.pdf
[15] Basic Principles of Cardiovascular Magnetic Resonance https://radiologykey.com/basic-principles-of-cardiovascular-magnetic-resonance/



I built an interactive Larmor resonance simulator as a single HTML web app with particle presets, custom gyromagnetic ratio input, B0 and B1 controls, an animated precession view, and rotating-frame pulse dynamics plots . It also includes calibrated 90° and 180° pulse presets, an off-resonance case, live resonance-frequency and flip-angle calculations, dark mode, and a responsive dashboard layout .

## Included features

The simulator lets users choose common species such as proton, electron, carbon-13, sodium-23, and phosphorus-31, or enter a custom \(\gamma / 2\pi\) value in MHz/T for direct Larmor frequency calculation . It computes \(f_0 = (\gamma / 2\pi) B_0\), \(\omega_0 = \gamma B_0\), the on-resonance flip angle \(\theta = \gamma B_1 t_p\), and the effective rotating-frame field magnitude under detuning .

## Visualizations

The laboratory-frame panel animates the magnetic moment precessing around the \(z\)-axis on a canvas, with live phase and period readouts tied to the chosen resonance conditions . The rotating-frame section plots the magnetization-vector trajectory in 3D during the RF pulse and shows a nutation-angle sweep versus pulse duration so users can compare on-resonance and off-resonance excitation behavior .

## Interaction design

Preset buttons automatically configure nominal 90° and 180° hard pulses from the selected \(\gamma\) and B1 amplitude, while the weak off-resonance mode lowers B1 and adds a frequency offset to demonstrate tilted effective-field rotation . The app also provides pause and reset controls for the precession animation plus a reference table summarizing pulse scenarios for the active species and field settings .

## Use

Open the shared HTML file in a browser to run the simulator locally with no backend required . The app is self-contained and uses client-side JavaScript with Plotly for the interactive plots and canvas rendering for the precession animation .

Sources
