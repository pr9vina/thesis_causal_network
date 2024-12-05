
**try.ipynb**

This notebook demonstrates the first attempt in the Data Generation Process. 

To generate a network I used Barabasi-Albert model that is commonly used for modeling real-world systems, for instance friendhip groups or high school networks. It generates networks with a power-law degree distribution, resulting in some nodes have a much larger number of connections than others.

To start with, we need to assume the type of network effect. Here I assume relational network effect, meaning that the outcome of te unit depends on its covariates, as well as their neighbours' outcome and covariates. There also could be a positional network effect, which depicts an effect on a network level, meaning that unit's position in network affects outcome and structural effect that depicts effect of the network as a whole. For simplicity I don't assume this. 

Additionally, we can simulate whether the influence of every node is the same by normalizing the adjacency matrix. Hovewer, in real-world scenarios I find this assumption too simplistic. 

To simulate these scenarios we can apply spatial lag model approaches. The value of the outcome of one unit depends on the value of its neighbours, leading to dependencies between neighbours. This means that a system of equations has to be solved simultaneously: $$ y = X\beta + \rho Wy + \epsilon $$

Solving for y:

$$y = (I - \rho W)^{-1}X\beta + (I - \rho W)^{-1}\epsilon$$

Then, we can simulate treatment $Z$, which results in the following model: $$y = (I - \rho W)^{-1}X\beta_{1} + (I - \rho W)^{-1} (\beta_{2}*Z) + (I - \rho W)^{-1}\epsilon$$