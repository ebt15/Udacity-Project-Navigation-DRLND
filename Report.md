# Udacity Exercise Navigation Report
The navigation project is using Deep Q-learing to train an agent to collect yellow bananas in an unity environment.
## The Environment Description
In this project, you will train an agent to navigate (and collect bananas!) in a large, square world.

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

- 0 - move forward.
- 1 - move backward.
- 2 - turn left.
- 3 - turn right.

The task is episodic, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.
## Learning Algorithm
We use deep Q-learning algorithm to train the agent. If you do not be familiar with it, please read this [research paper](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf)

DQN takes a game image as a input, in this project, we only learning from discrete action space 

### The Q-Network is shown below

    QNetwork(
      (Fully connected layer1): Linear(in_features=37, out_features=128, bias=True)
      (Fully connected layer2): Linear(in_features=128, out_features=64, bias=True)
      (Fully connected layer4): Linear(in_features=64, out_features=4, bias=True)
    ) 
### hyper-parameter

    BUFFER_SIZE = int(1e5) # replay buffer size
    BATCH_SIZE = 64 # minibatch size
    GAMMA = 0.99 # Discount factor for q-learning
    TAU = 1e-3 # for soft update of target parameters
    LR = 5e-4 # learning rate for the neural network
    UPDATE_EVERY = 4 # how often to update the network
    
### Plan of attack to choose hyper-parameters

#### eps
0<= ε <=1<br>
the agent selects the greedy action with probability 1- ε <br>
the agent selects an action uniform at random from the set of available(non-greedy AND greedy) actions with probability  ε <br>
so if  ε = 0, the agent always select the greedy action<br>
#### GAMMA
0<= 𝞬 <=1<br>
the agent will only care about if immediate rewards if 𝞬 = 0<br>
the agent will care more about future rewards if 𝞬 is large<br>
if you want to care more about future, you should take a large 𝞬

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

I’m planning to add following features in this:

• [Dueling DQN](https://arxiv.org/abs/1511.06581)

• Double DQN

• [Prioritized Experience Replay](https://arxiv.org/abs/1511.05952)

• Apart from this, I’m planning to use the DQN to train using the pixels of the environment,
  similar thing was done in the DQN paper
