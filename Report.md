   # **Report**

## Deep Q-Networks

Deep Q-Learning algorithm represents the optimal action-value function q∗​ as a neural network (instead of a table).
Reinforcement learning is notoriously unstable when neural networks are used to represent the action values. Deep Q-Learning algorithm addresses these instabilities by using two key features:
Experience Replay: a rolling history of past data via a re-play pool. Using the replay pool the behavior distribution is averaged out over many of its previous states smoothing out learning and avoiding oscillations. This has the advantage that the step of the updates is potentially used in many weight updates.
Fixed Q-Targets: use a target network to represent the old Q-Function, which will be used to calculate the loss of every action during training. At every step, the q-function values change so we can use a single network and the value estimates could spiral out of control.


## Deep Q-Learning Improvements

Several improvements to the original Deep Q-Learning algorithm have been suggested. Over the next several videos, we’ll look at three of the more prominent ones.

Double DQN: Deep Q-Learning tends to overestimate action values. Double Q-Learning has been shown to work well in practice to help with this.

Prioritized Experience Re-play: Deep Q-Learning samples experience transitions uniformly from a replay memory. Prioritized experienced replay is based on the idea that the agent can learn more effectively from some transitions than from others, and the more important transitions should be sampled with higher probability.

Dueling DQN: Currently, in order to determine which states are (or are not) valuable, we have to estimate the corresponding action values for each action. However, by replacing the traditional Deep Q-Network (DQN) architecture with a dueling architecture, we can assess the value of each state, without having to learn the effect of each action.


### The Q-Network is shown below

    QNetwork(
      (Fully connected layer1): Linear(in_features=37, out_features=128, bias=True)
      (Fully connected layer2): Linear(in_features=128, out_features=64, bias=True)
      (Fully connected layer3): Linear(in_features=64, out_features=4, bias=True)
    ) 
### hyper-parameter

    BUFFER_SIZE = int(1e5) # replay buffer size
    BATCH_SIZE = 64 # minibatch size
    GAMMA = 0.99 # Discount factor for q-learning
    TAU = 1e-3 # for soft update of target parameters
    LR = 5e-4 # learning rate for the neural network
    UPDATE_EVERY = 4 # how often to update the network

## Train The Network
    Episode 100	Average Score: 0.33
    Episode 200	Average Score: 2.68
    Episode 300	Average Score: 7.24
    Episode 400	Average Score: 11.94
    Episode 500	Average Score: 13.08
    Episode 600	Average Score: 14.39
    Episode 700	Average Score: 15.05
    Environment solved in 685 episodes!	Average Score: 15.05  
![train_network](https://github.com/ebt15/Udacity-Project-Navigation-DRLND/blob/master/assets/network.png?raw=true)

## Ideas for Future Work

I’m planning to use the DQN to train using the pixels of the environment.
