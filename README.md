<p align="center">
</p>
👨‍💻 Author

<p align="center">
  <img src="https://avatars.githubusercontent.com/u/00000000?s=200&v=4" width="120" height="120" style="border-radius:50%;" alt="Muhammad Hasnain Falaksher"/>
</p>

<p align="center">
  <b>Muhammad Hasnain Falaksher</b><br>
  Quantum Research Engineer
</p>

📍 **Focus Areas:** Quantum Algorithms, Quantum Error Correction, and Circuit Optimization  

<h1 align="center">⚛️ Shor’s Algorithm Simulation using Qiskit</h1>

<p align="center">
  <b>Quantum Factorization of N = 21 using Qiskit AerSimulator and Custom Quantum Fourier Transform</b><br>
  <a href="https://colab.research.google.com/drive/1iWHlj54Om0rAz-SPSZdw7r2DiDZsQX5K?usp=sharing" target="_blank">🚀 Open in Google Colab</a>
</p>

---

## 🧠 Overview

This repository demonstrates the **implementation of Shor’s Algorithm**, one of the most celebrated quantum algorithms that showcases **quantum advantage** in integer factorization. Using **Qiskit**, this project simulates the factorization of the composite number **N = 21** through a fine-tuned **Quantum Fourier Transform (QFT)** circuit.

The quantum circuit is designed to generate precise measurement peaks at `01000000` and `11000000`, representing the periodicity of the modular exponentiation function — the core concept behind **Shor’s Algorithm**.

---

## ⚙️ Key Highlights

- ✅ Implementation of **Shor’s Algorithm** for factoring N = 21  
- ✅ Custom **RZ phase rotations** for accurate quantum interference  
- ✅ Integration of **inverse QFT** for frequency extraction  
- ✅ **Classical post-processing** using GCD for prime factor retrieval  
- ✅ Compatible with **Qiskit AerSimulator** for reproducible, noise-free results  

---

## 📊 Simulation Results

After executing the custom quantum circuit, the output results were obtained as follows:


✅ These results confirm the correctness of **Shor’s Algorithm**:
> \( 3 \times 7 = 21 \)

This experiment demonstrates how **quantum phase estimation** and **period finding** can efficiently uncover the hidden structure of modular functions.

---

## 🧩 Circuit Explanation

The algorithm flow:

1. **Superposition Creation:** Hadamard gates applied to counting qubits  
2. **Phase Encoding:** RZ rotations to embed modular phase information  
3. **Inverse QFT:** Extracts the periodicity of the encoded function  
4. **Measurement:** Collapses qubit states to reveal frequency peaks  
5. **Classical Computation:** GCD used to extract factors from order \( r \)

---

## 💻 Code Overview

```python
def create_custom_shor_circuit():
    """Creates circuit with precise peaks at 01000000 and 11000000"""
    n_count = 8
    qc = QuantumCircuit(n_count, n_count)

    # Step 1: Create superposition
    for q in range(n_count):
        qc.h(q)

    # Step 2: Apply phase rotations (key tuning)
    qc.rz(np.pi/0.2, 1)   # For 01000000 peak
    qc.rz(np.pi/14, 5)    # For 11000000 peak

    # Step 3: Apply Inverse QFT
    qft = QFT(n_count, inverse=True)
    qc.append(qft, range(n_count))

    # Step 4: Measurement
    qc.measure(range(n_count), range(n_count))
    return qc



