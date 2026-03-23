# Phase-Dependent Plasticity, Attractor Dynamics & Embodied AI
**Investigating Neural Oscillations, Working Memory, and Dual-Process Cognitive Architectures.**

## 🔬 Overview
This repository contains five computational neuroscience experiments implementing biologically plausible learning, memory, stability, and behavioral mechanisms. The simulations explore how temporal dynamics (Theta oscillations), recurrent loops (Working Memory), and dual-process architectures (Embodied AI) enable complex, continuous, and proactive cognitive functions.

**Author:** Frederick (Fred) Hayes
**Status:** Complete (March 2026)

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

### 3. `synthetic_dasein.ipynb` (Embodied AI & Social Friction)
**Hypothesis:** True continuous learning requires a Dual-Process architecture where heavy, conscious deliberation trains fast, energy-efficient neural reflexes, mimicking the phenomenological transition from "Present-at-Hand" to "Ready-to-Hand."

**The Model:**
A GridWorld agent equipped with two minds:
* **Graph Mind:** High-compute, perfect accuracy (Conscious Planning).
* **Reflex Mind:** Low-compute, dopamine-trained weights (Spiking Reflexes).

**Key Results:**
* **The Heideggerian Drop:** The agent successfully optimized its metabolic cost by shifting control from the Graph Mind to the Reflex Mind once a confidence threshold (> 0.8) was reached via dopamine reinforcement.
* **The Cost of Masking:** By introducing an $\alpha$ modifier representing social anxiety or "masking," the simulation successfully quantified the metabolic penalty of over-relying on conscious deliberation in complex social environments. High-friction agents expended significantly more compute units to navigate the same space as low-friction agents.

### 4. `homeostatic_plasticity.ipynb` (Synaptic Scaling)
**Hypothesis:** Continuous learning systems utilizing Hebbian plasticity are inherently unstable. To prevent runaway excitation (seizures) or catastrophic forgetting, the network requires a slow, global regulatory mechanism to bound synaptic weights.

**The Model:**
A Leaky Integrate-and-Fire (LIF) network subjected to high-frequency noisy inputs. The learning rule combines fast Spike-Timing Dependent Plasticity (STDP) with a slow Homeostatic penalty:
$$\Delta W_{total} = \Delta W_{STDP} - \beta (R_{avg} - R_{target}) W$$

**Key Results:**
* **Runaway Prevention:** Initially, Hebbian learning caused weights and firing rates to spike rapidly.
* **Metabolic Stabilization:** The homeostatic penalty successfully engaged, acting as a gravity well. The network seamlessly bounded its own synaptic weights (stabilizing at a mean of 3.33) and settled into a safe, continuous firing rate of 14.2 Hz (against a 15.0 Hz biological target).
* **Conclusion:** This provides the mathematical foundation for "Continuous Learning" without catastrophic failure in Neuromorphic architectures.

### 5. `r_stdp.ipynb` (Reward-Modulated STDP)
**Hypothesis:** True agentic learning requires solving the "Credit Assignment Problem" in continuous time. A network must be able to associate a specific action with a delayed environmental reward.

**The Model:**
A network implementing R-STDP, where Hebbian spikes leave a slow-decaying chemical "Eligibility Trace" ($E$). Synaptic weights are only permanently updated when a global Dopamine signal ($D$) interacts with an active trace.
$$\frac{dE}{dt} = -\frac{E}{\tau_E} + \text{Spike}(t)$$
$$\Delta W = \eta \cdot E(t) \cdot (D(t) - D_{baseline})$$

**Key Results:**
* **Temporal Credit Assignment:** The network successfully isolated the correct action. Neuron A fired 300ms before a reward, and its eligibility trace remained sufficiently active to capture the dopamine update (Weight grew from 2.00 to 2.43). 
* **Penalty Integration:** Neuron B fired but received no subsequent reward, causing its baseline trace to naturally decay, suppressing its weight to 1.63.
* **Conclusion:** This proves the architecture's capacity for Reinforcement Learning without reliance on instantaneous backpropagation.

---

## 🛠 Usage
These simulations are self-contained Jupyter Notebooks.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/fehayes/oscillatory-stdp-experiments.git](https://github.com/fehayes/oscillatory-stdp-experiments.git)
    ```

2.  **Install dependencies:**
    ```bash
    pip install numpy matplotlib pandas
    ```

3.  **Run the notebooks:**
    * Open `resonance_learning.ipynb` for the STDP experiments.
    * Open `working_memory.ipynb` for the Attractor Dynamics experiments.
    * Open `synthetic_dasein.ipynb` for the Dual-Process Embodied AI experiments.
    * Open `homeostatic_plasticity.ipynb` for the continuous learning and stability simulations.
    * Open `r_stdp.ipynb` for the delayed reward reinforcement learning experiments.
