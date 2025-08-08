# Inventory Management with Deep Q-Network (Beer Game)

This repository contains the implementation of **Deep Reinforcement Learning** for inventory optimization in the Beer Game.  
It is based on the paper:  
[A Deep Q-Network for the Beer Game: Deep Reinforcement Learning for Inventory Optimization](https://pubsonline.informs.org/doi/abs/10.1287/msom.2020.0939).

---

## 📌 Overview
The Beer Game is a classic supply chain simulation with four roles:  
**Retailer → Wholesaler → Distributor → Manufacturer**.  
This project uses **SRDQN (Soft Recurrent Deep Q-Network)** to train agents for optimal ordering decisions, reducing costs and improving inventory management.

---

## 📂 Project Structure

| File                | Description |
|---------------------|-------------|
| `main.py`           | Entry point to start training or evaluation |
| `BGAgent.py`        | Agent properties and decision-making logic |
| `clBeergame.py`     | Environment setup and game simulation |
| `SRDQN.py`          | Deep Q-Network model and training algorithm |
| `config.py`         | Configuration parameters and scenario setup |
| `plotting.py`       | Visualization tools for simulation results |
| `utilities.py`      | Helper functions |
| `requirements.txt`  | List of Python dependencies |

---

## ⚙ Requirements

- Python 2.7 or Python 3.4–3.7  
- TensorFlow 1.x (Not compatible with TensorFlow 2+)  
- Install dependencies:
```bash
pip install -r requirements.txt
```

---

## 🚀 How to Run

### Train the Basic Model
```bash
python main.py
```

### Train with Custom Configuration
Example: Train SRDQN warehouse with Sterman co-players for 50,000 episodes:
```bash
python main.py --gameConfig=8 --maxEpisodesTrain=50000 --ILInit2=10 --batchSize=128
```

---

## 🎮 Play & Compare
You can play the Beer Game manually and compare your results with the trained AI:  
[https://beergame.opexanalytics.com/](https://beergame.opexanalytics.com/)

---

## 🔧 Configurations

### Agent Types
Agents can follow:
- `srdqn` – Trained Deep RL agent
- `bs` – Base-stock policy
- `Strm` – Sterman policy
- `rnd` – Random ordering

### Example Game Configurations
```python
if config.gameConfig == 3:
    config.agentTypes = ["srdqn", "bs", "bs", "bs"]
if config.gameConfig == 7:
    config.agentTypes = ["srdqn", "Strm", "Strm", "Strm"]
if config.gameConfig == 11:
    config.agentTypes = ["srdqn", "rnd", "rnd", "rnd"]
```

---

## 📊 Available Training Scenarios

1. **Basic Model** – Uniform demand U[0,2]
2. **Literature Cases** – Uniform U[0,8], Normal N(10,2), Custom C(4,8)
3. **Basket Dataset**
4. **Forecasting Dataset**
5. **Transfer Learning** – Use pre-trained models as a base

---

## 📈 Output & Visualization
When `config.ifSaveFigure=True`, the program saves:
- Inventory levels
- Rewards
- Actions
- Orders
- Shipments

When `config.ifsaveHistInterval=True`, it records the historical trajectory of each metric for analysis.

---

## 📜 Citation
If you use this code, please cite:

```
@article{oroojlooyjadid2017deep,
title={A Deep Q-Network for the Beer Game: Deep Reinforcement Learning for Inventory Optimization},
author={Oroojlooyjadid, Afshin and Nazari, MohammadReza and Snyder, Lawrence and Tak{'a}{{c}}, Martin},
journal={Manufacturing & Service Operations Management},
year={2021},
doi={10.1287/msom.2020.0939}
}
```

---

## 👤 Author
Modified and maintained by **Rishav Jindal**  
Based on the original research by Afshin Oroojlooyjadid et al.
