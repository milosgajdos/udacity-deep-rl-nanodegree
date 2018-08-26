# Navigation Report

The project implements a simple agent trained using Reinforcement Learning to navigate large environment in continuous space and collect rewards (yellow bananas) whilst avoiding collisions (blue bananas).

The agent implementation is based on Deep Q-Network (DQN) as described in the [Human-Level Control through Deep Reinforcement Learning](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf) paper.

# Implementation

Navigation project uses a variation of [Unity Banana Collector](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#banana-collector) environment. You can read more about the environment in the project [README](README.md).

The implementation is split into few small modules:
- `model.py`: contains Neural Network implementation in [PyTorch]() which is used for local and target Q-network
- `dqn_agent.py`: contains the agent implementations as described in the earlier mentioned paper
- `Navigation.ipynb`: imports all the required modules and allows to explore the environment and traind the agent

## Q-Network model

At the heart of the agent is a pair of Neural Networks: local and target network which are trained as described in the earlier mentioned paper. Both networks are identical - the only difference lies in a way their weights are being updated.

Both networks have been chosen to have 3 fully connected layers with RELU activations applied on the first two layers. The size of the first layer is identical to the size of the state vector, whilst the 2nd and 3rd layer both have 64 units. The output layer has the size equal to the number of allowed agent actions.

As the agent learns by interacting with the banana environment the weights of both networks are being updated and the resulting score is being accumulated.

# Agent implementation

The agent implementation implements a **replay buffer** which accumulates the agent's interactions with the environment. These experiences are then later used in the learning algorithm. By randomly sampling from the experience buffer we avoid stored experience correlations and can take advantage of [rare and potentially valuable] experiences, thus improving the agent's learning. This of course introduces two hyperparameters: the size of the buffer and the size of the batch.

I chose the size of the buffer to be 100 000, which is reasonably high to make room to hold valuable experiences across the training. The authors of the training use the size of 1 000 000 which increases the possibility of sampling valuable experiences further still. The choice of this parameter is a compromise between the availability of RAM on the training machine and possibility of better training. Equally, the sampling size has been chosen in my case to 64 experiences whilst the authors chose only 32. What this means in my case is the training should be a bit faster maybe rather fluctuating as the gradient descent steps are taken on a larger size of the sample. DQN authors probably do more, but smaller sized updates which might lead to less fluctuation when run with the same number of episodes.

The Q-Network is being updated every 4 steps of agents interactions with the environment. We could make the updates more frequent, but that would probably require more time for the full learning as we wouldnt fill the experience buffer with enough "interesting" (valuable) expriences that are used for learning.

Finally, we have the well known discount factor gama here, which is set to 0.99 which places agent's focus on the long term returns rather than the immediate rewards.

# Results

The agents achieves the score of 16.17 in 1500 episodes which satisfies the project submission requirements. It's worth pointing out that I could easily stop the training after about 600 episodes when the agent surpasses the required score of 13.

# Further improvements

We can futher improve the performance by implementing several improvements suggested in the original paper such as prioritizing experiences from the replay buffer or implementing dueling DQNs. The latter would howver require longer training. We could also tune the existing parameters more, such as already discussed expending of experience buffer and shrinking the batch size.
