# Ramsey vs. Hahn Echo on Quantum Hardware

This project demonstrates how **Ramsey interferometry** and the **Hahn echo sequence** can be used to probe quantum dephasing times (\(T_2^*\) and \(T_{2,\mathrm{echo}}\)).  
We implement both experiments in Qiskit, run them on noisy simulation and on real IBM Quantum hardware (via **SamplerV2**, one batched job), and compare the results.

---

## What is Quantum Echo?

- **Ramsey sequence** measures how quickly a qubit loses phase coherence due to noise. The signal decays with characteristic time \(T_2^*\).  
- **Hahn echo** inserts an extra refocusing pulse that cancels out slow noise. The echo signal decays more slowly, with a longer effective \(T_{2,\mathrm{echo}}\).

This is called a **quantum echo**: the qubit “forgets” some noise, briefly rephases, and shows a longer lifetime. It is one of the simplest **dynamical decoupling** techniques in quantum information.

---

## Results

### Simulation (Aer, with relaxation noise)
- The **Ramsey curve** decays relatively quickly.  
- The **Hahn echo curve** decays more slowly, showing the expected extension of coherence time.  
- Fitted values confirm \(T_{2,\mathrm{echo}} > T_2^*\).

### Hardware (IBM Quantum, SamplerV2)
- The same circuits were run on a real device in a **single Sampler job**.  
- Hardware results are flatter due to readout errors and device noise, but still show the distinction between Ramsey and echo.  
- This demonstrates that echo protection is visible even on today’s NISQ hardware, though quantitative fits are affected by noise.

---

## Why It Matters for Quantum Machine Learning (QML)

Quantum machine learning models rely on **coherent superpositions** and **phase information** to encode and process data.

- Without error mitigation, phase noise limits circuit depth and reduces trainability.  
- With echo (or more advanced dynamical decoupling), effective coherence is extended, giving **longer useful circuits** for QML.  
- In practice, echo and related techniques can make the difference between a model that **trains successfully** versus one that **collapses into noise**.

In other words: **quantum echo is not just a physics demo — it’s a practical tool to stabilize QML workloads on today’s hardware.**

---

## Takeaway

- **Ramsey vs. Hahn echo** provides a clear, intuitive picture of phase noise and its mitigation.  
- **Echo sequences extend useful coherence** — crucial for quantum algorithms and QML.  
- Even simple demonstrations like this highlight the **bridge from fundamental physics to practical quantum machine learning**.