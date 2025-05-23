# Multi-Virtual-Agent-Reinforcement-Learning-for-a-Stochastic-Predator-Prey-Grid-Environment

This code provides a new multi-virtual-agent reinforcement learning (MVARL) approach for a predator-prey grid game. It is implemented with three virtual agents.

You can read the paper at this link: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9891898

## **Citation**
This code is provided for academic training.
If this code is used for any research purpose, please cite our IJCNN’22 paper below.
```
@INPROCEEDINGS{9891898,
  author={Lin, Yanbin and Ni, Zhen and Zhong, Xiangnan},
  booktitle={2022 International Joint Conference on Neural Networks (IJCNN)}, 
  title={Multi-Virtual-Agent Reinforcement Learning for a Stochastic Predator-Prey Grid Environment}, 
  year={2022},
  pages={1-8},
  keywords={Learning systems;Q-learning;Monte Carlo methods;Heuristic algorithms;Computational modeling;Neural networks;Games;Reinforcement learning;multiple virtual agents;generalization problem;dynamic environment and parallel learning},
  doi={10.1109/IJCNN55064.2022.9891898}}
```
## Case Study (add this function to collab notebook)
This is a predator-prey game with a size of 6×9. Areas 1, 2, and 3 are where a predator is likely to occur, with a possibility of P=[0.4,0.3,0.2,0.1]. S is the start space, and g is the goal space. The grey ones are wall spaces.

![9891898-fig-2-source-small](https://github.com/user-attachments/assets/ade13d04-b17e-429e-8413-4d750d09401f)

We initially choose $α=1,γ= 0.9, N_{trials}=50, and N_{episodes}=5000$. To eliminate the effect of random results, we implemented 50 trials and averaged the results. In this code, ε=0.1. 

This is the heatmap of the Q table under the setting. The q-table has 6×9=54 spaces, and each space has four sub-spaces. Every four sub-spaces stand for four actions' q-values in this space, which are up, down, left, and right. The global agent will choose the action with the biggest q-value (highlighted in green color) as its actual action from four directions in each space. Therefore, it will find a way to go through Area 3, which has the minimum probability of losing the game.

![9891898-fig-4-source-small](https://github.com/user-attachments/assets/ee1d472c-68b0-4f02-bec1-7e14db4d2c5a)

## **Experiments**
To choose the optimal parameter of ε-greedy, there are two kinds of experiments. 

One is to choose ε fixed; the other is to choose ε variable according to the number of episodes, which means ε=ε/τ where τ is the declining rate. For the first choice, our experiment chooses ε=0.01/0.1/0.3/0.6/0.8. For the second choice, our experiment chooses initial ε=1, τ=1.1, ε declines every k episodes, where k varies from 5 to 80.

The results are shown in the figure below.
![9891898-fig-3-source-large](https://github.com/user-attachments/assets/7231d691-c735-4968-8973-6bdb7a2596c3)

We provide the data of the first choice, which is named as "Q_learning_M3-P4321-eps0.01-50runs5000episode.csv". The epsilon varies from 0.01 to 0.8. 

For the data of the second choice, you can change the value of k to generate data (which is the discount in our code).

## **Environment Setup**
```
pip install numpy
pip install pandas
pip install matplotlib
```
## **Run Experiments**
```
python Q-learning_M3-eps0.1-P4321.py.py
```
or run the following jupyter notebook on Google Colab
```
MVARL.ipynb
```
You can change the value of epsilon by yourself to generate results with different epsilons or directly use the data we generated.

## **Plot**
```
python plot_fig-eps0.01--0.8-P4321.py
python plot_fig-eps-STEP-boxplot.py
```

## **Follow up small prject (adding obstacles)**
```
python plot_fig-eps0.01--0.8-P4321.py
python plot_fig-eps-STEP-boxplot.py
```




