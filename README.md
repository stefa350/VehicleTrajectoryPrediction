# PBSC (Physical Behavior Scene Contex): LSTM-based model for Vehicle Trajectory Prediction
This repo contains python notebook used to preprocess the UWaterloo Intersection Dataset and to create and train the model.

## Abstract
Nowadays autonomous vehicles together with trajectory prediction represent a burgeoning field in AI. Vehicle Trajectory Prediction is essential for efficient and safe navigation, especially when considering traffic condition in urban centers. 
In the last years, simple models have been developed to predict vehicles trajectories using just physical laws, but more recent researches have attempted to include also interactions between the agents and the environment involving informations related to the agent’s state.
In this study we propose a trajectory prediction model that reflects both physical behavior and scene context information. The model considers agents' past state information, as well as their trajectory positions. Combining the results of a deep-learning solution with the results of a multilayer LSTM, the model takes care of a huge amount of information to predict the better trajectory.
The train and evaluation of the model are based on a part of the Waterloo multi-agent traffic intersection dataset, which provides multi-agent informations and Bird’s Eye View scenes for urban intersection situations.
## Dataset
The videos from the Waterloo multi-agent traffic intersection dataset were divided into frames with a sampling rate of 3Hz (a tenth of the video frame rate). After a preprocessing phase of the dataset, this is the obtained structure of the data, considering 12 points as observed trajectory and 5 to be predicted.
|TRACK_ID|First_Last_Timestamps|Frame|X-110,Y-110|...| X,Y|...| X+50,Y+50| STATUS-110|...|STATUS|STATUS+50|
|--------|:-------------------:|:---:|:---------:|---|:--:|---|:--------:|:---------:|---|:----:|:-------:|
|93|(83.083, 88.755333)|769_frame2610.jpg|(538857.67, 4813989.59)|...| (538844.67, 4814009.67)|...| (538835.71, 4814022.95)|(9.7034, 1.914, 0.3481, 2.207)|...|(32.2293, 1.0497, -0.0924, 2.1672)|(36.1521, 0.7201, -0.3222, 2.174)|
## Model
The model processes the context scene through a Resnet-18 CNN and the stati and observed trajectories information are processed by an LSTM encoder each. The concatenation of each output is processed by an LSTM decoder which predicts the trajectories.
<div align='center'>
  <img src='images/model.jpeg' width='1000px'>
</div>

## Results

<table style="width: 100%;">
  <tr>
    <th style="color: blue;">Blue</th>
    <th style="color: red;">Red</th>
    <th style="color: green;">Green</th>
  </tr>
  <tr>
    <td>Observed Trajectory</td>
    <td>Predicted Trajectory</td>
    <td>Target Trajectory</td>
  </tr>
</table>

<div align='center'>
  <table style="border-collapse: collapse; border: none;">
    <tr style="border: none;">
      <td style="border: none;"><img src="images/GIF/GIF9/trajectory9.gif" style="max-width: 100; height: auto;"></td>
      <td style="border: none;"><img src="images/GIF/GIF126/trajectory126.gif" style="max-width: 100; height: auto;"></td>
    </tr>
  </table>
</div>

Considering that minmax normalization has been applied on the data, the ADE loss on the training set is 0.0510 while in test set is 0.1605.

