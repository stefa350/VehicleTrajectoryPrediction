# PBSC (Physical Behavior Scene Contex): LSTM-based model for Vehicle Trajectory Prediction
This repo contains python notebook used to preprocess the UWaterloo Intersection Dataset and to create and train the model.

## Abstract
Nowadays autonomous vehicles together with trajectory prediction represent a burgeoning field in AI. Vehicle Trajectory Prediction is essential for efficient and safe navigation, especially when considering traffic condition in urban centers. 
In the last years, simple models have been developed to predict vehicles trajectories using just physical laws, but more recent researches have attempted to include also interactions between the agents and the environment involving informations related to the agent’s state.
In this study we propose a trajectory prediction model that reflects both physical behavior and scene context information. The model considers agents' past state information, as well as their trajectory positions. Combining the results of a deep-learning solution with the results of a multilayer LSTM, the model takes care of a huge amount of information to predict the better trajectory.
The train and evaluation of the model are based on a part of the Waterloo intersection dataset, which provides multi-agent informations and Bird’s Eye View scenes for urban intersection situations.

## Model

