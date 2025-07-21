# BattAIHealth: AI for Battery Health Monitoring  
**Pedro André Silva Ferreira**  
**July 2025**  

---

## Battery Basics: Introduction to Chemistries (2 min)  
- **What is a battery?**  
  - An electrochemical device that stores and releases energy through chemical reactions.  
- **Why batteries matter**: Power electric vehicles (EVs) and trains, critical for modern transportation.  
- **Battery Chemistries**:  
  - **Lithium-ion (Li-ion)**: High energy density, long life, used in EVs/trains.  
  - **Lead-acid**: Heavy, low energy, used in traditional vehicles.  
  - **Nickel-metal hydride (NiMH)**: Hybrid vehicles, less energy than Li-ion.  
  - **Solid-state**: Emerging, higher density, safer, still in development.  
- **Why Li-ion?** Ideal for transportation due to efficiency and reliability.  
- **Visual**: Diagram of a Li-ion battery + comparison chart of chemistries.  

---

## Introduction (2 min)  
- **Why it matters**: Batteries power EVs and trains, critical for safety and efficiency.  
- **Goal**: Use AI to predict:  
  - **State of Charge (SOC)**: Current energy level.  
  - **State of Health (SOH)**: Battery condition.  
  - **Remaining Useful Life (RUL)**: Time until replacement.  
- **Visual**: Image of an EV battery system.  

---

## State of the Art (2 min)  
- **Traditional Methods**:  
  - Kalman filters, equivalent circuit models.  
  - Limits: Struggle with nonlinearity and variability.  
- **AI Advantage**:  
  - Deep learning captures complex patterns from data.  
- **Visual**: Diagram comparing traditional vs. AI methods.  

---

## Baseline Methods (2 min)  
- **Explored**:  
  - **Transformer**: High accuracy, computationally heavy.  
  - **Mixture of Experts (MoE)**: Efficient, competitive results.  
- **Chosen**: **TimesNet**  
  - Excels at multi-periodic patterns in battery data.  
- **Visual**: Bar chart comparing Transformer, MoE, and TimesNet performance.  

---

## Selected Approach: TimesNet (2 min)  
- **What is it?**:  
  - State-of-the-art for time series forecasting.  
  - Uses Fast Fourier Transform (FFT) to detect periods.  
  - Converts 1D data to 2D tensors for 2D CNN analysis.  
- **Why it fits**: Captures short- and long-term battery patterns.  
- **Visual**: TimesNet architecture diagram (Fig. 19).  

---

## Methodology (2 min)  
- **Adaptation**:  
  - Inputs: Voltage, current, temperature, etc.  
  - Targets: SOC, SOH, RUL.  
- **Tools**:  
  - Hyperparameter tuning with **Optuna**.  
  - Experiment tracking with **Weights & Biases**.  
- **Visual**: Flowchart of methodology.  

---

## Experiments: Dataset (2 min)  
- **CALCE CS2 Dataset**:  
  - 886 cycles of battery data.  
  - Preprocessed for SOC, SOH, RUL calculations.  
- **Key Features**: Voltage, current, capacity trends.  
- **Visual**: Plot of SOC/SOH/RUL over cycles (Fig. 9).  

---

## Experiments: Training (2 min)  
- **Setup**:  
  - 43 epochs, 30.81 hours training.  
  - Final validation loss: 0.02929.  
- **Process**:  
  - Optimized with Optuna (50 trials).  
  - Monitored via Weights & Biases.  
- **Visual**: Validation loss curve (Fig. 23).  

---

## Results: Performance Metrics (2 min)  
- **Metrics**:  
  - SOC: RMSE = 0.2251 (best).  
  - SOH: RMSE = 0.5252.  
  - RUL: RMSE = 0.5311 (toughest).  
- **Insight**: SOC easiest, RUL hardest due to long-term prediction complexity.  
- **Visual**: Bar chart of RMSE values.  

---

## Results: Visualizations (1 min)  
- **SOC Prediction**: Closely tracks actual values.  
- **SOH/RUL**: Moderate accuracy, room for improvement.  
- **Visual**: Predicted vs. actual SOC plot (Fig. 25).  

---

## Discussion (2 min)  
- **Challenges**:  
  - Multi-task learning dilutes performance vs. specialized models.  
  - Trade-off: Unified model vs. task-specific accuracy.  
- **Deployment**:  
  - High complexity limits real-time use.  
- **Visual**: Diagram of multi-task trade-offs.  

---

## Conclusion & Future Work (2 min)  
- **Achievements**:  
  - Adapted TimesNet for battery health.  
  - Gained insights into multi-task learning limits.  
- **Next Steps**:  
  - Specialized models per task.  
  - Hybrid AI-physical models.  
  - Efficient designs for real-time use.  
- **Visual**: Icons for future research directions.  

---

**Total: ~15 minutes**  
- **Tips**: Use concise bullet points, explain visuals verbally, and rehearse for timing.