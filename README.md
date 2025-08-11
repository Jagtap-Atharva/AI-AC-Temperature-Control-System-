# AI AC Temperature Control System 🌡️🤖

An intelligent air conditioning temperature control system that uses machine learning and reinforcement learning to optimize comfort and energy efficiency automatically.

## 🚀 Features

- **Smart Temperature Control**: Uses ML models to predict optimal AC temperatures
- **Adaptive Learning**: Learns from user preferences and adjustments
- **Dual AI Approach**: Combines supervised learning and reinforcement learning
- **Energy Optimization**: Balances comfort with energy efficiency
- **Real-time Control**: Continuously monitors and adjusts temperature
- **Occupancy-aware**: Adjusts behavior based on room occupancy
- **Environmental Adaptation**: Considers outdoor temperature, humidity, and time patterns

## 🧠 How It Works

### Machine Learning Controller
- Uses **Random Forest** and **Gradient Boosting** regressors
- Trained on synthetic data modeling real-world AC usage patterns
- Features include:
  - Indoor/outdoor temperature
  - Humidity levels
  - Occupancy status
  - Time of day/week/month
  - Previous AC settings
  - Energy consumption

### Reinforcement Learning Controller
- Implements **Q-Learning** algorithm
- Learns optimal actions through trial and error
- Reward system based on:
  - Comfort (temperature deviation from ideal)
  - Energy efficiency (minimizing large temperature changes)
  - Occupancy consideration

## 📋 Requirements

```
numpy
pandas
scikit-learn
joblib
```

## 🛠️ Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/ai-ac-control.git
cd ai-ac-control
```

2. Install required packages:
```bash
pip install numpy pandas scikit-learn joblib
```

3. Run the notebook or Python script:
```bash
jupyter notebook "ac temperature control.ipynb"
```

## 💻 Usage

### Basic Usage

```python
from ac_control import SmartACController

# Initialize and train the controller
controller = SmartACController()
controller.train_model()

# Run a control cycle
decision_log = controller.run_control_cycle()
print(f"Recommended temperature: {decision_log['predicted_temp']}°C")
```

### Advanced Usage with Reinforcement Learning

```python
from ac_control import SmartACController, RLACController

# Initialize both controllers
ml_controller = SmartACController()
ml_controller.train_model()

rl_controller = RLACController()

# Get sensor data
sensor_data = ml_controller.get_sensor_data()

# Get recommendations from both models
ml_temp = ml_controller.predict_optimal_temperature(sensor_data)
rl_result = rl_controller.control_step(sensor_data)

print(f"ML Model suggests: {ml_temp}°C")
print(f"RL Model suggests: {rl_result['new_temperature']}°C")
```

## 🔧 Configuration

### SmartACController Parameters

- `comfort_range`: Comfortable temperature range (default: 22-26°C)
- `max_temp_change`: Maximum temperature change per adjustment (default: 2°C)
- `energy_weight`: Weight for energy efficiency in decisions (default: 0.3)

### RLACController Parameters

- `learning_rate`: Q-learning rate (default: 0.1)
- `discount_factor`: Future reward discount (default: 0.95)
- `epsilon`: Exploration rate (default: 0.1)

## 📊 Model Performance

The system achieves:
- **Mean Squared Error**: ~1.3°C
- **Mean Absolute Error**: ~0.8°C
- **Feature Importance**: Outdoor temperature (59%) and occupancy (40%) are primary factors

## 🎯 Key Features Explained

### 1. Adaptive Learning
The system learns from user manual adjustments:
```python
# When user manually adjusts temperature
controller.adaptive_learning(user_temperature, sensor_data)
```

### 2. Comfort Scoring
Calculates comfort based on occupancy and temperature deviation:
```python
comfort_score = controller.calculate_comfort_score(temperature, occupancy)
```

### 3. Energy Optimization
- Reduces energy consumption when unoccupied
- Limits rapid temperature changes
- Considers outdoor temperature for efficiency

### 4. Time-aware Control
- Uses cyclical encoding for time features
- Learns daily and seasonal patterns
- Adjusts for weekday vs. weekend usage

## 📈 Simulation Results

The system includes a 24-hour simulation that demonstrates:
- Continuous temperature monitoring
- Model predictions vs. actual decisions
- User interaction learning
- Reward-based RL optimization

## 🔮 Real-world Implementation

To deploy this system with real hardware:

1. **Sensor Integration**: Replace `get_sensor_data()` with actual sensor readings
2. **AC Interface**: Implement `control_ac()` to communicate with your AC unit
3. **Persistent Storage**: Add database integration for historical data
4. **Web Interface**: Create a dashboard for monitoring and control

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- Additional ML algorithms (LSTM for time series)
- Advanced RL techniques (Deep Q-Networks)
- Real sensor integration examples
- Energy consumption modeling
- Multi-zone control
- Mobile app interface

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙋‍♂️ Support

For questions or issues:
1. Check existing [Issues](https://github.com/yourusername/ai-ac-control/issues)
2. Create a new issue with detailed description
3. Contact: your.email@example.com

## 🔗 Related Projects

- [Smart Home Automation](https://github.com/example/smart-home)
- [IoT Temperature Sensors](https://github.com/example/iot-sensors)
- [Energy Management Systems](https://github.com/example/energy-mgmt)

---
