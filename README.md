# oscillatory-stdp-experiments
Simulations of Phase-Dependent Plasticity and Attractor Dynamics in Spiking Neural Networks.
# Phase-Dependent Three-Factor Plasticity & Attractor Dynamics
**Investigating the role of Neural Oscillations in Gated Synaptic Learning and Working Memory.**

## 🔬 Overview
This repository contains two computational neuroscience experiments implementing biologically plausible learning and memory mechanisms in Spiking Neural Networks (SNNs). The simulations explore how temporal dynamics—specifically **Theta oscillations** and **Recurrent loops**—enable complex cognitive functions like signal filtering and working memory.

**Author:** Frederick (Fred) Hayes
**Status:** Complete (Feb 2026)

---

## 📂 Repository Structure

### 1. `resonance_learning.ipynb` (Long-Term Plasticity)
**Hypothesis:** Neural oscillations (Theta waves) act as a "Gating Mechanism" for synaptic plasticity, allowing the brain to filter signal from noise based on phase alignment.

**The Model:**
We implement a **Three-Factor Learning Rule** for Leaky Integrate-and-Fire (LIF) neurons:
$$\Delta W = \eta \cdot \text{Trace}(t) \cdot \text{Dopamine}(t) \cdot \max(0, \sin(\omega t))$$

**Key Results:**
* **The Cocktail Party Effect:** The network successfully differentiated between two competing input streams of equal density.
    * **Signal (Phase-Locked):** Weights grew to **60.00**.
    * **Noise (Anti-Phase):** Weights suppressed to **28.53**.
    * **Result:** A **2.1x Signal-to-Noise Ratio** was achieved solely through temporal gating.
* **Resonance Tuning:** A frequency sweep demonstrated **Band-Pass Filter** behavior, where learning only occurred when the internal oscillation matched the input frequency (0.003–0.005 Hz).
* **Biological Realism:** The system exhibited a **~127° Phase Lag**, accurately reflecting biological integration latencies.

### 2. `working_memory.ipynb` (Short-Term Memory)
**Hypothesis:** Transient sensory stimuli can be maintained "online" through self-sustaining reverberation (Attractor Dynamics) in Recurrent SNNs.

**The Model:**
A population of LIF neurons with strong local recurrent excitation ($W_{rec} \gg 1.0$) and global inhibition.

**Key Results:**
* **Stable Attractor:** The network maintained a **1000 Hz** activity burst during a 400ms delay period after the stimulus was removed.
* **Robustness:** The memory trace showed **zero decay** over time.
* **Controllability:** A "Wipe" signal (Inhibitory Pulse) successfully silenced the attractor, demonstrating that the system is stable and controllable, not seizure-prone.

---

## 🛠 Usage
These simulations are self-contained Jupyter Notebooks.

1.  Clone the repository:
    ```bash
    git clone [https://github.com/fehayes/oscillatory-stdp-experiments.git](https://github.com/fehayes/oscillatory-stdp-experiments.git)
    ```
2.  Install dependencies:
    ```bash
    pip install numpy matplotlib pandas
    ```
3.  Run the notebooks:
    * Open `resonance_learning.ipynb` for the STDP experiments.
    * Open `working_memory.ipynb` for the Working Memory experiments.
