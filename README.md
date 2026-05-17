# neural-network-optimization-study
Systematic tuning of a Deep Learning model using Dropout, EarlyStopping, and LR Schedulers.
# Deep Learning Experimentation Log: Neural Network Optimisation

## 📌 Project Overview
This repository documents a systematic approach to tuning a Neural Network. The primary goal was to move from a basic linear baseline to a highly regularised, high-accuracy model using standard industry practices.

## 📈 Performance Summary

| Model | Architecture | Optimization & Regularization | Val Accuracy |
| :--- | :--- | :--- | :--- |
| **Model 0** | 0 Hidden Layers | Adam, Batch Size 32 | 92.16% |
| **Model 1** | 1 Hidden Layer (128) | Adam, ReLU | 97.63% |
| **Model 2** | 1 Hidden Layer | Dropout (0.2), Early Stop (Patience=3) | 97.82% |
| **Model 3** | 1 Hidden Layer | Dropout (0.2), Early Stop (Patience=5) | 97.75% |
| **Model 4** | 1 Hidden Layer | Dropout (0.3), Early Stop (Patience=3, min_delta=0.001) | 97.57% |
| **Model 5** | 1 Hidden Layer | **ReduceLROnPlateau + Early Stop (Patience=6)** | **97.95%** |

---

## 🛠️ Technical Components Reference

### 1. The Training Process (Verbosity)
- **`verbose=1`**: The default mode. Displays an animated progress bar and live metrics.
- **`verbose=2`**: Compact mode. Prints exactly one line of text summary at the end of each epoch.

### 2. Regularization & Callbacks
- **Dropout**: Randomly ignores a subset of neurons during training. This prevents the model from "memorising" specific training samples and forces it to learn more general patterns.
- **EarlyStopping**: Automatically stops training when the validation loss stops improving.
    - *Key Parameter*: `restore_best_weights=True` is crucial. It ensures that after training stops, the model reverts to the state with the lowest error.
- **ReduceLROnPlateau**: A "smart" scheduler that reduces the learning rate when the model hits a performance plateau.

### 3. Core Activations
- **ReLU (Rectified Linear Unit)**: f(x) = max(0, x). Used in hidden layers to allow the network to learn non-linear relationships.
- **Softmax**: Used in the output layer to scale results into probabilities.

### 4. How to Run the Project

Clone the repository:
Bash
git clone https://github.com/ananyaja/neural-network-optimization-study.git
cd neural-network-optimization-study

Install Dependencies:
Make sure you have the following libraries installed:

Bash
pip install tensorflow numpy pandas matplotlib
Explore the Notebook:
Open the Jupyter Notebook to see the step-by-step optimization process:

Bash
jupyter notebook "Neural Network Optimization.ipynb"
