# 🐦 Flappy Bird AI using Deep Q-Learning

A Deep Q-Learning (DQN) agent that learns to play Flappy Bird using
PyTorch and Reinforcement Learning.

The agent learns through trial and error by interacting with the Flappy
Bird environment, storing previous experiences in a replay memory, and
improving its policy using a Deep Q-Network.

## 🎮 Demo

### DQN Agent Gameplay

A gameplay demonstration of the trained agent will be added after
further training.

The final demo will show the trained DQN agent playing Flappy Bird
autonomously.

## 📌 Project Overview

The objective of this project is to train an AI agent to play Flappy
Bird using Deep Q-Learning.

The agent follows this learning process:

Observe Game State → DQN predicts Q-values → Choose an Action → Interact
with Flappy Bird → Receive Reward → Store Experience → Experience Replay
→ Update DQN → Synchronize Target Network

The agent uses an epsilon-greedy strategy to balance exploration and
exploitation during training.

## 🧠 Deep Q-Learning

Deep Q-Learning uses a neural network to approximate the Q-function:

Q(state, action)

The network estimates the expected future reward for each available
action.

The agent then selects actions based on these estimated Q-values.

### Exploration vs Exploitation

During training, the agent uses epsilon-greedy action selection.

With probability ε, the agent chooses a random action for exploration.

Otherwise, the agent chooses the action with the highest predicted
Q-value for exploitation.

Epsilon gradually decreases during training, allowing the agent to
explore initially and rely increasingly on its learned policy.

## 🧠 Neural Network Architecture

The Deep Q-Network used in this project consists of:

Input State → Linear Layer (12 → 256) → ReLU → Linear Layer (256 → 2) →
Q-values

### Architecture

  Layer            Size
  -------------- ------
  Input              12
  Hidden Layer      256
  Activation       ReLU
  Output              2

The two output values correspond to the available actions in the Flappy
Bird environment.

## 🔄 Experience Replay

The agent stores its previous interactions in an experience replay
buffer.

Each experience contains:

(state, action, next_state, reward, terminated)

During training, a random mini-batch is sampled from the replay memory.

This allows the agent to learn from previous experiences instead of
relying only on the most recent interaction.

The replay memory is implemented using a bounded deque.

## 🎯 Target Network

The project uses two neural networks:

### Policy Network

The policy network is updated during training and is responsible for
learning the optimal Q-values.

### Target Network

The target network is used to calculate the target Q-values.

The target network is periodically synchronized with the policy network
to improve training stability.

Policy Network → Updated Weights → Target Network

## 🏆 Best Model Saving

During training, the total reward obtained in each episode is tracked.

Whenever an episode achieves a reward greater than the previous best
reward, the current policy network is saved.

The saved model is stored in the runs/ directory.

This allows the trained agent to be tested using the best-performing
model encountered during training.

## ⚙️ Hyperparameters

The training parameters are stored separately in parameters.yaml.

This allows the training configuration to be modified without changing
the main Python code.

Important parameters include:

  Parameter            Description
  -------------------- -----------------------------------------
  alpha                Learning rate
  gamma                Discount factor
  epsilon_init         Initial exploration probability
  epsilon_min          Minimum exploration probability
  epsilon_decay        Epsilon decay rate
  replay_memory_size   Maximum replay memory capacity
  mini_batch_size      Training batch size
  network_sync_rate    Target network synchronization interval
  reward_threshold     Episode reward limit

## 📁 Project Structure

    flappy-bird-dqn/
    │
    ├── README.md
    ├── requirements.txt
    ├── .gitignore
    │
    ├── agent.py
    ├── dqn.py
    ├── experience_replay.py
    ├── game_flappy_bird.py
    └── parameters.yaml

### File Description

  -----------------------------------------------------------------------
  File                                Purpose
  ----------------------------------- -----------------------------------
  agent.py                            Main DQN training and testing
                                      implementation

  dqn.py                              Defines the Deep Q-Network
                                      architecture

  experience_replay.py                Implements the experience replay
                                      buffer

  game_flappy_bird.py                 Allows manual interaction with the
                                      Flappy Bird environment

  parameters.yaml                     Stores training hyperparameters

  requirements.txt                    Lists Python dependencies

  .gitignore                          Prevents unnecessary/generated
                                      files from being uploaded
  -----------------------------------------------------------------------

## 🛠️ Technologies Used

-   Python
-   PyTorch
-   Gymnasium
-   Flappy Bird Gymnasium
-   Pygame
-   PyYAML

## 🚀 Installation

### 1. Clone the repository

    git clone https://github.com/YOUR_USERNAME/flappy-bird-dqn.git
    cd flappy-bird-dqn

### 2. Create a virtual environment

    python -m venv venv

### 3. Activate the environment

#### Windows

    venv\Scripts\activate

#### macOS / Linux

    source venv/bin/activate

### 4. Install dependencies

    pip install -r requirements.txt

## ▶️ Running the Project

### Train the DQN Agent

Run:

    python agent.py flappybirdv0 --train

During training, the agent:

1.  Observes the current state.
2.  Selects an action using epsilon-greedy exploration.
3.  Receives a reward from the environment.
4.  Stores the experience in replay memory.
5.  Samples experiences for training.
6.  Updates the policy network.
7.  Periodically synchronizes the target network.
8.  Saves the model whenever a new best episode reward is achieved.

### Test the Trained Agent

After training, run:

    python agent.py flappybirdv0

This loads the saved trained model and opens the Flappy Bird environment
with rendering enabled.

The trained DQN then chooses actions autonomously.

## 🎮 Manual Flappy Bird

The project also contains a simple environment interaction script:

    python game_flappy_bird.py

The script allows the user to control the bird manually using the
keyboard.

SPACE → Flap

## 💻 Device Support

The training script automatically selects an available computing device:

Apple Silicon GPU (MPS) → NVIDIA GPU (CUDA) → CPU

This allows the project to run on different hardware configurations.

## 📚 Reinforcement Learning Concepts

This project demonstrates practical implementation of:

-   Reinforcement Learning
-   Deep Q-Learning
-   Q-values
-   Epsilon-Greedy Exploration
-   Exploration vs Exploitation
-   Experience Replay
-   Target Networks
-   Bellman-style Q-value updates
-   Neural Networks
-   PyTorch Optimization
-   Gymnasium Environments

## 🔮 Future Improvements

Possible improvements to the project include:

-   Add training reward visualization.
-   Track and plot rewards across episodes.
-   Record trained gameplay automatically.
-   Add configurable training episode limits.
-   Add model checkpoints.
-   Experiment with different network architectures.
-   Tune hyperparameters for improved performance.
-   Implement Double DQN.
-   Implement Dueling DQN.
-   Compare different reinforcement learning approaches.

## 👩‍💻 Author

**Mahathi**

Computer Science Undergraduate

## ⭐ Acknowledgements

This project uses the Flappy Bird Gymnasium environment and PyTorch to
explore Deep Reinforcement Learning and Deep Q-Learning.
