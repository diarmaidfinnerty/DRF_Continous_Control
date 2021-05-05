## Report
---
The aim of the project was to train a Deep Reinforcement Agent to solve the *_Udacity's Reacher Unity Env_* [(Windows x64 verion)](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip). 

For details on the nature of the environment see README.md

## Algorithm

The agent was trained using a `Deep Deterministic Policy Gradient` model using an `Actor-Critic` methodology. This was sufficient to solve the environment in 122 episodes meaning that the  average score for each episode (where the average is over all 20 agents) is over 30.


### Hyper Parameters  

```
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 128        # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR_ACTOR = 1e-3         # learning rate of the actor 
LR_CRITIC = 1e-3        # learning rate of the critic
WEIGHT_DECAY = 0        # L2 weight decay
```

## Learning Algorithm 
The `Agent` is trained using the ddpg training helper function in the `Continous_Control.ipynb`. The training happens in an episodic manner until the environment is natually solved or maximum number of epsiodes are completed. The environment is considered solved when the average reward over 100 episodes is at least +30.

###  Network
DDPG (Deep Deterministic Poliy Gradient) is an actor-critic approach as a learning algorithm. This works similarly to a DQN but with adjustmets to allow for continous spaces.

DDPG utilizes four networks: 
    - Local actor
    - Target actor
    - Local critic 
    - Target critic 

The reason for two networks for both the Actor and Critic is that the local version is updated at each episode whereas the target actor weights are held static for a stated number of episodes. This allows for a benchmark network to critique the actors actions and helps account for any occiliations that would be visible in an actor method alone.  

The actor tries to estimate the optimal policy by using the estimated state-action values from the critic while critic tries to estimate the optimal q-value function and learns by using a normal q-learning approach. Using this approach one gains the benefits of value based and policy based methods at the same time.

## Training Rewards
![Plot of Rewards](rewardplot.png)

## Future Work
The agent could be improved by utilising a different learning algorithm. 

Examples of possible algorithms are:
    - PPO
    - AC3
    - D4PG
    
As well as using an improved memory method such as:
    - Prioritized Memory