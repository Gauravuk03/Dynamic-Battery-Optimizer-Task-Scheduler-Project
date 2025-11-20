🔋⚡ Dynamic Battery Optimizer & 🧠 ML-Based Task Scheduler
A smart, intelligent Battery Optimization + Process Scheduling System built using Python, Flask, and Machine Learning.
The system predicts process priority, optimizes CPU usage, and automatically switches to low-battery emergency mode to schedule only the most important tasks.

🚀 Features
🧠 Machine Learning-Based Priority Prediction
ML model trained on process CPU usage, memory usage, and execution history

Predicts priority scores for each process

Dynamic scheduling based on predicted priority

⚙️ Hybrid Scheduling Algorithms
Used algorithms include:

Algorithm	Purpose
FCFS (First Come First Serve)	Base-level scheduling when ML confidence is low
SJF (Shortest Job First)	Optimizes execution time
Priority Scheduling	Works with ML’s predicted priority scores
Round Robin (Optional)	Ensures fairness among tasks
Rule-Based Emergency Scheduling	Activated during low-battery mode
🔋 Intelligent Low-Battery Mode
When battery is below threshold:

System skips ML prediction

Automatically selects highest priority processes

Maximizes battery life by killing low-importance tasks

🌐 Flask REST API
/predict → Predict process priority

/schedule → Return optimized schedule

/battery → Battery health API

📊 Real-Time Monitoring Dashboard (Optional UI)
Battery level

CPU usage

Active processes

ML prediction logs

🏗️ System Architecture
Processes → Feature Extractor → ML Model → Priority Score
               ↓                         ↑
               Scheduler (FCFS/SJF/Priority/Rule-based)
                          ↓
                      Final Task Order
🤖 Machine Learning Model Used
Model Type: RandomForestClassifier / XGBoost (choose based on your project)
Input Features:

CPU usage

Memory usage

Runtime duration

I/O usage

Process type

User activity pattern

Output:

Priority label: {High, Medium, Low}

Priority score (0–1)

📂 Project Structure
Dynamic-Battery-Optimizer/
│── app.py               # Flask backend
│── model.pkl            # Trained ML model
│── scheduler/
│     ├── fcfs.py
│     ├── sjf.py
│     ├── priority.py
│     ├── rule_based.py
│── utils/
│     ├── feature_extractor.py
│     ├── battery_monitor.py
│── static/
│── templates/
│── README.md
🔌 Installation & Setup
1️⃣ Clone Repo
git clone https://github.com/yourusername/Dynamic-Battery-Optimizer.git
cd Dynamic-Battery-Optimizer

2️⃣ Install Dependencies
pip install -r requirements.txt

3️⃣ Run Flask Server
python app.py

📡 API Endpoints
🔹 Predict Task Priority
POST /predict

🧮 Scheduling Algorithms (How It Works)
1️⃣ ML Mode (Battery High)
- Extract features
- Predict priority using ML
- Apply priority scheduling + SJF optimization
2️⃣ Low Battery Mode (<20%)
- Skip ML (to save power)
- Choose highest priority tasks directly
- Kill background + low-importance processes
