[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

# Project 1: Navigation

### Introduction

This repo provides an implementation of an agent which learns to navigate and collect bananas in a large, square world provided by [Unity ML Agents](https://github.com/Unity-Technologies/ml-agents).

![Trained Agent][image1]

### Environment

The agent operates in a state space which has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction. Given this information, the agent learns how to best select actions.

Four discrete actions are available to agent, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The task is episodic, and in order to solve the environment, the agent must get an average score of +13 over 100 consecutive episodes.

### Getting Started

1. Clone this repository

```
git clone https://github.com/milosgajdos83/udacity-deep-rl-nanodegree.git
cd udacity-deep-rl-nanodegree/navigation
```

2. Install python dependencies

It's **highly advisable** to create a separate `Python` [virtual environment](https://docs.python-guide.org/dev/virtualenvs/). Once your virtualenv has been activated you can proceed with installing `Python` dependencies as per [Udacity guide](https://github.com/udacity/deep-reinforcement-learning#dependencies).

**Note:** Udacity guide recommends using the [Conda](https://conda.io/) `Python` distribution which overrides the system `Python` setup. The author of this repository refuses to mess with the system `Python` and was successful with setting up the workspace without using the Conda `Python` distribution.

**Note:** When setting up the workspace locally on macOS you might encounter the following issues:

    - when installing `pip3 install -e '.[box2d]'`: `error: command 'swig' failed with exit status 1`
      FIX: `brew install cmake boost boost-python sdl2 swig`
      
    - when installing `Python` requirements for Udacity DRLND: `Could not find a version that satisfies the requirement tensorflow==1.7.1 (from unityagents==0.4.0)`
      FIX: `pip3 install --upgrade https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.7.1-py3-none-any.whl`
      
    - when installing `Python` requirements for Udacity DRLND: `Could not find a version that satisfies the requirement torch==0.4.0 (from unityagents==0.4.0) (from versions: 0.1.2, 0.1.2.post1, 0.4.1)`
      FIX: `sed -i .bak 's/torch==0\.4\.0/torch==0\.4\.1/' ./python/requirements.txt`

3. Download the environment from one of the links below. You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.

4. Move the downloaded file to the project directory and unzip (or decompress) it.

### Instructions

Once you have installed all depdencies run the following command which will start `jupyter` notebook and follow the instructions in `Navigation.ipynb` to get started with training the agent:

```
jupyter notebook
```

**Note: The notebook in this repo has been used for training on a `Linux` machine. If you would like to train the agent on macOS you need to change the path to your Banana Unity environment in the notebook code!!!**
