This project was submitted to CUCAI 2025 (proceedings of which can be found [here](https://drive.google.com/file/d/1Ov-0nKdaizbdKaXh8qTzVd0fzU6_8gG1/view). Our paper can be found under World Model Architectures for Model-Based Reinforcement Learning)
and done in tandem with Triston Grayston whose repository is [here](https://github.com/tristongrayston/Expressive_World_Models/tree/main).
We experimented with three deep learning architectures to learn three different environments.

# Architectures

## Residual Connection
Residual Connection models only predict the change from one state to the next. We claim this is a simpler problem than creating the next state from scratch. 
In practice, this is done by adding its output (the prediction for the change in state) to the input state to get a prediction for the next state.

## Recurrent Network
RNN are a type of neural network designed for sequential data, where past information influences the current output via a hidden state that maintains context across time steps. 
Many world models in previous works have used derivatives on RNN architectures, such as dreamerV3.

## Neural Circuit Policies
Fundamentally derived from NeuralODE’s (and by extension Residuals) and recurrent networks, these models promise to identify cause-and-effect patterns in data, theoretically tackling a separate problem of that of predictive inference. 
These models, developed by Hasani, R., et al. (2022), are derivatives of the foundational work of continuous-time neural networks which train neural networks as approximate derivatives and solving over temporal data by
integrating that neural network over time, or closed form approximating that integration. We can then add sparse connections to certain circuits in the network in a way which mimics biological networks, with the consequence of increased interpretability. 

# Environments

## Pendulum
The state space of pendulum consists of x and y positions, and angular velocity, and the action applies a torque to the pendulum.
Pendulum’s simple yet continuous dynamics make it ideal for testing an architectures as world models.

## Partially Observable Pendulum
This environment is identical to the above Pendulum, except we hide the velocity (Residual Connections were omitted form these experiments as they have no temporal component).
This makes the environment non-markovian, which means that there is insufficient information in a single state to predict the next one.
Residual Connection models are ommitted as they have no temporal aspect to learn how the state changes over time.

## Lorenz
Lorenz systems display, due to their chaotic nature, dynamics which are difficult to approximate with neural networks.

More details can be found in our submission

# Relevant Papers: 
\
[PPO](https://arxiv.org/abs/1707.06347) \
[General Advantage Esimtation](https://arxiv.org/pdf/1506.02438) \
[Neural ODES](https://arxiv.org/pdf/1506.02438) \
[LTC Networks](https://arxiv.org/abs/2006.04439) \
[NCPS](https://www.nature.com/articles/s42256-020-00237-3) \
[CFCS](https://www.nature.com/articles/s42256-022-00556-7) 
